# Faraz OS — Build Roadmap (Phase 10)

## Purpose

`roadmap.md` sequences what Phases 1–9 defined into a dependency-ordered
build plan. It is the Phase 10 target and the direct downstream of Phase 9.

This file answers: *"What do you build, in what order, and at what concrete
specification?"* It does not re-define the architecture — that is Phases 1–8.
It does not assign technology to abstract blocks — that is Phase 9. It builds
on the Phase 9 technology assignments and lands the specifics that Phase 9
explicitly deferred to the build layer.

---

## Altitude

Phase 10 operates at **build-roadmap altitude**: concrete build decisions,
dependency-ordered stages, named pre-build gates, and the exact specifications
that Phase 9 (`infrastructure.md`) flagged as `Build-layer → Phase 10`.
This is the first and only phase in the Faraz OS stack where these specifics land.

Phase 10 **lands**:
- Exact instance SKUs, storage sizes, connection pool limits.
- Named queue namespaces, per-queue priority tiers, dead-letter policies.
- Migration runner implementation spec (schema-per-client create-on-demand
  + same-migration-set-on-deploy).
- Exact RLS policy set per table, per domain.
- CI/CD pipeline config, deployment runbook, autoscaling thresholds.
- API middleware implementation specs (Firebase JWT → `search_path` routing).
- Secret naming convention, IAM grant matrix.
- Cloud Run Job vs Cloud Run Service selection for AI workers.
- OpenTelemetry SDK integration, Grafana workspace, alert policies.
- Bilingual / IR-sensitivity build constraints on Content and Publishing.

Phase 10 **does not**:
- Re-architect or redefine what blocks, layers, or domains ARE — that is
  Phases 1–8.
- Re-assign technology to abstract blocks — that is Phase 9.
- Resolve carried-open Phase-1 questions (Q-003, Q-006, Q-007, Q-024) — it
  sequences them as named gates; each resolves in its own Phase-1 decision.
- Write code — that is Phase 11 (Claude Code Operating System).

---

## Strategic Context

Faraz OS is a **single-tenant** system — one agency, its own operation, no
multi-tenant isolation to architect. The base it runs on is the real product:
a clean, module-mountable, AI-native platform. Faraz OS is the showcase build
and reference architecture for that base.

**MVP → V1 as the near-term showcase target.** MVP and V1 together form the
contiguous showcase deliverable — the sequence to build and present to
leadership as a working demonstration of the AI-native agency operating system:

- **MVP** = the agency operating loop provably working: all 7 fixed-flow
  workflows running end-to-end for a single client, T1-critical domains active,
  schema-per-client isolation proven.
- **V1** = the same loop in a production-ready form: all 5 persona portals
  fully populated across 16 surfaces, Permission Matrix enforced, T1 domains
  complete. V1 is MVP polished to a demo-ready standard.

MVP → V1 is the near-term target. V2 and Future are the later expansion horizon.

**Bilingual and IR-sensitivity — first-class build constraints.** Faraz OS
serves Iranian clients. Content production and publishing carry two
non-negotiable constraints that must be baked in from the start:

1. **Farsi/English bilingual** — content artifacts, PromptTemplates
   (Knowledge domain, DEC-044), channel publishing payloads, and portal UI
   all have bilingual requirements. The Content domain schema must carry a
   language field as a first-class attribute. PromptTemplate must support
   Farsi-language templates. Publishing payloads must handle right-to-left
   rendering and Unicode normalization.

2. **Iran-specific platform-access reality** — some publishing and social
   channels may be regionally restricted or intermittently accessible.
   The Dual-Path / Manual Fallback routing pattern (DEC-037,
   `workflows.md:238`) is the primary mitigation. It is T1-critical, not
   an optional enhancement — for Iranian client deployments, platform-access
   intermittency is a routine operating condition, not an edge case.

Both constraints surface explicitly in the T1 Launch stage as build gates
before Content domain schema and Publishing pipeline config are written.
Phase 11 (Claude Code) must validate these constraints before writing
Content or Publishing schema, pipeline code, or PromptTemplate structures.

---

## Governing Boundary Test

From `infrastructure.md:8-12`, the Phase 9 altitude declaration:

> This file does not specify build procedures, exact instance SKUs, or
> deployment scripts — that is Phase 10.

**Phase 9 → Phase 10 cut:**
- Phase 9 ASSIGNS: service names, topology, governing patterns, security
  invariants, and illustrative sizing (flagged as not locked in Phase 9).
- Phase 10 IMPLEMENTS: the exact parameters, policies, migration runner specs,
  and enforcement mechanism details for each Phase 9 technology assignment.

**Phase 10 → Phase 11 cut:**
- Phase 10 SPECIFIES: what to build, in what order, at what concrete spec.
  It may include schema sketches and pseudocode as specifications.
- Phase 11 EXECUTES: Claude Code writes and runs the implementation against
  these specifications.

---

## How to Read This File

Each build stage uses a **six-field per-stage skeleton**:

1. **Stage** — label and T-tier mapping (T1 / T2 / T3 / v2).
2. **Purpose** — what working artifact this stage delivers.
3. **Depends on** — prior stage(s) that must be complete before this begins.
4. **In scope** — domains, capabilities, surfaces, and workflows active here.
5. **Build-layer decisions that land here** — the Phase-9 `Build-layer flag
   → Phase 10` items from `infrastructure.md` resolved in this stage.
6. **Gates and deferred items** — Phase-1 questions that must resolve before
   key schema writes, and v2/Future items that first slot or activate here.

The four top-level sections (MVP / V1 / V2 / Future) match the Phase 10
sub-items in `Faraz-OS-Canon.md:162-165`. Foundation and Core Layer are nested
within MVP as build sub-stages — they are prerequisites, not product milestones.

---

## Non-goals

`roadmap.md` does NOT author:

- Re-definition of abstract block names, layer structure, or logical roles —
  Phase 8 (`architecture.md`).
- Re-assignment of technology to abstract blocks — Phase 9 (`infrastructure.md`).
- Domain entity schemas, field lists, or Postgres table definitions — Phase 1
  domain truth (`domains.md`); written by Phase 11 under the constraints this
  file establishes.
- Resolution of carried-open questions (Q-003, Q-006, Q-007, Q-024) — each is
  a separate Phase-1 gated decision that gates specific schema writes.
- Phase-1 entity reopenings for T3 entities (Campaign, Ad-Account, Schedule,
  Consent) — each requires its own Phase-1 gate before any domain schema write.
- Application code, API implementation, or test suites — Phase 11.
- Multi-tenant isolation — outside T1 scope entirely; its own major
  architecture gate if ever needed.
- Visual workflow editing (DEC-048 v2 item) — requires Phase 2 / 4 / 6 / 7
  multi-phase gate to open; deferred.

---

## MVP

MVP delivers the **agency operating loop provably working**: all 7 fixed-flow
workflows running end-to-end for a single client, schema-per-client isolation
proven, T1-critical domains active, and bilingual / IR-sensitivity constraints
baked in from the start.

MVP is built in three dependent sub-stages: Foundation → Core Layer → T1 Launch.

---

### MVP / Foundation

**Stage:** Foundation — T1 prerequisite. No domain data enters before this
stage gate passes.

**Purpose:** A provisioned GCP environment with schema-per-client isolation
proven for a test client before any domain or application code is written.
The Foundation stage gate is the build gate for every stage that follows.

**Depends on:** nothing (first stage).

**In scope — all Phase 9 infrastructure blocks instantiated:**

- `infrastructure.md:98` Block 1 (Persistent Store): Cloud SQL instance
  provisioned; Cloud SQL Auth Proxy sidecar configured.
- `infrastructure.md:141` Block 2 (Job Queue / Event Bus): `pg-boss` schema
  bootstrapped inside the Cloud SQL instance.
- `infrastructure.md:201` Block 3 (Worker / Job Runtime): Cloud Run API server
  deployed (`minInstances = 1`); Cloud Run AI worker deployed (`minInstances = 0`).
- `infrastructure.md:263` Block 4 (Auth Backing Service): Firebase Authentication
  project configured; custom JWT claims (`client_id`, `role`) wired.
- `infrastructure.md:316` Block 5 (Secret Store): GCP Secret Manager secrets
  populated — database credentials, Firebase service account key, AI model API keys.
- `infrastructure.md:357` Block 6 (Observability): Cloud Logging + Cloud
  Monitoring baseline configured; Grafana Cloud workspace provisioned; Sentry
  DSN assigned per persona portal.
- `infrastructure.md:411` Block 7 (Per-Client Data Scoping Scheme):
  **schema-per-client migration runner implemented** — the single most
  load-bearing build item in the stack (see Critical-Path Risk below).
- `infrastructure.md:581` Frontend Serving: hosting method selected and
  provisioned.
- `infrastructure.md:614` Object Storage (Media & Assets): GCS bucket
  provisioned (single bucket; per-client object-prefix namespace). Activated
  at T1 for Publishing payload storage; full Client Asset integration is V2.

**Build-layer decisions that land here:**

| Block | Phase-9 `Build-layer flag → Phase 10` item |
|---|---|
| Block 1 | Exact Cloud SQL SKU (instance type, storage size, connection pool limits) |
| Block 1 | Schema-per-client migration runbook (same migration set applied to every client schema on deploy) |
| Block 1 | Cloud SQL Auth Proxy sidecar container version and startup probe config |
| Block 1 | Read replica provisioning criteria (if/when query volume warrants it) |
| Block 2 | `pg-boss` version, connection pool for queue schema, dead-letter handling policy |
| Block 3 | `minInstances`, `maxInstances`, memory, CPU for both Cloud Run services |
| Block 3 | Cloud Run Job vs Cloud Run Service for AI workers |
| Block 3 | Maximum concurrent SSE connections per API server instance |
| Block 4 | Firebase JWT custom claims schema (field names, types, required fields) |
| Block 4 | TOTP MFA enforcement middleware spec (which personas require MFA at login) |
| Block 5 | Secret naming convention (naming pattern for all Secret Manager secret IDs) |
| Block 5 | IAM grant matrix (which service account accesses which secret) |
| Block 5 | Secret audit log configuration |
| Block 6 | GCS bucket naming convention, ACL policy, object lifecycle rules |
| Block 7 | **Migration runner implementation**: per-client schema create-on-demand + same-migration-set-on-deploy |
| Block 7 | Exact RLS policy set per table, per domain |
| Block 7 | Cloud SQL Auth Proxy session-mode pooling configuration |
| Block 8 | OpenTelemetry SDK integration spec for Cloud Run worker code |
| Block 8 | Grafana Cloud Tempo data-source configuration |
| Block 8 | Cloud Monitoring uptime check targets and alert policies |
| Block 8 | Sentry DSN configuration per persona portal |

**Stage gate — MUST PASS before Stage 2 begins:**
> Mint one test client → set `search_path` to that client's schema → insert
> rows → verify via adversarial cross-client query that RLS blocks visibility
> from a second test-client connection. Zero cross-client data visibility is
> the pass criterion. This test must run before any domain entity data enters
> the system.

**Critical-path risk:** The schema-per-client migration runner
(`infrastructure.md:411`) is the **single highest-risk build item** in the
stack. A defect here means cross-client data visibility — a data isolation
failure before any application code runs. Harden with adversarial isolation
tests (multiple clients, concurrent inserts, cross-client query attempts)
before any domain entity data enters the system.

---

### MVP / Core Layer

**Stage:** Core Layer — T1 prerequisite. Application server fully wired before
domain schemas are written.

**Purpose:** Requests correctly scoped to client context via the Firebase JWT →
`search_path` middleware; secrets read from Secret Manager; `pg-boss` poller
live; SSE endpoint up. The Core Layer stage gate confirms the Authorization
Enforcement Block is functioning before any real domain data enters.

**Depends on:** MVP / Foundation stage gate passed.

**In scope — Core Layer blocks (`architecture.md:100`):**

- **API Router**: client-scoped request routing; `client_id` extracted from
  verified Firebase JWT and injected into connection context.
- **Authorization Enforcement Block**: Firebase JWT → `search_path` middleware
  (`infrastructure.md:466`). Enforces Phase-2 Permission Matrix rules
  (DEC-026); authors no rules.
- **Credential / Secret Handling Block**: reads from Secret Manager (Block 5)
  at startup; no credentials in environment variable files.
- **Extension Contract Surface**: scaffold-level instantiation — passive at
  this stage, no extension registered yet.
- **Job Queue Integration Block**: `pg-boss` poller embedded in API server;
  queue consumer for the T1 workflow stages.
- **Domain Event Bus**: integration wired in API server.
- **SSE endpoint**: workflow execution state feed for the Agent & Workflow
  Monitor surface (Phase 2); provides real-time workflow state without polling.
- **Feature-Module Mounting Engine**: scaffold-level instantiation — passive
  at this stage, no Feature Module mounted yet.

**Build-layer decisions that land here:**

| Block | Item |
|---|---|
| Block 2 | Named queue namespace convention (naming pattern for all `pg-boss` queue names used by the 7 workflows) |
| Block 2 | Per-queue priority tiers definition |
| Block 7 | Firebase JWT → `search_path` routing: middleware implementation spec (Firebase Admin SDK JWT verification → `client_id` claim extraction → Cloud SQL Auth Proxy session-mode `search_path` set per connection) |

**Stage gate — MUST PASS before Stage 3 begins:**
> Firebase JWT with a valid `client_id` claim → API server sets `search_path`
> to that client's schema → query returns only that client's rows. Adversarial
> test: JWT from client A routed through client B's schema path must be blocked
> at the Authorization Enforcement Block with zero data leakage. `pg-boss`
> poller receives and acknowledges a test job. SSE endpoint emits an event on
> test trigger.

**Critical-path risk:** The Firebase JWT → `search_path` middleware is the
second-highest-risk build item. Misconfiguration results in the wrong
`search_path` being set — exposing one client's schema to another client's
session. Must be verified with adversarial cross-client tests before domain
entity schemas are populated.

---

### MVP / T1 Launch

**Stage:** T1 Launch — the single-tenant showcase MVP.

**Purpose:** All 7 fixed-flow workflows running end-to-end for a single client,
with T1-critical domain schemas written, AI chain executing, cost metering
active, bilingual / IR-sensitivity constraints baked in, and Dual-Path /
Manual Fallback routing wired. The minimum demonstrable AI-native agency
operating system.

**Depends on:** MVP / Core Layer stage gate passed + Q-006 and Q-024 Phase-1
gates resolved (see explicit pre-build gates below).

---

#### T1 Launch — Pre-build gates

These are Phase-1 decisions — they resolve in `decisions.md`, not here.
Phase 10 sequences them as named mandatory gates before specific schema writes.

**Gate A — Q-006** (Service Agreement / Engagement Scope aggregate boundary):
must be resolved before the CRM domain schema (Service Agreement) and the
Service Delivery / Engagement Scope schema are written.

**Gate B — Q-024** (Ticket ↔ Escalation Case lifecycle coupling,
`domains.md:1720`): must be resolved before the Client Success domain
bounded-context schema (Ticket, Escalation Case relationship) is written.

These gates do not block Foundation or Core Layer stages. They block the
specific schema writes in T1 Launch.

---

#### T1 Launch — In scope

**T1-critical domains:**

| Domain | Entities and notes |
|---|---|
| CRM | Client Account, Brand (DEC-036), Contact, Service Agreement (DEC-034) |
| Client Success | Client Success Case, Escalation Case, Ticket (DEC-039), Coordination Request |
| Engagement | Engagement entity, Engagement Scope |
| Content | Content artifacts, production state; language field first-class (bilingual constraint — see below) |
| Publishing | `publish_intents` table, named queues, channel publishing; bilingual payload handling required |
| Knowledge | Client Brain (per-Brand partition, DEC-045), Knowledge Base, PromptTemplate (DEC-044; Farsi template support required) |
| AI Operations | UsageRecord (per-job AI cost metering, DEC-038) |
| Governance | Authorization rules (DEC-026); policy enforcement |

**Capabilities:** all 8 Phase-3 capabilities (`capabilities.md`) wired to
their T1 domains.

**Plugins in scope:** Channel Model with access-status / connection-health
(DEC-046); Provider Model; Plugin Model; Extension Contracts scaffold; AI
Model Routing Policy.

**Workflows — all 7 fixed-flow workflows (`workflows.md:265`):**

| Workflow | Canon entry |
|---|---|
| Lead → Client | `workflows.md:272` |
| Client → Strategy | `workflows.md:291` |
| Strategy → Production | `workflows.md:309` |
| Production → Approval | `workflows.md:330` |
| Approval → Publishing | `workflows.md:348` |
| Publishing → Reporting | `workflows.md:368` |
| Learn → Memory Update | `workflows.md:387` |

Dual-Path / Manual Fallback routing (`workflows.md:238`, DEC-037) is wired
alongside the 7 workflows — not deferred. For Iranian client deployments,
platform-access intermittency is a routine operating condition.

**AI Layer (T1):**
- Chain Orchestrator.
- Agent / Subagent Identity (DEC-031).
- Routing Engine (applies the Phase-4 AI Model Routing Policy).
- Model Invocation Interface (executes against the Phase-4 Model abstraction).

**Build-layer decisions that land here:**

| Area | Item |
|---|---|
| Block 2 | `publish_intents` table schema and uniqueness constraint |
| Block 2 | Migration-path trigger criteria for BullMQ upgrade (if/when `pg-boss` polling throughput warrants) |
| Block 7 | Domain entity schemas for all T1 domains (first live write into per-client schemas; Q-006 and Q-024 gates must be resolved first) |
| Content domain | Language field (`fa` / `en` / `bilingual`) on all content artifacts — first-class schema attribute |
| Knowledge domain | PromptTemplate schema must support Farsi-language templates; no Latin-charset assumptions |
| Publishing pipeline | Unicode normalization and RTL-safe payload handling for Farsi text in publishing payloads |
| Dual-Path | `access_status` / `connection_health` channel attribute read logic (DEC-046) wired into the Dual-Path routing decision |

---

#### T1 Launch — Bilingual / IR-sensitivity build constraints

These are first-class build constraints, not optional enhancements.
Phase 11 (Claude Code) must validate these five constraints before writing
Content domain schema, Publishing pipeline config, or PromptTemplate structures:

1. The Content domain schema carries a `language` field as a first-class
   attribute on all content artifacts (minimum: `fa` / `en` / `bilingual`).
2. The Knowledge domain PromptTemplate supports Farsi-language templates;
   the PromptTemplate schema makes no Latin-charset assumptions.
3. Publishing pipeline payloads handle right-to-left rendering and Unicode
   normalization for Farsi text across all channel types.
4. Dual-Path / Manual Fallback (DEC-037) is a T1-required routing pattern —
   wired at T1 because Iranian channel platforms may be intermittently
   inaccessible independent of connection health state.
5. Portal UI text surfaces that display client-generated content must support
   RTL layout without separate layout branches.

---

#### T1 Launch — Stage gate

> End-to-end: Lead → Client → Strategy → Production → Approval → Publishing →
> Learn / Memory Update, for one test client on one test channel. AI chain
> executes at the Production stage. UsageRecord captured in AI Operations.
> Dual-Path routing fires correctly when channel access-status is degraded.
> RLS isolation remains intact throughout the full workflow run (verify
> cross-client query blocked at every domain table touched by the workflow).
> Farsi content artifact created, queued, and published without encoding error.

---

## V1

V1 delivers the **production-ready T1 showcase**: all 5 persona portals fully
populated across 16 surfaces, Permission Matrix enforced end-to-end, and the
MVP operating loop running at demo-ready standard. V1 is MVP polished for
leadership presentation.

**Depends on:** MVP / T1 Launch stage gate passed.

**Q-003 note (Brand aggregate placement):** Q-003 is the Brand *aggregate*
placement question — Brand *entity* placement is already resolved (DEC-036).
Brand is referenced throughout T1 (per-Brand Client Brain partition, DEC-045).
The aggregate boundary affects the Brand schema design. Q-003 should be
resolved as a Phase-1 gate **before V1 schema is finalized** — it is not a
T1 Launch blocker, but building V1 against an unresolved aggregate placement
creates rework risk. Sequence: resolve Q-003 as a Phase-1 decision before
the V1 schema finalization commit.

**In scope:**

- All 5 persona portals (Operator, Manager, Contractor, Client, System
  Administrator) with their Operating Surfaces — 16-surface firm inventory
  (Phase 2, `experience-architecture.md`).
- Permission Matrix enforced through the Core Layer Authorization Enforcement
  Block (DEC-026 rules; Phase-2 surface ↔ resource mapping).
- Navigation Model implemented (surface-movement model, Phase 2).
- Channel Behaviors per channel type (Phase 2).
- Agent & Workflow Monitor surface wired to SSE endpoint — real-time workflow
  execution state; System Administrator Full access.
- Cross-Domain Views (7 firm views, Phase 2) populated with live data.
- Performance & Analytics View: Client persona scoped to own-engagement data
  (DEC-047).
- Feature Modules mountable via Feature-Module Mounting Engine and Extension
  Contract Surface (Phase-4 Feature Module contract, DEC-032, active).

**Stage gate:**
> Each of the 5 personas logs in, reaches their portal surfaces, performs
> their core workflow actions, and sees data scoped per Permission Matrix
> rules. Agent & Workflow Monitor shows real-time workflow execution state for
> the System Administrator. Cross-client data remains invisible. Q-003
> resolved; Brand aggregate schema finalized before V1 schema commit.

---

## V2

V2 expands the working T1 / V1 system to cover the full Phase-1 domain
inventory and lands the T3 entity gates and deferred features.

**Depends on:** V1 stage gate passed.

---

### V2 / T2 Domain Expansion

The following domains are out of MVP / V1 scope and activate in V2:

| Domain | Key entities and notes |
|---|---|
| Media & Assets | Client Asset (raw / client-uploaded / AI-generated / produced media + rights + provenance + retention-status); full GCS integration (`infrastructure.md:614`) activated for Client Assets |
| Community | Comment, DM, Conversation, Engagement Reply; Sentiment Signal carried as contested / draft flag |
| Intelligence | Derived analytics, per-client cost (from AI Operations UsageRecord), agency-level analytics |
| Finance | Billing, sub-ledger; references CRM Service Agreement commercial spine |
| Service Delivery | Delivery coordination, Coordination Request lifecycle |

Each domain requires its own Phase-1 schema write under the existing
per-client schema layout (Block 7, Foundation stage). No new infrastructure
blocks are required; the GCS per-client object-prefix namespace (provisioned
in Foundation) is activated fully in V2 for Media & Assets.

**Deferred items that gate or slot in V2 (each its own decision):**

- Phase-4 deferred sub-items — Versioning & Compatibility, External
  Integrations, Future Domains — each requires its own un-defer gate before
  Phase-4 content is written for it.
- Community Phase-3 capability + Phase-4 inbound-channel category + Phase-6
  8th workflow (post-publish engagement loop) — three separate gated decisions.
- Asset Intelligence (Phase-5 deferred stub) — its own un-defer gate.

---

### V2 / T3 Entity Gates

The four paused Phase-1 entities activate in V2, each requiring its own
Phase-1 decision gate before any domain schema is written:

| T3 Entity | Gate discipline |
|---|---|
| Campaign | Own Phase-1 decision gate (domain ownership + entity classification) before schema write |
| Ad-Account | Own Phase-1 decision gate before schema write |
| Schedule | Own Phase-1 decision gate before schema write |
| Consent | Own Phase-1 decision gate before schema write |

These entities are realistic within the showcase timeline and are marked V2
(not Future) — gated-but-intended, not permanently deferred. Each Phase-1 gate
must land before the corresponding domain schema write in Phase 11.

---

### V2 / Late Deferred Features

The following features deferred by explicit architecture decisions activate in
V2 late, after V2 / T2 Domain Expansion is stable:

- **Agent Supervision / Observability** (AI Layer deferred slot 2,
  `architecture.md:449`): requires a Phase-7 extension gate before Phase-7
  content is written; then Phase-11 implementation.
- **Visual workflow editing** (DEC-048): multi-phase coordinated feature
  spanning Phase 2, 4, 6, and 7 — requires its own multi-phase gate to open
  before any implementation.

---

## Future

Items held without timeline commitment. Each activates only through an
explicit gated decision:

- **Q-003 residual** — if Brand aggregate placement is not resolved before V1
  finalization (see V1 Q-003 note), it carries to Future.
- **Q-006 residual** — if Service Agreement / Engagement Scope lifecycle
  coupling is not fully resolved in the pre-T1 Launch gate.
- **Q-007** (Engagement Scope assignment artifact) — intentionally deferred;
  no active sequencing needed.
- **Q-024 residual** — if Ticket ↔ Escalation Case lifecycle is not fully
  resolved in the pre-T1 Launch gate; cross-references `domains.md:1720`.
- **Community Phase-6 8th workflow** (post-publish engagement loop) — if not
  taken in V2.
- **Multi-tenant isolation layer** — wholly outside T1 scope; requires a
  separate major architecture gate before any Phase-7 / 8 / 9 changes are made.
- **Navigation Model deferred items** — landing-surface designation,
  notification routing, deep-linking (marked future in Phase 2).
- **Future Personas placeholder** (carried from Phase 2).
- **Phase-4 Future Domains stub** — if not un-deferred in V2.

---

## Open and Deferred Items

The following are carried explicitly and must not be resolved within this file:

- **Q-003** (Brand aggregate placement) — Phase-1 gate; should resolve before
  V1 schema finalization (not a T1 Launch blocker).
- **Q-006** (Service Agreement / Engagement Scope aggregate boundary) —
  Phase-1 gate; must resolve before CRM and Service Delivery schema writes
  in T1 Launch (Gate A above).
- **Q-007** (Engagement Scope assignment artifact) — intentionally deferred.
- **Q-024** (Ticket ↔ Escalation Case lifecycle coupling) — Phase-1 gate;
  must resolve before Client Success bounded-context schema write in T1 Launch
  (Gate B above); cross-references `domains.md:1720`.
- Insight → durable-knowledge threshold (`domains.md:1946`, R-027 set) —
  Phase-1 truth pending; referenced, not resolved.
- T3 Phase-1 entity reopenings (Campaign, Ad-Account, Schedule, Consent) —
  V2 slots; each its own Phase-1 gate before domain schema write.

---

## Status

Phase 10 first write. Date: 2026-06-09.

Scoped and authorized by DEC-049. All four Canon sub-items (MVP / V1 / V2 /
Future) populated on the six-field skeleton.

Phase 10 first-write-complete milestone — consistent with Phase-2 / 6 / 7 /
8 / 9 precedent: a first-write-complete is not a formal phase-complete
declaration. Phase-complete (if separately declared) would require its own
gated decision.

With this write, **all ten architecture content phases (Phases 1–10) now have
first-write entries**.
