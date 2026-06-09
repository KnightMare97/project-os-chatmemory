# Faraz OS — Claude Code Operating System (Phase 11)

## Purpose

`claude-operating-system.md` defines the operating discipline under which
Claude Code executes the Faraz OS build.

This file answers: *"How does Claude Code operate, stay oriented,
self-review, and hand off work during each build session?"*

It is the bridge from the finished architecture (Phases 1–10) to actual code.
It governs process, not product.

---

## Altitude

Phase 11 operates at **operating-system altitude**: build-session discipline,
agent role definitions, mode transitions, prompt-handoff format, development
rules, the coding-standards framework, and the provisioning/credentials
checklist Ali must complete before the first build session begins.

Phase 11 **owns:**
- The four build-time agent roles (operating stances within a Claude Code session)
- The three operating modes (Plan / Build / Review) and their transitions
- Session protocol — start discipline, close-out discipline, GATED vs AUTO split
- Snapshot discipline for build sessions
- Prompt handoff format for cold-start session orientation
- Development rules and the coding-standards framework
- The provisioning and credentials checklist
- The Build-Time CLAUDE.md Template (Appendix A) — a spec embedded here;
  no new CLAUDE.md is created in this architecture repo

Phase 11 **does not own:**
- Architecture content — that is Phases 1–8
- Build roadmap sequencing, stage order, or stage-gate criteria — that is Phase 10
- Domain boundary resolution or carried-open Phase-1 questions
- Application code (that lives in the build repo)
- Any edit to `./CLAUDE.md` in this architecture repo (it is the architecture
  operating contract and must not be touched)

---

## Boundaries

**Phase 10 → Phase 11.**
Phase 10 (`roadmap.md`) says WHAT to build and in what order: stages, blocks,
concrete specifications, and named pre-build gates. Phase 11 says HOW Claude Code
executes that — the operating contract, agent stances, modes, and session
discipline. Phase 10 is the instruction set; Phase 11 is the execution method.

**Phase 11 → actual code.**
Phase 11 ends at "ready to write the first line of code in the build repo."
Code itself lives in the build repo, not here. Architecture-memory snapshots
(this repo) record design history; build-session snapshots (build repo) record
build progress. The two repos are distinct by design.

**This repo's `./CLAUDE.md` is the architecture operating contract.**
It governs AI collaboration on this architecture-memory repo and must never be
edited or replaced by Phase 11 work. Any CLAUDE.md governing the build repo is
the Build-Time CLAUDE.md Template (Appendix A) — a spec written here, to be
instantiated in the build repo at build-repo setup time.

---

## Prerequisites — Provisioning Checklist

Ali must complete this checklist before the first build session begins.
Nothing in this section requires technical expertise beyond following the
GCP and Firebase console UIs — each item is described in plain language.

### 1. GCP Project + Billing

**What it is.** A Google Cloud Platform project is the container for all
Faraz OS cloud resources. Billing must be attached before any paid service
can be used.

**What to do.**
- Create a new GCP project at console.cloud.google.com (e.g. project ID:
  `faraz-os-dev`; adjust for staging/prod later).
- Link a billing account to the project. Without billing, Cloud Run, Cloud SQL,
  and Secret Manager will not activate.
- Note the **Project ID** and **Project Number** — both are needed when granting
  IAM roles.

### 2. APIs to Enable

In the GCP console, navigate to "APIs & Services → Library" and enable each of
the following. All are free to enable; cost is only incurred when used.

| API | Purpose |
|-----|---------|
| Cloud SQL Admin API | Manage Cloud SQL instances |
| Cloud Run API | Run containerized API server and AI worker |
| Cloud Build API | Build Docker images in CI/CD |
| Artifact Registry API | Store Docker images |
| Secret Manager API | Store and access secrets securely |
| Cloud Storage API | Object storage (GCS) |
| Cloud Pub/Sub API | Message queue / event bus |
| Cloud Scheduler API | Scheduled jobs |
| Cloud Logging API | Structured log ingestion |
| Cloud Monitoring API | Service metrics and alerting |
| Cloud Trace API | Distributed tracing |
| Identity and Access Management (IAM) API | Service accounts and roles |
| Firebase Authentication (identitytoolkit.googleapis.com) | User auth tokens |
| Firebase Management API | Link Firebase project to GCP project |

### 3. Firebase Project

**What it is.** Firebase Authentication is the auth backing service
(Phase 9 Block 4). A Firebase project linked to the GCP project is required
for Firebase JWT issuance and verification.

**What to do.**
- Create a Firebase project at console.firebase.google.com.
- Link it to the same GCP project created in Step 1 (Firebase offers this
  during project creation or in Settings → Your project → General).
- Enable the **Email/Password sign-in provider** (and any other providers
  Faraz OS will use) under Authentication → Sign-in method.
- Note the **Firebase Project ID** — it must match the GCP project ID.

### 4. Service Accounts + IAM Roles

**What it is.** A service account is an identity for a non-human actor
(e.g. the API server, the AI worker, the CI/CD pipeline). Each service account
is granted only the roles it needs — no more.

**Create three service accounts** in GCP Console → IAM & Admin → Service Accounts:

#### API Server Service Account
- **Name:** `faraz-os-api-server` (or similar)
- **Roles to grant:**
  - Cloud SQL Client → connects to Cloud SQL via Auth Proxy
  - Secret Manager Secret Accessor → reads secrets at startup
  - Firebase Auth Admin (via Firebase Admin SDK SA key stored in Secret Manager;
    no direct GCP role needed — the SA key grants Firebase Admin access)

#### AI Worker Service Account
- **Name:** `faraz-os-ai-worker` (or similar)
- **Roles to grant:**
  - Cloud SQL Client → connects to Cloud SQL via Auth Proxy
  - Secret Manager Secret Accessor → reads secrets at startup
  - Cloud Storage Object Admin → reads/writes AI output artifacts in GCS
  - Pub/Sub Publisher → publishes job results to event bus
  - Pub/Sub Subscriber → consumes job requests from queue

#### CI/CD Service Account
- **Name:** `faraz-os-cicd` (or similar)
- **Roles to grant:**
  - Cloud Run Developer → deploy Cloud Run services
  - Artifact Registry Writer → push Docker images
  - Cloud Build Editor → trigger builds
  - Service Account User → allow CI/CD to deploy as the API server / AI worker SAs
  - Storage Object Viewer → read build artifacts if needed

### 5. Secrets to Provision — Enumerated List

These are the specific secrets Ali must create in GCP Secret Manager before
the Foundation stage gate can pass. For each: **what it is, where to get it,
and how to store it.**

#### 5a. Cloud SQL Database Password

**What it is.** The password for the database user that the API server and
AI worker use to connect to Cloud SQL. Cloud SQL is the Persistent Store
(Phase 9 Block 1).

**Where to get it.** You create this password yourself — pick a strong
random password (20+ characters, mixed case, numbers, symbols). You will set
this password when you create the Cloud SQL instance and its database user.

**How to store it.** In Secret Manager, create a secret named
`faraz-os-dev-sql-password` (or `faraz-os-prod-sql-password` for prod).
Paste the password as the secret value. Grant the API Server SA and AI Worker SA
`secretmanager.versions.access` on this secret.

#### 5b. Firebase Admin SDK Service-Account Key (JSON)

**What it is.** A JSON key file that gives the API server Firebase Admin SDK
access — specifically the ability to verify Firebase JWTs and read/write
Firebase Auth user records. This is how the API server authenticates incoming
requests (Phase 9 Block 4 / `roadmap.md:257`).

**Where to get it.** In the Firebase console → Project Settings → Service accounts →
"Generate new private key." Download the JSON file. This file contains a private
key — treat it as a password.

**How to store it.** In Secret Manager, create a secret named
`faraz-os-dev-firebase-sa-key`. Paste the entire JSON file content as the
secret value (it is a JSON string). Grant the API Server SA access on this secret.
**Delete the downloaded JSON file from your machine after storing it in
Secret Manager.**

#### 5c. AI Model Provider API Key(s)

**What it is.** An API key (or keys) that the AI worker uses to call external
AI model providers — for example Gemini, Vertex AI, or any other provider
confirmed at build-repo setup per Phase 9's deferred model-provider selection.
If multiple providers are used, each gets its own secret.

**Where to get it.** From the provider's developer console:
- Google Gemini / Vertex AI: console.cloud.google.com → APIs & Services →
  Credentials, or through AI Studio (aistudio.google.com).
- Other providers: their respective developer portals.

**How to store it.** In Secret Manager, create one secret per provider:
`faraz-os-dev-ai-gemini-key`, `faraz-os-dev-ai-openai-key`, etc.
Paste the API key as the secret value. Grant the AI Worker SA access
on each secret it uses.

#### 5d. Channel API Keys (T1 Launch stage — provision when starting T1)

**What they are.** API keys for the social / publishing channels Faraz OS
integrates with (Instagram, LinkedIn, etc.). These are not needed at Foundation
or Core Layer but must be provisioned before the T1 Launch stage begins.

**Where to get them.** From each platform's developer/partner portal.

**How to store them.** One secret per channel:
`faraz-os-dev-channel-instagram-key`, `faraz-os-dev-channel-linkedin-key`, etc.

### 6. Secret Naming Convention

**Pattern:** `faraz-os-{env}-{block}-{type}`

| Field | Values |
|-------|--------|
| `env` | `dev` · `staging` · `prod` |
| `block` | `sql` · `firebase` · `ai` · `channel-{name}` · `gcs` |
| `type` | `password` · `sa-key` · `api-key` · `connection-string` |

**Examples:**
- `faraz-os-dev-sql-password`
- `faraz-os-dev-firebase-sa-key`
- `faraz-os-dev-ai-gemini-key`
- `faraz-os-prod-sql-password`
- `faraz-os-dev-channel-instagram-key`

All secret names across all environments follow this pattern. Names are declared
in the build repo config; none are hard-coded in application code.

### 7. Secret-Handling Discipline

These rules apply at all times, in all build sessions:

- **Secrets go into GCP Secret Manager only.** Never paste a secret into a
  chat message, a canon file, a code file, an environment variable file
  committed to a repo, or a Docker image.
- **Claude Code reads secrets via Secret Manager at runtime.** Cloud Run's
  native Secret Manager integration mounts secrets as environment variables
  at service startup — no SDK call needed in application code for bootstrap
  secrets (`infrastructure.md:329`).
- **Ali authorizes Claude Code sessions** via `gcloud auth login` on his machine
  or a service-account key file located locally. No credentials are embedded
  in session prompts.
- **After downloading any key file** (e.g. Firebase SA JSON), store it in
  Secret Manager immediately and delete the local file.

### 8. Pre-Build Gates (from Phase 10)

Two Phase-1 questions are named mandatory gates before specific domain
schema writes. They do not block Foundation or Core Layer stages.

**Gate A — Q-006** (Service Agreement / Engagement Scope aggregate boundary):
Must be resolved as a Phase-1 decision before the CRM domain schema is written
in any build session. See `roadmap.md:316`.

**Gate B — Q-024** (Ticket ↔ Escalation Case lifecycle coupling):
Must be resolved as a Phase-1 decision before the Client Success domain schema
is written in any build session. See `roadmap.md:320`.

Any Claude Code session approaching a gated domain schema write must halt,
surface the gate, and wait for Ali's Phase-1 decision — it must not write
schema code that assumes a resolution it does not have.

### 9. Pre-Session Checklist

Run before every build session:

- [ ] `gcloud auth list` — confirm the correct account is active
- [ ] `gcloud config get-value project` — confirm the correct GCP project
- [ ] Confirm Secret Manager secrets are populated for the current stage
- [ ] `git fetch origin && git status` — confirm clean branch in sync with `origin/main`
- [ ] Confirm the active stage and block (from `roadmap.md` and latest build snapshot)
- [ ] Confirm gate status: are Q-006 / Q-024 resolved if entering a gated stage?

---

## The Build Repo

The Faraz OS build work lives in a **separate build/code repository** — not this
architecture-memory repo. The build repo will be created at build-time.

**This architecture-memory repo** (`project-os-chatmemory`) remains pure
design canon after Phase 11. Its `./CLAUDE.md` governs AI collaboration here
and is never modified by build sessions.

**The build repo** will contain:
- All application code (API server, AI worker, migrations, CI/CD config)
- Build-session snapshots (what was built, stage-gate status, surprises)
- Its own CLAUDE.md — instantiated from the template in Appendix A at build-repo
  setup time, then maintained in the build repo

Build-session snapshots belong in the build repo. Architecture-design snapshots
(this repo) record design history and must not be mixed with build progress records.

---

## Agent Roles

Claude Code operates through **four role stances** within a single session.
These are not separate processes or separate Claude instances — they are
distinct operating modes that Claude adopts at the appropriate moment.
The model is **extensible**: if a build need calls for an additional role
(e.g. a Documentation Agent, a Migration Agent), it can be added to the team.
The four below are the baseline set for the Faraz OS MVP → V1 build.

### Architect Agent

**When active.** Before any build session begins; when a structural question
or unexpected boundary arises mid-build.

**Responsibilities.**
- Reads canon (Current-State.md, latest snapshot, and the relevant roadmap.md
  stage) before writing any plan.
- Enforces the Phase Boundary Rule: no architecture decisions are made in code;
  any question that touches architecture is surfaced and gated.
- Proposes the session plan (exact files in scope, what must not change,
  which gate must be resolved before starting) — Plan Mode output.
- Identifies if a pre-build gate (Q-006, Q-024, or other) is unresolved and
  halts if a gated domain is about to be written without gate resolution.

**Hard limits.**
- Never resolves a carried-open Phase-1 question in code.
- Never invents architecture beyond repository evidence.
- Never writes code — hands off to Builder Agent after plan approval.

### Builder Agent

**When active.** After the Architect Agent's plan has been reviewed and Ali
has given explicit go.

**Responsibilities.**
- Executes the approved plan. Minimal-diff edits — no speculative abstractions,
  no silent scope expansion beyond the approved plan.
- Applies bilingual / IR-sensitivity constraints as first-class requirements
  wherever Content or Publishing domain code is written
  (DEC-049; `roadmap.md:66–84`).
- Surfaces surprises immediately rather than resolving them independently.
  Any surprise that touches architecture or a gate → escalates to Architect Agent.

**Hard limits.**
- No architecture decisions.
- No features beyond the current approved block.
- No hardcoded credentials anywhere.

### QA Agent

**When active.** After each build block completes; at each stage gate.

**Responsibilities.**
- Writes integration tests against the stage-gate criteria defined in
  `roadmap.md` (e.g. Foundation stage gate: schema-per-client isolation proven,
  Cloud Run deployed, Firebase JWT → `search_path` routing verified;
  `roadmap.md:225`).
- Confirms schema-per-client isolation holds after any migration.
- Confirms auth middleware behavior (Firebase JWT claim → `search_path` set).
- Confirms zero hardcoded secrets in the diff (grep for known patterns).

**Hard limits.**
- Does not write application features.
- Does not redefine stage-gate criteria — those are set by `roadmap.md`.

### Review Agent

**When active.** Before every canon/posture commit; after every meaningful
build block.

**Responsibilities.**
- **Part A — Mechanical citation verifier (deterministic, shell-based).**
  For every file:line citation introduced or modified: run `sed` on the
  current working tree and confirm the claimed token is literally present.
  Run a stale-token sweep (grep for old line numbers in changed files).
  After any same-session canon landing, re-derive all draft citations from
  post-landing ground truth (FIND-032). Report raw `sed`/`grep` output —
  never a bare "verified" claim without the bytes.
- **Part B — Semantic red-team (judgment, against the repository).** Confirm:
  altitude is right; no carried-open item was silently touched; no architecture
  was invented beyond repository evidence; wording matches the ruling; no
  `./CLAUDE.md` was modified.

**Hard limits.**
- Not a replacement for Ali's meaning/posture judgment.
- Surfaces findings; Ali decides on any posture or meaning call.
- Immutable-history citations (snapshots, brainstorms, decisions.md historical
  entries) resolve against their landing commits and are never retro-edited.

### Extensibility Note

If a build need calls for an additional agent role — for example a Migration
Agent for schema-migration authoring and review, or a Documentation Agent
for API docs — add it to this team with the same structure: when active,
responsibilities, hard limits. The four above are not a closed set.

---

## Operating Modes

### Plan Mode

**Purpose.** Scope the session, compare options, identify exactly which files
are in scope, define the intended edits, and clarify risks — before any change
is made.

**Inputs.** Active roadmap stage and block; gate status (Q-006, Q-024,
or other gates); Current-State.md; latest build snapshot.

**Output.** A proposed session plan containing:
- Active stage and block (from `roadmap.md`)
- Exact file list: files in scope + files that must not change
- Gate status: any pre-build gate that must be resolved before this block
- Constraints active (bilingual, IR-sensitivity, schema-per-client,
  zero hardcoded secrets)
- Deferred items: what is explicitly out of scope this session
- Proposed edit summary (what changes, why, what the expected output is)

**Transition to Build Mode.** Ali's explicit go on the proposed plan.
No Build Mode action begins without this go.

### Build Mode

**Purpose.** Execute the approved plan. Minimal-diff edits. No creative
deviation from the approved plan.

**Constraints.**
- Follows the approved plan exactly.
- Any surprise (unexpected file state, an undiscovered dependency, a gate
  conflict) surfaces immediately — never resolved silently.
- Bilingual + IR-sensitivity constraints are checked before writing any
  Content or Publishing domain code.
- No hardcoded credentials; all secrets are read from Secret Manager.

**Transition to Review Mode.** After any meaningful build block completes —
a file is written, a migration is authored, a service config is set.

### Review Mode

**Purpose.** Audit the diff for correctness, canon alignment, and no
boundary violations before committing.

**Process.** The Review Agent runs the mandatory two-part self-review:
Part A (mechanical citation verifier — raw shell bytes) and Part B
(semantic red-team). Raw output is shown for every citation check.
A bare "looks right" is never acceptable.

**Outputs.**
- **CLEAR**: the diff is clean → commit.
- **Findings**: one or more issues → back to Build Mode with specific fixes,
  then back to Review Mode.

**Transition.** CLEAR → commit → push → raw-verify on main.
Findings → Build Mode → Review Mode again.

### Mode Transitions

| Trigger | From | To | Gate |
|---------|------|----|------|
| Session starts | — | Plan Mode | Read Current-State.md + latest build snapshot |
| Plan approved | Plan Mode | Build Mode | Ali's explicit go |
| Build block complete | Build Mode | Review Mode | Automatic |
| Review CLEAR | Review Mode | Commit + push | Raw output shown |
| Review finds issues | Review Mode | Build Mode | Fixes applied before re-review |
| Structural surprise surfaces | Build Mode | Plan Mode (Architect Agent) | Ali notified |
| Gate conflict found | Build Mode | Plan Mode (halt) | Gate must resolve before proceeding |

---

## Session Protocol

### Session Start Discipline

At the beginning of every build session:

1. Run the Pre-Session Checklist (§ Prerequisites, item 9).
2. Read `Current-State.md` (architecture-memory repo) for orientation.
3. Read the latest build-repo snapshot to confirm the active stage, last
   completed block, and any open surprises from prior sessions.
4. Confirm the active stage and block in `roadmap.md`.
5. Confirm gate status: if entering a gated stage, confirm the gate is resolved.
6. Enter Plan Mode. Produce the session plan before any code is written.

### Session Close-Out Discipline

At the end of every build session with meaningful progress:

1. **Build snapshot.** Write a build snapshot in the build repo using the
   format defined in Snapshot Discipline below. Record what was built,
   gate status, surprises, and next focus.
2. **Tracker backfill — same commit.** The build snapshot and any tracker
   updates land in the same commit as the work they record. Nothing is
   deferred to a later commit.
3. **Push + raw-verify.** Commit → push → confirm on `origin/main` of the
   build repo with raw `git log --oneline origin/main -3` output. Nothing
   is "done" until pushed and verified.
4. **Architecture-memory repo.** If a build session produces a finding that
   affects the architecture (a gate that was resolved, a boundary question
   answered, a risk materialized), bring it back to this architecture-memory
   repo as a new DEC or snapshot — via the normal GATED discipline.

### GATED vs AUTO in Build Sessions

**AUTO (lands without explicit go):**
- Record commits (build snapshot + tracker backfill)
- Reference-altitude knock-on refreshes (pointer updates after a resolved gate)
- Linear tracker mirroring after a verified push

**GATED (requires Ali's explicit go):**
- Any surprise that touches architecture, domain ownership, or a boundary
- Tech-selection changes beyond what Phase 9 / Phase 11 authorize
- Stage-gate criteria changes (only `roadmap.md` may redefine these)
- Any schema write for a domain whose gate (Q-006, Q-024, or other) is unresolved
- Any posture or meaning call

---

## Snapshot Discipline (Build Sessions)

Build snapshots live in the **build repo**, not this architecture-memory repo.
They record what was built, not what was designed.

### When to snapshot

- A stage gate passes
- A named block from `roadmap.md` completes
- A build-session surprise surfaces that may affect architecture
- Session close-out with meaningful progress

### Build snapshot fields

```
## Stage
[Active stage from roadmap.md, e.g. "MVP / Foundation"]

## Blocks Completed (This Session)
[Block names and short description of what was written]

## Stage-Gate Status
[Pass / Pending / Blocked — and which criterion is open]

## Surprises / Deferred Items
[Anything that surfaced unexpectedly; deferred to a future session]

## Architecture Flags
[Anything that must return to the architecture-memory repo as a DEC or finding]

## Next Focus
[The next block or gate to address]
```

Build snapshots are immutable history — never retro-edited after commit,
consistent with the architecture-memory repo snapshot discipline.

---

## Prompt Handoff Format

A cold-start session must be oriented without re-reading all 10 architecture
phases. Use this format at the start of every new Claude Code session
(or when handing off between sessions).

```
## Faraz OS — Build Session Handoff

### Current Stage + Block
[e.g. "MVP / Foundation — Block 3: Cloud Run deployment"]

### Architecture Memory
- Repo: project-os-chatmemory (architecture canon)
- Current-State.md: current orientation pointer
- Latest architecture snapshot: [Snapshot number + title]
- Latest build snapshot: [Build snapshot reference in build repo]

### Active Plan
[The approved session plan produced in Plan Mode this session]

### Files in Scope
[Exact list of files to be written or edited]

### Files That Must Not Change
[Explicit list — e.g. architecture-memory repo files; CLAUDE.md]

### Gate Status
- Q-006 (Service Agreement aggregate boundary): [Resolved / Open]
- Q-024 (Ticket ↔ Escalation Case): [Resolved / Open]
- [Other gates if applicable]

### Constraints Active
- Schema-per-client isolation: enforced from Block 2 (Foundation)
- Firebase JWT → search_path routing: enforced from Block 7 (Core Layer)
- Bilingual / IR-sensitivity: enforced from first T1 domain schema write
- Zero hardcoded secrets: enforced everywhere, always

### Deferred Items (Out of Scope This Session)
[Explicit list]

### Pre-Session Checklist Status
- [ ] gcloud auth: confirmed
- [ ] GCP project: confirmed
- [ ] Secret Manager secrets populated for this stage: confirmed
- [ ] Clean branch: confirmed
```

---

## Development Rules

These rules apply in every build session, in every block, at every stage.

1. **Prefer editing existing files over creating new ones.** New files are
   justified only when a block explicitly calls for them.

2. **No speculative abstractions.** Do not introduce interfaces, base classes,
   or patterns beyond what the current block requires. Abstractions are added
   when a second concrete use case exists, not in anticipation of one.

3. **No hardcoded credentials anywhere.** No secret, password, API key, or
   connection string in code, config, Docker image, or committed env file.
   All secrets are read from GCP Secret Manager at runtime.

4. **Schema writes are gated.** Do not write a domain schema for CRM until
   Q-006 is resolved. Do not write a domain schema for Client Success until
   Q-024 is resolved. Do not write a schema for any T3 entity (Campaign,
   Ad-Account, Schedule, Consent) until its own Phase-1 gate is resolved.

5. **Test against stage-gate criteria.** The integration test suite for each
   stage proves the stage-gate criterion passes, not just that unit tests
   are green. Stage-gate criteria are defined in `roadmap.md`.

6. **Bilingual + IR-sensitivity are first-class.** From the first T1 domain
   schema write: Content domain schema carries a `language` field; PromptTemplate
   supports Farsi; Publishing pipeline handles RTL and Unicode normalization;
   Dual-Path / Manual Fallback (DEC-037) is wired at MVP (T1-critical).

7. **Surface surprises immediately.** Any unexpected file state, undiscovered
   dependency, or boundary question surfaces immediately in the session.
   Do not resolve silently in code.

8. **Nothing is done until pushed and verified.** "I wrote the file" is not
   done. Done = committed + pushed + raw `git log --oneline origin/main -3`
   output confirms the commit is on main.

9. **Report raw output.** For every verification step, show the raw command
   output. Never claim "verified" or "confirmed" without showing the bytes.

---

## Coding Standards Framework

Phase 11 defines the **framework** for coding standards — what categories of
standards apply and how they are documented. The concrete pins (specific language
versions, linter configs, import conventions, style rules) are defined in the
**build-repo CLAUDE.md** at build-repo setup time, once technology choices
from Phase 9 are confirmed and any remaining selections are made.

This separation is deliberate: Phase 9 (`infrastructure.md`) deferred some
technology selections to the build layer (DEC-049). Pinning concrete syntax
rules before those selections are confirmed would create rework.

**Standards that apply regardless of technology choice:**

| Category | Rule |
|----------|------|
| Secrets | Zero hardcoded secrets; all secrets via Secret Manager |
| Configuration | All environment config via Secret Manager or build-level config vars; no committed `.env` files with real values |
| Migrations | Schema migrations versioned, reviewed, and applied via the migration runner before execution; never run ad-hoc |
| Error handling | Errors surface clearly; never silently swallowed; structured error objects with context |
| Observability | OpenTelemetry SDK instrumentation from the first Cloud Run deployment (Block 8, Foundation stage) |
| Testing | Integration tests preferred over unit tests for schema + auth middleware; tests run against a real database, not mocks, for schema verification |
| Bilingual | Language field first-class in Content domain schema; RTL and Unicode handling in Publishing pipeline; Farsi PromptTemplate support |

**Standards deferred to build-repo CLAUDE.md:**
- Language and runtime version pins
- Linter and formatter configuration
- Import ordering conventions
- Naming conventions (variable, function, module)
- Framework-specific patterns (ORM conventions, router structure, etc.)
- Test runner configuration

At build-repo setup: the first act is to instantiate Appendix A (BUILD-TIME
CLAUDE.md TEMPLATE) in the build repo and complete the deferred standards
section based on confirmed Phase 9 technology selections.

---

## Non-Goals

Phase 11 does not:

- Re-architect or redefine what blocks, layers, or domains ARE (Phases 1–8)
- Re-assign technology to abstract blocks (Phase 9)
- Resolve carried-open Phase-1 questions (Q-003, Q-006, Q-007, Q-024)
  or any entity reopenings (Campaign, Ad-Account, Schedule, Consent)
- Write application code (that is the build repo's job)
- Define the content of any domain schema (that is the build repo's job, gated
  on Phase-1 decisions)
- Edit `./CLAUDE.md` in this architecture-memory repo
- Create any new CLAUDE.md file in this architecture-memory repo

---

## Cross-Phase References

| Phase / File | Relevance to Phase 11 |
|-------------|----------------------|
| `roadmap.md` (Phase 10) | Stages, blocks, stage-gate criteria, pre-build gates A+B, IAM grant matrix, secret naming context |
| `infrastructure.md` (Phase 9) | Technology selections; Block 5 Secret Store discipline; Block 3 Cloud Run topology |
| `domains.md` (Phase 1) | Domain truth; schema-write gate awareness |
| `Current-State.md` | Live orientation pointer for every session start |
| `./CLAUDE.md` | Architecture operating contract for this repo; governs AI collaboration here; not touched by Phase 11 |
| `decisions.md` | DEC-049 (Phase 10 scope), DEC-050 (Phase 11 scope) |

---

## Appendix A — Build-Time CLAUDE.md Template

This template is instantiated in the build repo at build-repo setup time.
It is a **spec** — shown here as reference. No CLAUDE.md is created in this
architecture-memory repo.

```
# CLAUDE.md — Faraz OS Build Repo

## Purpose
This file governs Claude Code execution in the Faraz OS build repo.
It is the build-time operating contract — distinct from the architecture-memory
repo's CLAUDE.md, which governs design collaboration.

## Architecture Memory
- Architecture-memory repo: project-os-chatmemory
- Current-State.md: the live orientation pointer for every session start
- Phase 11 operating system: Faraz-OS-Canon/claude-operating-system.md
  (full detail for all rules below)

## Active Stage
[Fill in at build-repo setup: e.g. "MVP / Foundation"]

## Agent Roles (Operating Stances)
Four baseline stances within a single Claude Code session:
- Architect Agent: scoping, plan, gate enforcement — Plan Mode
- Builder Agent: code execution per approved plan — Build Mode
- QA Agent: integration tests, stage-gate verification — after each block
- Review Agent: Part A citation verifier + Part B semantic red-team — before every commit
Extensible: add agent roles as build needs require.

## Operating Modes
- Plan Mode: scope + plan + gate check → output: session plan → Ali's go required
- Build Mode: execute approved plan, minimal-diff, surface surprises immediately
- Review Mode: Part A (shell sed/grep raw bytes) + Part B (semantic red-team) →
  CLEAR → commit; findings → back to Build Mode

## GATED vs AUTO
AUTO: record commits, tracker backfill, reference knock-ons
GATED (Ali's explicit go): architecture-touching surprises, tech-selection changes,
stage-gate criteria changes, gated domain schema writes (Q-006, Q-024, others)

## Provisioning
See Faraz-OS-Canon/claude-operating-system.md § Prerequisites for full checklist.
Secret naming: faraz-os-{env}-{block}-{type}
No secret ever in code, config, chat, or committed env file.

## Development Rules
1. Prefer editing existing files over creating new ones
2. No speculative abstractions
3. No hardcoded credentials — all via Secret Manager
4. Schema writes gated (Q-006 before CRM schema; Q-024 before Client Success schema)
5. Test against stage-gate criteria (roadmap.md), not just unit coverage
6. Bilingual + IR-sensitivity first-class from first T1 schema write
7. Surface surprises immediately; never resolve silently
8. Nothing done until pushed + verified; always report raw output

## Coding Standards
Technology pins (language version, linter, formatter, naming conventions):
[Complete at build-repo setup — see claude-operating-system.md § Coding Standards Framework]

Standards that apply always (regardless of technology):
- Zero hardcoded secrets
- All env config via Secret Manager or build-level config vars
- Schema migrations versioned and reviewed before execution
- Errors surfaced clearly; never swallowed
- OpenTelemetry instrumentation from first Cloud Run deployment
- Integration tests preferred for schema + auth middleware

## Self-Review Requirement (MANDATORY before every commit)
Part A — Mechanical citation verifier:
  For every file:line citation introduced or modified:
  1. sed the exact range in the current working tree; confirm the token is there
  2. Stale-token sweep: grep changed files for old line-number tokens
  3. Same-session shift rule: re-derive LIVING-doc citations after any same-session landing
  4. Report raw sed/grep output for each citation — never a bare "verified" claim

Part B — Semantic red-team:
  - Wording matches the ruling; altitude is right
  - No carried-open item silently touched
  - No architecture invented beyond repository evidence
  - No boundary violated

## Session Close-Out
Same-commit discipline:
  build snapshot + tracker backfill in the same commit as the work they record.
Nothing "done" until: committed → pushed → git log --oneline origin/main shows
the commit → raw output reported.

## Build Snapshots
Format (in this build repo, not architecture-memory repo):
  Stage / Blocks Completed / Stage-Gate Status / Surprises-Deferred /
  Architecture Flags / Next Focus
Immutable after commit — never retro-edited.

## What Must Not Change
- Architecture-memory repo files (read-only reference from build sessions)
- project-os-chatmemory/CLAUDE.md (architecture operating contract; never touched)
- Stage-gate criteria in roadmap.md (fixed; changes require Ali's explicit go)
- Phase-1 domain truth in domains.md (fixed; changes require Phase-1 DEC gate)
```
