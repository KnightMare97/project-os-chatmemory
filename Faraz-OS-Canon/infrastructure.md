# Faraz OS — Infrastructure Design (Phase 9)

## Purpose

`infrastructure.md` assigns physical technology to each of the seven abstract
Infrastructure Layer blocks defined in `architecture.md` (`Faraz-OS-Canon.md:149`).
It is the Phase 9 target and the one-way downstream from Phase 8.

This file answers: *"What concrete technology backs each abstract Infrastructure
block, and how is it deployed?"* It does not re-define what the blocks ARE —
that is Phase 8. It does not specify build procedures, exact instance SKUs, or
deployment scripts — that is Phase 10.

---

## Altitude

Phase 9 assigns technology at **infrastructure-design altitude**: service names,
topology (which GCP product, what role it plays, how the blocks connect), and
governing patterns (data separation scheme, connection routing, security
invariants). It does **not** author:

- Build-layer specifics: exact machine types, autoscaling thresholds, managed
  migration scripts, CI/CD pipeline config → Phase 10.
- Application-layer code: API middleware, ORM configuration, worker process
  code → Phase 10.
- Physical infrastructure for Phases 1–8 conceptual blocks (domains, capabilities,
  plugins, experience) — this file is the substrate those blocks run on, not a
  re-definition of them.

Where a concrete sizing reference appears (e.g., "Cloud SQL db-g1-small as
illustrative starting point"), it is **illustrative and not locked**; the exact
SKU is a Build-layer decision.

---

## Governing Boundary Test

From `architecture.md:197`, the P8 ↔ P9 cut:

> Phase 8 Infrastructure Layer names blocks at **abstract** altitude — no named
> technology, framework, database, or service. Phase 9 Infrastructure Design
> (`infrastructure.md`) assigns physical technology to each abstract block.

Phase 9 ASSIGNS. Any re-definition of what an abstract block IS refers back to
Phase 8 (`architecture.md:184-190`). Any implementation procedure refers forward
to Phase 10.

---

## Platform Decision

**All-GCP — no VPS.** The approved stack runs entirely on Google Cloud Platform.
No self-hosted server outside GCP is required or assumed. This was approved
2026-06-09 after a six-team infrastructure analysis (Option B from the three-option
comparison: managed Cloud SQL + Firebase Auth + Cloud Run + GCS + Secret Manager;
see DEC-041). The VPS is not in the production data path.

---

## How to Read This File

Each Infrastructure block entry uses a **four-field per-entry skeleton**:

1. **Abstract block** — which Phase 8 block (`architecture.md`) is being assigned.
2. **Assigned technology** — the concrete GCP service that fills this role.
3. **Topology and pattern** — how it is deployed and how it connects to other blocks.
   Build-layer specifics (exact SKU, autoscaling rules) are flagged as
   illustrative-not-locked.
4. **Boundary notes** — what this technology does NOT own, and cross-block seams.

A fifth field, **Build-layer flags**, appears where Phase 10 must make explicit
decisions before this block can be instantiated.

The Per-Client Data Scoping Scheme entry is expanded to first-class depth because
it is the most architecturally load-bearing block in the stack.

---

## Non-goals

`infrastructure.md` does NOT author:

- Re-definition of abstract block names or their logical roles — Phase 8
  (`architecture.md:184-190`).
- Application API code, ORM layer, or middleware implementation — Phase 10.
- Domain entity schemas or Postgres table definitions — Phase 1 domain truth
  (`domains.md`).
- Build pipeline, CI/CD config, or deployment runbook — Phase 10.
- Cost arithmetic or exact SKU commitments — illustrative references only;
  actual sizing is Phase 10 / operational.
- Resolution of any carried-open question (Q-004, Q-006, Q-017, Q-020, Q-022,
  Q-024, R-027 set) — all referenced where relevant, none resolved here.

---

## Block 1 — Persistent Store

**Abstract block.** `architecture.md:184` — "Abstract durable storage substrate
for domain entities and artifacts."

**Assigned technology.** **Google Cloud SQL for PostgreSQL** (managed Postgres on
GCP). Single Cloud SQL instance; one Postgres database; schema-per-client layout
(see Block 7 — Per-Client Data Scoping Scheme, which governs the layout inside
this store).

**Topology and pattern.**
- Cloud SQL is the single source of relational truth for all domain entities
  across all Faraz OS layers.
- Connected from Cloud Run services (API server, workers) via the **Cloud SQL
  Auth Proxy** running in sidecar mode, using a dedicated IAM service account.
  The Auth Proxy manages connection lifecycle and supports session-mode pooling,
  which is required for the schema-per-client routing described in Block 7.
- The `pg-boss` job queue (Block 2) runs inside this same Cloud SQL instance —
  no separate Postgres instance is needed for queue state.
- Instance sizing is a Build-layer decision; an `e.g. db-g1-small` (1 shared
  vCPU, 1.7 GB RAM) is an illustrative starting point for 30 clients at moderate
  volume. Production sizing and read-replica provisioning are Phase 10.

**Boundary notes.**
- Cloud SQL is the Persistent Store substrate only. The data-layout scheme inside
  it (schema-per-client) is Block 7 (Per-Client Data Scoping Scheme). The
  enforcement logic above it (which sets `search_path` and applies RLS policies)
  is the Core Layer's Per-Client Isolation Enforcer (`architecture.md:118`).
- Binary / media assets (Client Asset entity, Media & Assets domain) are NOT
  stored in Cloud SQL — they live in Block 9 (GCP Cloud Storage). Cloud SQL
  holds metadata references only.
- Postgres itself is a GCP-managed service; Faraz OS does not run a Postgres
  container, VPS, or self-hosted instance.

**Build-layer flags.**
- Exact instance SKU, storage size, and connection pool limits → Phase 10.
- Automated backup schedule, PITR retention window, and point-in-time recovery
  runbook → Phase 10.
- Cloud SQL Auth Proxy sidecar container configuration → Phase 10.
- Read replica provisioning (if/when query volume warrants it) → Phase 10.

---

## Block 2 — Job Queue / Event Bus

**Abstract block.** `architecture.md:185` — "Abstract queuing and
event-distribution substrate for async work and domain events."

**Assigned technology.** **pg-boss** (Postgres-native job queue library running
inside the Cloud SQL instance assigned to Block 1). No separate message broker,
Redis instance, or managed queue service is introduced at this stage.

**Topology and pattern.**
- pg-boss creates and manages a `pgboss` schema inside the Cloud SQL Postgres
  database. All job state (pending, active, completed, failed, awaiting-approval)
  is a Postgres row — durable, transactionally consistent with domain data,
  survives any Cloud SQL restart event.
- Named queues per workflow domain (e.g., `service_delivery.production`,
  `crm.lead_scoring`, `community.engagement_reply`) provide module-level
  routing within a single broker. Queue name namespace convention is a
  Build-layer concern.
- The HITL (human-in-the-loop) "awaiting approval" state is a durable pg-boss
  job row, not an in-memory state. When a human approves (via the portal API),
  the approval handler inserts a new job into the downstream queue; the
  suspended job is marked complete. This is the correct pattern for the
  Production → Approval workflow gate (Phase 6, `workflows.md`).
- The **Dual-Path / Manual-Fallback Routing** pattern (DEC-037) is realized at
  the worker layer: before dispatching to an automated path, the worker checks
  connection health; on failure it inserts into a `manual_fallback` named queue
  instead of the dead-letter set. No special queue infrastructure is needed
  beyond named queues.
- Publish-idempotency guard: a `publish_intents` table with a unique constraint
  on `(workflow_id, channel_id, content_id)` guards against dual-path
  double-publish. This is a Postgres-level structural guard, not a queue-level
  guard. The queue can re-enqueue; the worker checks the `publish_intents` row
  before dispatching to a channel API. Details are a Phase 10 / Build concern.
- Domain events (Lead converted, Deliverable approved, Content published, etc.)
  are routed by inserting downstream jobs on job completion — the job queue
  doubles as the event bus. No separate event bus infrastructure is needed at
  30-client volume. Postgres `LISTEN/NOTIFY` is available for real-time surface
  updates (see Block 3 — Worker / Job Runtime, SSE endpoint).

**Boundary notes.**
- pg-boss lives inside Block 1 (Cloud SQL). It is not a separate infrastructure
  block; it is the queue technology assigned to an abstract queue block, running
  on the Persistent Store substrate.
- The job queue manages work state. It does NOT own domain entity state — domain
  entities live in client schemas (Block 7). A job carries `client_id` in its
  metadata; the worker resolves the correct schema from that metadata.
- If throughput or worker concurrency meaningfully outgrows pg-boss polling
  (a Phase 10 / operational threshold), the migration path is BullMQ + Cloud
  Memorystore for Redis. That migration is a Build-layer concern; no Redis
  instance is provisioned at Phase 9.

**Build-layer flags.**
- Named queue namespace convention and per-queue priority tiers → Phase 10.
- pg-boss version, connection pool for the queue schema, and dead-letter
  handling policy → Phase 10.
- `publish_intents` table schema and uniqueness constraint → Phase 10.
- Migration-path trigger criteria for BullMQ upgrade → Phase 10.

---

## Block 3 — Worker / Job Runtime

**Abstract block.** `architecture.md:186` — "Abstract compute substrate for
background and async job execution."

**Assigned technology.** **Google Cloud Run** — two surfaces:
1. **API / Application Server** (Cloud Run service, `minInstances = 1`): the
   Faraz OS application server — handles inbound API requests from the portal,
   manages the pg-boss job poller, and serves the SSE endpoint for the Workflow
   Monitor surface.
2. **AI Chain Worker** (Cloud Run service or Cloud Run Job, `minInstances = 0`,
   scale-to-zero): executes AI agent chain jobs (content creation, research,
   strategy, lead scoring, publishing, report generation) dispatched from the
   pg-boss queue.

**Topology and pattern.**
- The API server runs with one minimum-warm instance to eliminate cold-start
  latency on portal interactions. Cold-start on Node.js / Python Cloud Run is
  1–3 seconds; one minimum instance at a small memory footprint (~256–512 MB)
  eliminates this for the interactive surface. Cost is illustrative and
  Build-layer.
- AI chain workers run scale-to-zero. A 1–3 second cold start on a background
  job that runs 30 seconds to 5 minutes is imperceptible. Cloud Run AI worker
  instances connect to Cloud SQL via the Cloud SQL Auth Proxy sidecar.
- All Cloud Run services authenticate to other GCP services (Cloud SQL, Cloud
  Storage, Secret Manager) via **Workload Identity** (IAM service account bound
  to the Cloud Run service account), not via environment-variable credential
  files. Secrets are injected at startup from Secret Manager (Block 5).
- **Realtime — SSE endpoint:** The API server holds a long-lived HTTP/2
  connection open for each portal client subscribed to the Workflow Monitor
  surface. Internally, it polls pg-boss job state (or uses Postgres
  `LISTEN/NOTIFY`) and pushes job status updates as Server-Sent Events to the
  subscribed browser session. No external websocket service is required. The
  minimum-warm API instance ensures SSE connections are always available.
- The AI chain worker is stateless between jobs. Per-job client context
  (`client_id`, `search_path`) is set at job execution time from pg-boss job
  metadata. No module-level shared state holds client-specific data (see
  Block 7 — isolation invariant).

**Boundary notes.**
- Cloud Run is compute substrate only. The AI Layer's Chain Orchestrator, Agent /
  Subagent Execution Units, and Routing Engine (`architecture.md:461-465`) are
  the application-layer logic executing on this substrate. Phase 9 names the
  substrate; the AI execution model is Phase 7 / Phase 8.
- The job queue (Block 2) manages work state. Cloud Run workers consume jobs;
  they do not own queue state.
- The application API server (on Cloud Run) enforces the JWT → `search_path`
  routing described in Block 7. Enforcement logic is the Core Layer's
  Per-Client Isolation Enforcer (`architecture.md:118`); the routing happens
  at the connection level in Cloud Run's application code.

**Build-layer flags.**
- `minInstances`, `maxInstances`, memory, CPU configuration for both Cloud Run
  services → Phase 10.
- Cloud Run Job vs Cloud Run Service selection for AI workers (jobs are better
  for batch invocations; services for long-running queue consumers) → Phase 10.
- SSE connection management, reconnect logic, and maximum concurrent
  SSE connections per instance → Phase 10.
- Cloud SQL Auth Proxy sidecar container version and startup probe → Phase 10.

---

## Block 4 — Auth Backing Service

**Abstract block.** `architecture.md:187` — "Abstract authentication and identity
substrate that the Core Authorization Enforcement Block enforces over."

**Assigned technology.** **Firebase Authentication** (Google product; same GCP
billing account as all other services).

**Topology and pattern.**
- Firebase Auth issues **JSON Web Tokens (JWTs)** with a custom `app_metadata`
  claim encoding per-user identity and per-client context:

  ```
  app_metadata: {
    client_id: "<uuid>",   // null for Operator / Sysadmin personas
    os_role:   "operator" | "manager" | "contractor" | "client" | "sysadmin"
  }
  ```

- The API server (Block 3) verifies the Firebase JWT on every inbound request
  using the Firebase Admin SDK. The `client_id` claim drives `search_path`
  routing (Block 7). The `os_role` claim drives persona routing and RLS
  policy selection.
- **MFA:** Firebase Auth supports TOTP MFA (Time-based One-Time Password).
  TOTP MFA is enforced for the `operator` and `manager` roles via an
  `aal` (assurance level) check in the API server middleware. Details are
  Phase 10.
- **Session expiry:** Firebase Auth's short-lived ID tokens (~1 hour) with
  silent refresh via refresh tokens. The portal frontend uses `onAuthStateChange`
  to catch `SIGNED_OUT` events and redirect before stale-token API calls surface
  as errors.
- The Authorization Enforcement Block (`architecture.md:117`) — the Core Layer
  block that enforces Phase 1 Governance rules (DEC-026) and the Phase 2
  Permission Matrix — uses the verified JWT claims as its input. Firebase Auth
  is the identity substrate; the Core block does the rule enforcement.

**Boundary notes.**
- Firebase Auth issues identity tokens only. It does NOT author authorization
  rules — those are Phase 1 (DEC-026 / `domains.md`) enforced by the Core Layer.
- Firebase Auth does NOT scope data. The JWT's `client_id` claim is the signal
  that the Per-Client Isolation Enforcer (Core, `architecture.md:118`) and the
  Per-Client Data Scoping Scheme (Infrastructure, Block 7) act on. Firebase Auth
  produces the claim; Block 7 uses it.

**Build-layer flags.**
- Firebase project configuration, authorized domains, and OAuth provider setup
  → Phase 10.
- TOTP MFA enforcement middleware implementation → Phase 10.
- Service-account key provisioning for the Firebase Admin SDK on Cloud Run
  → Phase 10 (use Workload Identity, not key files).

---

## Block 5 — Secret Store

**Abstract block.** `architecture.md:188` — "Abstract secrets vault that the
Core Credential / Secret Handling Block reads from."

**Assigned technology.** **Google Cloud Secret Manager**.

**Topology and pattern.**
- All application secrets (database passwords, Firebase Admin SDK credentials,
  external API keys for AI model providers, channel API keys) are stored as
  Secret Manager secrets. No secret is held in environment variable files at
  rest, in Docker images, or in the repository.
- Cloud Run services access secrets at startup via Secret Manager's native
  Cloud Run integration: secrets are mounted as environment variables or
  volume-mounted files, using the Cloud Run service's IAM service account for
  access control. No SDK call is needed in application code for bootstrap
  secrets.
- Per-module secret scoping: secrets for different Feature Modules' external
  integrations are stored as separate named secrets; each Cloud Run service's
  IAM policy grants `secretmanager.versions.access` only on the secrets it
  requires. This realizes module-level isolation consistent with Feature Modules
  as mountable product units (Phase 4, `extensibility.md:426`).
- The Credential / Secret Handling Block (`architecture.md:119`) — the Core
  Layer block that manages credential scoping, rotation, and re-auth — reads
  from this store. Secret Manager is the vault; the Core block is the
  handling logic above it.

**Boundary notes.**
- Secret Manager is the vault substrate only. Rotation policy, re-auth triggers,
  and the Dual-Path manual re-auth credential swap (DEC-037) are the Core Layer's
  Credential / Secret Handling Block.
- Firebase Auth tokens are not stored in Secret Manager — they are issued
  dynamically by Firebase Auth (Block 4) and verified at runtime.

**Build-layer flags.**
- Secret naming convention and version rotation policy → Phase 10.
- IAM grant matrix (which service account gets access to which secret) → Phase 10.
- Secret audit log configuration → Phase 10.

---

## Block 6 — Observability Infrastructure

**Abstract block.** `architecture.md:189` — "Abstract logging, metrics, and
tracing substrate for runtime visibility."

**Assigned technology.** Three complementary GCP-aligned services:

1. **GCP Cloud Logging** — structured application log ingestion (primary).
2. **GCP Cloud Monitoring** — GCP service metrics (Cloud SQL, Cloud Run,
   Cloud Storage) and uptime checks.
3. **Grafana Cloud free tier** — custom dashboards and distributed trace
   spans for AI chain jobs (OpenTelemetry → Grafana Tempo).

**Topology and pattern.**
- All Cloud Run services (API server, AI workers) emit **JSON-structured logs**
  with mandatory fields per log line: `timestamp`, `job_id`, `workflow_id`,
  `client_id`, `step_name`, `status`, `duration_ms`, `error` (if applicable).
  Cloud Run's built-in log ingestion pipes these to Cloud Logging automatically.
  No log agent is required on any host.
- GCP Cloud Logging free tier (50 GB/month ingestion) is not exceeded at
  30-client moderate volume. Structured log queries support the Workflow Monitor
  surface's historical log view and failed-job investigation.
- **AI chain tracing:** each AI model invocation inside a chain emits an
  OpenTelemetry span: `model_id`, `tokens_in`, `tokens_out`, `latency_ms`,
  `step_name`, `chain_id`, `client_id`. Spans are shipped to Grafana Cloud
  Tempo (free tier: 50 GB traces / month, 14-day retention). The
  `UsageRecord` entity (AI Operations domain, Phase 1 / DEC-038) is the
  business-layer record of this trace; the OTel span is the operational
  substrate.
- **Frontend error tracking:** Sentry (free tier, 5K errors / month) provides
  browser-side error capture for the persona portals. Sentry is an
  application-layer concern; it is noted here as the observability surface
  assigned to the frontend, not an Infrastructure block in Phase 8's sense.
- The Workflow Monitor Operating Surface (`experience-architecture.md:239`) —
  the persona-visible view of AI and workflow execution state — reads from two
  sources: the pg-boss `pgboss.job` table (live job state, directly queryable)
  and the structured Cloud Logging log stream (historical). The observability
  infrastructure is the substrate that populates both.

**Boundary notes.**
- This block is the logging / metrics / tracing substrate. The Agent & Workflow
  Monitor surface (`architecture.md:403`) renders this data for Operator and
  Manager personas — that is Phase 2 / Experience Layer, not re-authored here.
- No self-hosted Prometheus, Grafana, or Loki stack runs on any VM. Grafana
  Cloud free tier provides the dashboard capability without additional compute.

**Build-layer flags.**
- OpenTelemetry SDK integration in Cloud Run worker code → Phase 10.
- Grafana Cloud workspace configuration and Tempo data-source setup → Phase 10.
- Cloud Monitoring uptime check targets and alert policies → Phase 10.
- Sentry DSN configuration per persona portal → Phase 10.

---

## Block 7 — Per-Client Data Scoping Scheme

**Abstract block.** `architecture.md:190` — "Data-organization layout within the
Persistent Store that makes per-client logical data separation a storage-level
reality — the substrate beneath the Core Per-Client Isolation Enforcer."

This block is expanded to first-class depth because per-client data isolation is
the most architecturally load-bearing decision in the Phase 9 stack.

**Assigned technology.** **Schema-per-client in PostgreSQL (Cloud SQL)**, with
**Row-Level Security (RLS) as belt-and-suspenders** within each client schema.

---

### Schema Layout

The Cloud SQL Postgres instance is organized as follows:

```
public schema
  ├── clients                 (OS-level client registry)
  ├── workforce_identities    (Phase 1 Workforce — identity, role, capacity)
  ├── governance_policies     (Phase 1 Governance — policy, authorization rules)
  └── [other platform-level tables shared across all clients]

client_{uuid} schema  [one per client account]
  ├── crm_*                   (CRM domain: Lead, Client Account, Brand, Service Agreement)
  ├── service_delivery_*      (Service Delivery: Engagement, Deliverable, Revision Cycle)
  ├── client_success_*        (Client Success: Approval Response, Escalation Case,
  │                            Coordination Request, Ticket)
  ├── knowledge_*             (Knowledge: Client Brain, Knowledge Artifacts)
  ├── community_*             (Community: Comment, Direct Message, Conversation)
  ├── intelligence_*          (Intelligence: Insights, Recommendations, Scores)
  ├── media_asset_refs        (Media & Assets: metadata references; binaries → GCS)
  ├── ai_operations_*         (AI Operations: UsageRecord)
  └── [workflow_instances, publish_intents, and other cross-domain operational tables]
```

**Rationale for schema-per-client (vs RLS-only):**

Schema-per-client provides a **structural** data boundary — one client's data is
physically unreachable from another client's Postgres session, not merely
policy-filtered. This is the right foundation for a system managing sensitive
strategic content (Client Brain, Deliverables, AI-generated artifacts). RLS-only
on a shared schema depends entirely on policy correctness; a single missing policy
exposes all clients' data for that table.

Cloud SQL with the Cloud SQL Auth Proxy in **session mode** supports
`SET search_path` persistence across the connection lifetime. This makes
schema-per-client viable on the GCP managed stack (unlike Supabase Cloud, which
locks the connection pooler to transaction mode and drops `SET search_path`
between transactions).

---

### JWT → search_path Routing

The routing chain for every inbound request:

1. Firebase Auth (Block 4) issues a JWT with `app_metadata.client_id`.
2. The API server middleware (Core Layer — Per-Client Isolation Enforcer,
   `architecture.md:118`) verifies the JWT and extracts `client_id`.
3. On Cloud SQL connection checkout from the pool, the middleware executes:
   ```sql
   SET search_path TO client_{uuid}, public;
   ```
   where `{uuid}` is the verified `client_id` from the JWT.
4. Every Postgres query in that request executes inside `client_{uuid}` schema.
   No query can reach another client's schema through this connection.
5. For `os_role = 'operator'` or `os_role = 'sysadmin'`, `client_id` is null;
   the search_path is set to `public` only (OS-level tables). Cross-client reads
   for admin analytics use the Cloud SQL service account (bypasses per-client
   schemas) with explicit schema qualifiers.

For **AI chain worker** jobs: the pg-boss job metadata carries `client_id`. The
worker reads `client_id` from job metadata and sets `search_path` on the worker's
Cloud SQL connection before any domain query. No global state is set on the worker
process; each job execution scopes its own connection.

---

### RLS as Belt-and-Suspenders

Each `client_{uuid}` schema carries RLS policies on every tenant-scoped table:

- **Default policy: deny.** Every RLS-enabled table uses `USING (false)` as the
  baseline. Named policies explicitly GRANT access. A missing policy denies rather
  than leaks.
- Policies verify `current_setting('app.current_client_id')` matches the row's
  `client_id` column (where applicable for cross-schema join contexts).
- `SECURITY DEFINER` functions bypass RLS by design. Every function at or below
  the data path must be audited; none in the client-data path should carry this
  flag.
- Views over tenant-scoped tables use `CREATE VIEW ... WITH (security_barrier = true)`
  to prevent predicate-pushdown leakage.

RLS is a second enforcement layer. Because the `search_path` is already scoped to
the correct client schema, an RLS misconfiguration now causes a deny within the
correct schema — it cannot expose a different client's data, because that client's
schema is not in the path.

---

### Service-Role Discipline (Security Invariant)

The Cloud SQL service account (used by admin tooling and migration runners) can
bypass `search_path` isolation by specifying explicit schema qualifiers. This
account must NEVER be used by client-facing API handlers or AI workers. It is
reserved exclusively for:

- Migration runners (Phase 10)
- Administrative / reporting queries run by the Operator persona under explicit
  audit context

Violation of this invariant is the single highest-consequence security failure in
the stack: it exposes all client schemas to an unauthenticated application path.

---

### Per-Client Lifecycle

**Onboarding a new client:**
1. Insert a row into `public.clients` (registers the client identity).
2. `CREATE SCHEMA client_{uuid}`.
3. Run the migration set against `client_{uuid}` (same migration files applied
   to all client schemas — see Build-layer flag below).
4. Seed initial RLS policies for `client_{uuid}`.

**Offboarding / data deletion:**
1. `DROP SCHEMA client_{uuid} CASCADE` — removes all domain data for the client
   in a single operation.
2. Delete the `public.clients` row.
3. Archive or delete GCS objects under `clients/{uuid}/` prefix (Block 9).

This lifecycle is operationally clean: onboarding and offboarding are
single-schema operations, not multi-table `DELETE WHERE client_id = X` sweeps
across a shared schema.

**Boundary notes.**

The Per-Client Data Scoping Scheme is the substrate. The Core Layer's
Per-Client Isolation Enforcer (`architecture.md:118`) is the enforcement logic
above it that sets `search_path` per request. These are distinct: substrate
(Infrastructure, this block) vs enforcement (Core Layer). Per the Core ↔
Infrastructure cut (`architecture.md:134-136`):

| Core block | Its Infrastructure counterpart (this block) |
|---|---|
| Per-Client Isolation Enforcer | Per-Client Data Scoping Scheme |

Binary assets (images, documents, AI-generated files) for the Media & Assets
domain are NOT stored in per-client Postgres schemas — they live in GCS under
`clients/{uuid}/` prefixes (Block 9). Cloud SQL holds metadata references
(`media_asset_refs`) only.

**Build-layer flags.**
- Migration runner implementation (script that iterates `client_{uuid}` schemas
  and applies the same migration set to each on deploy) → Phase 10.
  This runner must be automated from day one; it is the operational prerequisite
  for any schema change at scale.
- Exact RLS policy set per table, per domain → Phase 10.
- Cloud SQL Auth Proxy session-mode pooling configuration → Phase 10.
- Connection pool allocation for the admin / service account path → Phase 10.
- Performance threshold for schema-per-client scalability review
  (informational: structurally sound to ~150–200 schemas on Cloud SQL;
  beyond that, catalog pressure and migration-runner runtime become
  Build-layer operational concerns) → Phase 10.

---

## Frontend Serving

*(Not a Phase 8 Infrastructure Layer block; included here because Phase 9 is the
phase that assigns the serving substrate for the OS frontend.)*

**Assigned technology (default).** **Firebase Hosting** — Google product; same
GCP billing account and Google account as all other services. Zero-ops static
serving, global CDN, automatic SSL, free tier (10 GB storage, 360 MB/day
bandwidth). Covers development through early production.

**Alternative (AU-edge).** **Cloudflare Pages** — AU-edge nodes in Sydney,
Melbourne, and Perth; unlimited deploys and requests on the free tier. Preferable
if Australian client latency is a primary concern. Requires testing Next.js
compatibility with the Cloudflare Workers runtime (not standard Node.js).

**Frame for later flip:** The frontend serving choice is not load-bearing to the
rest of the infrastructure stack. Firebase Hosting is the default because it keeps
all services under one Google account with zero additional configuration. Switching
to Cloudflare Pages is a deployment target change — no backend, auth, database, or
storage change required.

**Topology and pattern.**
- Single Next.js monorepo; one deployment; role-based routing via middleware
  (per `app_metadata.os_role` from the Firebase Auth JWT). Five persona portals
  are route segments within the same app, not separate deployments.
- Feature Modules mount as Next.js dynamic-import lazy route segments; no module
  federation at this stage.
- API calls from the portal go to the Cloud Run API server (Block 3).
- Media / asset uploads go directly to GCS (Block 9) via presigned PUT URLs
  issued by the API server; binary files never transit the API server.

---

## Object Storage — Media & Assets

*(Not a Phase 8 Infrastructure Layer block by name, but is the physical storage
substrate for the Media & Assets domain entity (DEC-033 / `architecture.md:246`)
and is required by Block 7's per-client layout.)*

**Assigned technology.** **Google Cloud Storage (GCS)**, standard class.

**Topology and pattern.**
- One GCS bucket per environment (production, staging). Per-client isolation
  is enforced via **path-prefix scoping**: all client-owned objects are stored
  under `clients/{client_id}/` prefixes. The API server enforces that a given
  authenticated `client_id` may only receive presigned URLs scoped to its own
  prefix.
- **Upload pattern:** frontend requests a presigned PUT URL from the API server
  → API server validates auth and generates a time-limited signed URL scoped to
  `clients/{client_id}/uploads/{uuid}` → frontend uploads directly to GCS.
  Binary files do not transit Cloud Run. The API server records the GCS path
  in `media_asset_refs` (Block 7 / Cloud SQL) on upload completion.
- **Download / serve pattern:** the API server issues presigned GET URLs for
  client-owned objects. The frontend never constructs GCS paths directly.
- Client Asset lifecycle states (raw / client-uploaded / AI-generated / produced)
  map to GCS object metadata labels; lifecycle transition is a Build-layer concern.
- **Offboarding:** all objects under `clients/{client_id}/` are deleted or
  archived as part of the per-client offboarding procedure (see Block 7 — Per-
  Client Lifecycle).

**Boundary notes.**
- GCS is object storage only. Metadata, rights, and provenance for Client Assets
  belong to the Media & Assets domain (`architecture.md:246`, `domains.md:3801`,
  DEC-033). GCS holds the binary; Cloud SQL holds the metadata reference.
- GCS path prefixes enforce isolation at the application layer (the API server
  scopes presigned URLs). GCS itself has no native per-client RLS; the API
  server is the enforcement point.

**Build-layer flags.**
- Exact bucket name, CORS policy, uniform bucket-level access configuration
  → Phase 10.
- GCS object lifecycle policy (auto-archive / delete for old client-upload
  versions) → Phase 10.
- CDN configuration for GCS-served assets (Cloud CDN or Cloudflare proxy)
  → Phase 10.
- Retention and purge policy aligned with Governance domain (DEC-026)
  → Phase 10.

---

## Platform Summary

| Abstract block (Phase 8) | Assigned technology (Phase 9) | Platform |
|---|---|---|
| **Persistent Store** | Cloud SQL for PostgreSQL | GCP managed |
| **Job Queue / Event Bus** | pg-boss (runs in Cloud SQL) | In-Postgres |
| **Worker / Job Runtime** | Cloud Run (API server + AI workers) | GCP serverless |
| **Auth Backing Service** | Firebase Authentication | GCP / Google |
| **Secret Store** | Cloud Secret Manager | GCP managed |
| **Observability Infrastructure** | Cloud Logging + Cloud Monitoring + Grafana Cloud free tier | GCP + Grafana |
| **Per-Client Data Scoping Scheme** | Schema-per-client in PostgreSQL + RLS belt-and-suspenders | In Cloud SQL |
| Frontend Serving | Firebase Hosting (default) / Cloudflare Pages (AU-edge alt.) | Google / Cloudflare |
| Object Storage (Media & Assets) | Cloud Storage (GCS) standard class | GCP managed |

All primary services are GCP-native or GCP-hosted. No VPS, no self-hosted
Supabase stack, no self-hosted Redis or Postgres is in the production data path.

---

## Status

Phase 9 Infrastructure Design — **first write complete** (DEC-041; 2026-06-09).

All seven abstract Infrastructure Layer blocks have physical technology assigned.
Frontend serving and object storage are assigned as supplementary entries.

Pending gated events (separate decisions, not Phase 9's to resolve):

- Phase 10 Build Roadmap (`roadmap.md`) — translates assigned technologies into
  build steps, MVP scope, and implementation sequence.
- Migration-runner implementation and schema-per-client tooling — Build-layer
  concern flagged throughout this file.
- Q-017 (Workflow Management Engine) — open; if resolved into the AI Layer
  (Phase 8), the worker topology in Block 3 may gain a dedicated Cloud Run
  service.
- Q-020 (access-status / connection-health owner) — open; affects how the
  Dual-Path / Manual-Fallback routing signal is surfaced in the infrastructure
  layer (likely a flag in the pg-boss job metadata or a connection-health table
  in Cloud SQL).
- Q-022 (prompt / template versioning) — open; affects whether a versioned
  prompt store is added to Block 1 or Block 9.
- Remaining Phase-1 entity reopenings (Campaign, Ad-Account, Schedule, Consent)
  — each may add tables to `client_{uuid}` schemas; no infrastructure change
  required, schema migration runner accommodates new tables automatically.

This file does not resolve any carried-open question. It will be updated when
relevant gates close.
