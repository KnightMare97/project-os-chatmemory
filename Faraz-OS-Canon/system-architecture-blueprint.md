# System Architecture Blueprint — Phase 7

## Purpose
`system-architecture-blueprint.md` defines the **logical system architecture** of
Faraz OS as **seven cross-cutting concern-views** (Logical, Application, Data, AI,
Integration, Security, Runtime Architecture) over the platform: it names **how** the
system runs, stores, secures, integrates, and executes AI.

It **references — never re-decides** — what things are and who owns them: domain
truth and authorization (Phase 1), surfaces and the Permission Matrix (Phase 2),
capabilities (Phase 3), provider / channel / model selection and the Feature-Module
contract (Phase 4), and workflow sequences / runtime semantics (Phase 6). It is a
**concern-view** blueprint, not the layered assembly (that is Phase 8, DEC-030).

It records each concern-view on a fixed six-field skeleton.

---

## Altitude
Phase 7 sits at **system-architecture altitude** (DEC-031 G-1): it architects the
*how* — execution, storage, security, integration, AI — at logical altitude, naming
no implementation technology. This is the **R-028 inversion** from the earlier
phases: through Phase 6 the risk was engine/mechanism talk bleeding *into* logical
phases; here it flips — the risk is Phase 7 **re-deciding** domain / capability /
workflow / experience truth instead of **referencing** it. The governing
inversion-guard litmus is applied to every view (referenced below, not restated).

Faraz OS is **single-tenant**: no multi-tenant isolation layer is architected
(DEC-031 G-5).

---

## Status
Phase 7 scope is defined and human-confirmed (**DEC-031 / Snapshot-042**). The
Phase 7 ↔ Phase 8 boundary is drawn (**DEC-030**); Q-013 is resolved
(architecture-home → Phase 7 AI Architecture; surface rendering → Phase 2). The
Application / Logical view prerequisite — a firm Phase-4 Feature-Module contract — is
satisfied (**DEC-032**; `Faraz-OS-Canon/extensibility.md:426`).

This file is written in batches, dependencies-first (FIND-033), so no view's
references ever point at unwritten content. **This is Batch A — the file skeleton and
framing only; no concern-view content yet.** The seven views land in subsequent gated
batches (Logical + AI Architecture; Application + Data; Integration + Security;
Runtime + closing).

No Phase 1 domain truth, ownership, or boundary is changed by this file. Phase 7
references Phase 1; it does not reinterpret it. It resolves no inherited Phase-1
question (R-027).

---

## Governing rules (referenced, not restated here)
This file **applies** the rules fixed by **DEC-031 / DEC-030 / DEC-028**; it does not
restate them. Three governing rules bind every concern-view; each is recorded verbatim
at its cited home and applied here:

- **Inversion-guard litmus** — DEC-031 G-1 (`decisions.md:1578-1582`): the per-view
  test separating the *how* (Phase 7 architects it) from the *what* (Phases 1/2/3/6
  own it, referenced). Recorded verbatim there; applied to every view. If a view
  cannot be written without re-defining owned truth, the litmus has fired — escalate,
  do not write around it.
- **P7 ↔ P8 boundary** — DEC-030: Phase 7 is the **concern-views**; Phase 8 Puzzle
  Board is the **layered assembly**. This file authors no Phase-8 layer content.
- **P6 ↔ P7 runtime litmus** — `Faraz-OS-Canon/workflows.md:167-171` (DEC-028
  `decisions.md:1348-1353`): the engine-vs-semantics test (workflow semantics are
  Phase 6; the executing engine is Phase 7 Runtime Architecture). Recorded verbatim at
  its home; carried verbatim into the Runtime Architecture view when that batch lands.

The closed boundary set (G-2), the non-goals (G-5), and the carried set (G-7) are
fixed in DEC-031; the non-goals and carried flags are written into this file in the
closing batch.

---

## AI-native, not AI-only
**AI Architecture is the spine** of the seven views (Faraz OS is AI-native), but
AI-native is **never AI-only** (DEC-031 G-3). Every view honors **Core Principle #1**
(`Faraz-OS-Canon/principles.md:3`, "AI-first, but not AI-only") and the
human-in-the-loop mode vocabulary
(`Faraz-OS-Canon/human-in-the-loop-philosophy.md:18-22`): AI is the default executor,
with human and hybrid paths first-class, not an afterthought.

---

## How to read this file — the six-field per-view skeleton
Each of the seven concern-views is recorded on a fixed six-field skeleton
(DEC-031 G-4):

1. **Definition / concern** — what the view covers.
2. **What it architects (the *how*)** — the architectural answer to the concern.
3. **Referenced owned-truth (the *what*, by phase)** — an explicit reference list of
   the domain / surface / capability / workflow truth the view depends on, by owning
   phase; referenced, never re-decided.
4. **Key decisions / mechanisms at logical altitude** — the architectural decisions,
   stated at altitude with no named technology.
5. **Cross-phase boundary notes** — how the G-1 inversion litmus holds at each seam.
6. **Open / deferred items** — anything flagged, carried, or left to a later pass.

---

## The seven concern-views
The views below are written across the gated batches (`Faraz-OS-Canon.md:132-138`);
each follows the six-field skeleton above and is bound by the three governing rules:

- Logical Architecture
- Application Architecture
- Data Architecture
- AI Architecture *(the spine; agent / subagent identity is defined here, DEC-031 G-6(a))*
- Integration Architecture
- Security Architecture
- Runtime Architecture

---

## Logical Architecture
- **Definition / concern.** The overall logical shape of the Faraz OS platform: the
  configurable core, the mountable Feature-Modules that compose onto it, and the domains
  rendered as logical components with their relationships. It answers, at architecture
  altitude, *what the system's logical building blocks are and how they relate.*
- **What it architects (the *how*).** A **base-plus-modules** shape: a configurable core
  onto which Feature-Modules mount (the module-mounting thesis — base and modules both
  extensible and updatable). Domains appear as logical components bounded by their Phase-1
  meaning, wired by their relationships; capabilities and plugins attach through the
  Phase-4 contract surface. Described at altitude — no named framework, runtime, or
  topology.
- **Referenced owned-truth (the *what*, by phase).**
  - Phase 1 — the domain set (`Faraz-OS-Canon/domains.md`): each domain is a logical
    component here, referenced by its owned meaning, never re-defined.
  - Phase 3 — capabilities (`Faraz-OS-Canon/capabilities.md`): the reusable abilities the
    components expose; invoked, not defined.
  - Phase 4 — the Feature-Module contract (`Faraz-OS-Canon/extensibility.md:426`), the
    Plugin Model (`:273`), and Extension Contracts (`:196`): the mount / attachment
    contracts the shape composes; referenced, never re-defined.
- **Key decisions / mechanisms at logical altitude.**
  - Base + mountable modules is the platform's organizing shape; modules mount through the
    Phase-4 Feature-Module contract, and the core depends on no specific module.
  - Domains-as-components: each Phase-1 domain is one logical component; cross-domain
    relationships are wiring at altitude, not new domain truth.
  - Single-tenant: a single platform instance; no multi-tenant isolation layer
    (DEC-031 G-5). No named technology.
- **Cross-phase boundary notes (G-1 litmus).**
  - ↔ Phase 1: components *reference* domain meaning; this view re-owns no entity,
    ownership, or boundary.
  - ↔ Phase 4: the shape *mounts* the Feature-Module / plugin contract; it does not
    re-define what a module or plugin is (`Faraz-OS-Canon/extensibility.md:426`, `:273`).
  - ↔ Phase 8: the *assembled* layered board — which components / modules are assembled
    where — is Phase 8 (DEC-030); this view is the concern-view shape, not the assembly.
- **Open / deferred items.** None new. Resolves no inherited Phase-1 question (R-027).

---

## Application Architecture
- **Definition / concern.** How the system is structured as runnable applications: the
  persona portals, the base-plus-mountable-modules platform that hosts them, and the
  services structure — answering, at architecture altitude, *what application structures
  run and how they compose.*
- **What it architects (the *how*).** A base-plus-modules application shape (the runnable
  projection of the Logical view): a configurable core hosts the persona portals (the
  Phase-2 surfaces, run here — not authored here) and **mounts Feature-Modules** through
  the Phase-4 contract; agent / subagent execution inside an application references the AI
  Architecture (the spine). Described at altitude — no named framework, runtime, or
  deployment topology.
- **Referenced owned-truth (the *what*, by phase).**
  - Phase 2 — the portals / Operating Surfaces and the Permission Matrix
    (`Faraz-OS-Canon/experience-architecture.md:280` Portals, `:151` Operating Surfaces):
    the application *runs* what Phase 2 defines; it authors no surface.
  - Phase 4 — the Feature-Module contract (`Faraz-OS-Canon/extensibility.md:426`): the
    module-mount the application composes.
  - Phase 7 Logical Architecture (this file) — the base+modules shape this view projects
    into runnable applications.
  - Phase 7 AI Architecture (this file) — agent / subagent execution within applications.
- **Key decisions / mechanisms at logical altitude.**
  - The configurable core hosts persona portals and mounts Feature-Modules (the
    module-mount platform — the base-product thesis made runnable).
  - Services structure: the application composes capabilities and modules into the
    surfaces personas use; it *runs* them, it does not define them.
  - Single-tenant: one application instance for the platform operator (DEC-031 G-5). No
    named technology.
- **Cross-phase boundary notes (G-1 litmus).**
  - ↔ Phase 2: hosts / runs the portals; authors no surface, view, or permission rule.
  - ↔ Phase 4: mounts the Feature-Module contract; does not re-define it
    (`Faraz-OS-Canon/extensibility.md:426`).
  - ↔ Phase 7 Logical / AI (this file): projects the Logical shape into runnable
    applications; defers agent execution to AI Architecture.
- **Open / deferred items.** None new. Resolves no inherited Phase-1 question (R-027).

---

## Data Architecture
- **Definition / concern.** How data persists and stays consistent: where each domain's
  truth lives, the asset / media persistence model, per-client data scoping, ingest /
  upload data paths, and retention enforcement — answering *how / where data is stored and
  kept consistent*, referencing (never re-owning) what the data **is**.
- **What it architects (the *how*).** A persistence-and-consistency model over the
  Phase-1 domains: each domain's truth persists in its owning store (referenced, not
  re-owned); the **Client Asset** (owned by the new **Media & Assets** domain, DEC-033)
  gets an asset / media persistence model across its raw / uploaded / AI-generated /
  produced states; cross-domain consistency keeps referencing-domains in sync without
  re-owning them. **Per-client data scoping** logically separates one client's data from
  another. **Ingest / upload data paths** carry assets in — including the **manual-upload
  hook** for the dual-path posture (the automated path and its human / manual fallback
  both persist data here). **Retention enforcement** acts on the asset's retention-status
  per the Governance retention policy. Described at altitude — no named storage / database
  / cloud technology.
- **Referenced owned-truth (the *what*, by phase).**
  - Phase 1 domains (`Faraz-OS-Canon/domains.md`) — each domain owns its entity truth;
    Data persists / serves it, never re-owns.
  - Phase 1 **Media & Assets** (DEC-033; `Faraz-OS-Canon/domains.md:3738`) — the Client
    Asset entity + rights / provenance / retention-status; the asset persistence model
    references this owner.
  - Phase 1 Engagement Scope — `relevant_assets_refs` (`Faraz-OS-Canon/domains.md:517`) is
    the reference Data resolves to the asset store.
  - Phase 1 Governance — the retention *policy*; Data *enforces*, does not author it.
  - Phase 5 (`Faraz-OS-Canon/memory.md`) — memory / knowledge structure; Data persists it,
    does not define it.
- **Key decisions / mechanisms at logical altitude.**
  - **Per-client logical data scoping is distinct from single-tenant** (DEC-031 G-5):
    single-tenant = one platform operator (no multi-tenant isolation layer); per-client
    scoping = data organization *within* that one operator (one client's media not mixed
    with another's).
  - Asset / media persistence model for the Client Asset (Media & Assets, DEC-033) across
    all media states.
  - Ingest / upload data paths including the dual-path **manual-upload hook** (automated +
    human/manual fallback both persist here; the dual-path *posture* is referenced, not
    decided here).
  - Retention enforcement on the asset retention-status per the Governance policy.
  - Cross-domain data consistency without re-owning domain truth. No named storage / cloud
    technology (Phase-10).
- **Cross-phase boundary notes (G-1 litmus).**
  - ↔ Phase 1 domains: persists / serves domain truth; re-owns no entity — including the
    Client Asset (owned by Media & Assets, DEC-033).
  - ↔ Phase 1 Governance: enforces the retention policy; authors none.
  - ↔ Phase 5: persists memory / knowledge structure; defines none
    (`Faraz-OS-Canon/memory.md`).
  - ↔ Phase 2: per-client scoping serves the surfaces; authors no surface.
  - ↔ Phase 8: the *assembled* data layer is Phase 8 (DEC-030); this view is the data
    concern-view.
- **Open / deferred items.** The dual-path manual-upload *posture* and the retention
  *window* (the 29-day default, non-canon grounding) are referenced — their policy is the
  dual-path principle / Phase-1 Governance / Phase-10, not decided here. Asset Intelligence
  (Phase 5) deferred. Resolves no inherited Phase-1 question (R-027).

---

## AI Architecture
- **Definition / concern.** The **spine** of the blueprint (Faraz OS is AI-native): how
  the system *executes AI* — the model-invocation / routing execution, agent and subagent
  execution and **identity**, and the human / hybrid execution paths. AI-native, **never
  AI-only**.
- **What it architects (the *how*).** A **chain-modelling / routing** execution
  architecture: the system invokes models and composes agent / subagent execution into
  chains, selecting per part by policy. **Agent / subagent identity is defined here**
  (Q-013; DEC-031 G-6(a)): what an agent / subagent *is* architecturally — a defined
  executing entity with a lifecycle-as-architecture (instantiated, executes, hands off,
  retires) — distinct from the *role* it plays in a Phase-6 sequence. AI is the default
  executor; human and hybrid paths are first-class. The engine is described at altitude —
  no named runtime, framework, model, or vendor.
- **Referenced owned-truth (the *what*, by phase).**
  - Phase 3 — capabilities (`Faraz-OS-Canon/capabilities.md:85-88`): the abilities AI and
    agents execute; invoked, not defined.
  - Phase 4 — the Model abstraction (`Faraz-OS-Canon/extensibility.md:308`) and AI Model
    Routing (`:351`): the swappable-model unit and the policy-driven selection layer. This
    view *executes* the routing engine but authors no selection policy — Phase 4 owns it
    (`:390-391`). The agent / subagent-identity flag is scoped here (`:345-347`).
  - Phase 2 — agent-facing **surface rendering** stays Phase 2 (the Q-013 split,
    DEC-031 G-6(b)).
  - Core Principle #1 (`Faraz-OS-Canon/principles.md:3`) and the HITL mode vocabulary
    (`Faraz-OS-Canon/human-in-the-loop-philosophy.md:18-22`).
- **Key decisions / mechanisms at logical altitude.**
  - Chain-modelling execution: agent / subagent steps compose into chains; per-part
    model / agent selection is enforced by *invoking* the Phase-4 routing policy, not
    re-deciding it.
  - Agent / subagent identity model: a defined executing entity (identity,
    lifecycle-as-architecture, and the AI architecture that executes it) — the Phase-7
    side of the role-vs-identity litmus.
  - Human / hybrid execution paths are first-class alternatives to AI-default execution
    (HITL), never an afterthought. No named model, runtime, or vendor; selection *policy*
    is referenced (Phase 4), not authored.
- **Cross-phase boundary notes (G-1 litmus).**
  - ↔ Phase 3: executes capabilities; defines none (`Faraz-OS-Canon/capabilities.md:85-88`).
  - ↔ Phase 4: executes the routing / selection *engine*; Phase 4 owns the routing /
    selection *policy* and the Model / Provider contracts
    (`Faraz-OS-Canon/extensibility.md:351`, `:390-391`).
  - ↔ Phase 2: defines agent / subagent *identity and executing architecture*; agent-facing
    *surface rendering* is Phase 2 (the Q-013 split, DEC-031 G-6(b)).
  - ↔ Phase 6: **role vs identity.** Phase 6 names where an agent-performed step sits in a
    sequence (its *role*); Phase 7 defines what the agent *is*. Role-vs-identity litmus
    (`Faraz-OS-Canon/workflows.md:129-133`; DEC-028 `decisions.md:1325-1332`), Phase-7
    clause verbatim: *"Defines what the agent is (identity, surface, executing AI
    architecture) → Phase 7."*
- **Open / deferred items.** Q-017 (system-administrator visual workflow management) notes
  a candidate Phase-7 home but is its own gated, multi-phase decision — carried, not
  resolved here. Resolves no inherited Phase-1 question (R-027).

---

## Integration Architecture
- **Definition / concern.** How the system integrates with external providers, channels,
  and APIs: outbound dispatch (publish / upload to platforms), provider / channel / model
  invocation, and inbound ingest — answering *how the system reaches and is reached by the
  outside world*, referencing (never re-deciding) the bindings.
- **What it architects (the *how*).** An integration architecture over the Phase-4
  bindings: the system invokes external providers / channels / models through their
  Phase-4 contracts. Integration carries the **dual-path posture** — an automated API path
  and a manual / human path with automatic fallback when the automated one is unavailable
  (the Iran platform-access reality). Inbound ingest paths bring external uploads / signals
  in (the data lands via the Data view). Described at altitude — no named APIs, SDKs, or
  platform endpoints.
- **Referenced owned-truth (the *what*, by phase).**
  - Phase 4 — Provider Model (`Faraz-OS-Canon/extensibility.md:84`), Channel Model
    (`:120`), Model (`:308`), AI Model Routing (`:351`): the bindings and the selection
    policy. Selection / binding *policy* is Phase 4; the *integration architecture that
    executes against them* is Phase 7 (`Faraz-OS-Canon/extensibility.md:391-392`).
  - Phase 7 Data Architecture (this file) — inbound ingest / upload persists via Data;
    Integration carries it in.
  - Phase 7 Runtime Architecture (this file, pending) — async / long-running external
    calls, retries, and rate-limit handling are Runtime; Integration is the connection
    shape.
- **Key decisions / mechanisms at logical altitude.**
  - External dispatch (publish / upload) goes through the Phase-4 channel / provider
    contract; Integration architects *how it connects*, not which provider (Phase 4
    selects).
  - **Dual-path integration posture:** every external action has an automated path and a
    manual / human fallback, auto-engaged on unavailability (referenced principle, not
    authored here as policy).
  - Inbound ingest: external uploads / signals enter through defined ingest paths; the
    data lands via Data Architecture. No named API / SDK / endpoint (Phase-10).
- **Cross-phase boundary notes (G-1 litmus).**
  - ↔ Phase 4: invokes provider / channel / model bindings; defines neither them nor
    their selection policy (`Faraz-OS-Canon/extensibility.md:391-392`).
  - ↔ Phase 7 Data (this file): ingest carries data in; Data persists it.
  - ↔ Phase 7 Runtime (this file): retries / rate-limits / async execution are Runtime;
    Integration is the connection shape.
  - ↔ Phase 8: the *assembled* integration / plugins layer is Phase 8 (DEC-030).
- **Open / deferred items.** The dual-path posture and inbound community / engagement
  ingest (a candidate future domain / flow per the non-canon gap analysis) are referenced,
  not decided here. Resolves no inherited Phase-1 question (R-027).

---

## Security Architecture
- **Definition / concern.** How the system secures access and data: enforcement of
  authorization and the Permission Matrix, per-client data isolation, credential / secret
  handling, and protection of sensitive data — answering *how access and data are secured*,
  referencing (never re-authoring) the rules.
- **What it architects (the *how*).** A security architecture that **enforces** what other
  phases author: it enforces the Phase-1 Governance authorization rules and the Phase-2
  Permission Matrix at the application and data boundaries; it architects **per-client data
  isolation enforcement** (the Data view's per-client scoping, made an access boundary);
  and it architects credential / OAuth / secret handling *as architecture* (how credentials
  are scoped, held, rotated, and re-authed) — not implementation. Described at altitude — no
  named cryptography, key store, or auth product.
- **Referenced owned-truth (the *what*, by phase).**
  - Phase 1 Governance — authorization rules (DEC-026, `decisions.md:972`; Governance
    domain `Faraz-OS-Canon/domains.md:2155`): Security *enforces*, authors none.
  - Phase 2 — the Permission Matrix (`Faraz-OS-Canon/experience-architecture.md:502`):
    Security enforces the exposure it defines.
  - Phase 7 Data Architecture (this file) — data sensitivity and per-client scoping:
    Security enforces isolation over it.
- **Key decisions / mechanisms at logical altitude.**
  - Authorization enforcement: the Phase-2 Permission Matrix and the Phase-1 Governance
    rules (DEC-026) are enforced at the application and data boundaries; Security adds no
    rule.
  - **Per-client isolation enforcement:** the Data view's per-client logical scoping is
    enforced as an access boundary (one client's data unreachable from another's context),
    within single-tenant (DEC-031 G-5).
  - Credential / OAuth / secret handling as architecture: how credentials are scoped, held,
    rotated, and re-authed (including the dual-path manual re-auth) — not the crypto /
    implementation (Phase-10).
- **Cross-phase boundary notes (G-1 litmus).**
  - ↔ Phase 1 Governance: enforces authorization (DEC-026); authors no rule.
  - ↔ Phase 2: enforces the Permission Matrix (`Faraz-OS-Canon/experience-architecture.md:502`);
    authors no surface or rule.
  - ↔ Phase 7 Data (this file): enforces isolation over per-client-scoped and sensitive
    data.
  - ↔ Phase 8: the *assembled* security layer is Phase 8 (DEC-030).
- **Open / deferred items.** AI-monitoring privacy and prompt-injection defense (per the
  non-canon gap analysis) are referenced as future-gated, not authored here. Resolves no
  inherited Phase-1 question (R-027).

---

## Runtime Architecture
- **Definition / concern.** How workflows and jobs actually execute: the **engine** that
  runs them — scheduling, queues, the process model, execution-state persistence,
  async / long-running jobs, retry / recovery, and the deployment runtime. The
  highest-firewall view: it owns the *engine*, never the workflow *meaning*.
- **What it architects (the *how*).** A runtime / execution engine over the Phase-6
  workflows and the AI Architecture's agent chains: schedulers and queues that run and
  order jobs; the process model and execution-state persistence; async / long-running
  content and AI job execution; retry / backoff and failure recovery; the deployment
  runtime (single instance, single-tenant). It carries the dual-path / degraded-mode
  posture at runtime — the manual fallback path is independently runnable. Described at
  altitude — the *concept* of scheduler / queue / process-model, with **no named
  scheduler, queue, runtime, or cloud** (Phase-10).
- **Referenced owned-truth (the *what*, by phase).**
  - Phase 6 — workflow-runtime *semantics* (`Faraz-OS-Canon/workflows.md:167-171`): what a
    workflow *means* while running (lifecycle states, suspend / resume at gates,
    loop / exception semantics) is Phase 6; Runtime executes it. Retry / recovery is
    explicitly Phase-7 Runtime per Phase 6 (`Faraz-OS-Canon/workflows.md:233-236`).
  - Phase 7 AI Architecture (this file) — agent / subagent execution; Runtime schedules
    and runs the AI jobs the AI view defines.
  - Phase 7 Data Architecture (this file) — Runtime persists *execution state*,
    referencing where data lives (Data owns the persistence model).
  - Phase 4 — the Runtime-vs-Config-Time binding attribute
    (`Faraz-OS-Canon/extensibility.md:399`): which bindings are runtime vs config-time is
    the Phase-4 attribute; Runtime executes accordingly.
  - Phase 3 / Q-015 — cross-item publishing queueing is Phase-6 orchestration and the
    scheduled-publish when-parameter is Phase-3; the *queue engine* that runs them is here.
- **Key decisions / mechanisms at logical altitude.**
  - The execution engine: schedulers, queues, process model, execution-state persistence —
    runs Phase-6 workflows and AI-Architecture agent chains.
  - Async / long-running jobs: content and AI jobs that do not complete synchronously;
    failure → retry / backoff / recovery (the *mechanism* behind the Phase-6
    Failure / Exception pattern).
  - Deployment runtime: a single instance for the single tenant (DEC-031 G-5); no
    multi-tenant isolation.
  - Dual-path / degraded-mode at runtime: the manual fallback is independently runnable
    (the agency runs by hand if the engine is down) — referenced posture.
  - Idempotency / duplicate-post prevention and rate-limit / quota handling are runtime
    mechanisms architected here at altitude. No named technology (Phase-10).
- **Cross-phase boundary notes (G-1 litmus). P6↔P7 litmus carried verbatim**
  (`Faraz-OS-Canon/workflows.md:167-171`; DEC-028 `decisions.md:1348-1353`): *"Defines what
  a workflow means while running — its logical lifecycle states, what suspends/resumes at
  a gate, how a loop/exception behaves semantically → Phase 6 Workflow Runtime. Defines the
  engine that executes workflows — schedulers, queues, process model, state persistence,
  deployment runtime → Phase 7 Runtime Architecture."*
  - ↔ Phase 6: owns the engine; Phase 6 owns the semantics; never re-defines what a
    workflow means.
  - ↔ Phase 7 AI (this file): runs the AI jobs / agent chains the AI view defines.
  - ↔ Phase 7 Data (this file): persists execution state; the data persistence model is
    Data's.
  - ↔ Phase 4: honors the Runtime-vs-Config-Time binding attribute
    (`Faraz-OS-Canon/extensibility.md:399`).
  - ↔ Phase 8 / Phase 9: the *assembled* runtime layer is Phase 8 and the physical
    infrastructure is Phase 9; this view is the runtime concern-view.
- **Open / deferred items.** Concrete engine technology (scheduler / queue / process /
  deployment) is Phase-10. Resolves no inherited Phase-1 question (R-027).

---

## Non-goals
Per DEC-031 G-5, this file authors no:
- named technology / vendor / language / cloud (deferred to the Build / Phase-10 handoff —
  this preserves the generalizable-pattern value);
- implementation code;
- re-decided Phase-1 domain truth or authorization, Phase-3 capability definitions, or
  Phase-6 workflow sequences / semantics;
- Phase-8 layered-assembly content.

Single-tenant constraint (DEC-031 G-5): Faraz OS is single-tenant — no multi-tenant
isolation layer is architected.

---

## Open and deferred items
Referenced by the views, owned elsewhere, not authored here:
- The **dual-path / manual-fallback** posture (publish / upload / payment / OAuth re-auth) —
  a cross-cutting principle referenced across Integration / Data / Runtime; its decision is
  the dual-path principle (and a candidate Phase-6 fourth loop/exception pattern), not
  Phase 7.
- Deeper **agent supervision / observability** (beyond the agent / subagent identity defined
  in AI Architecture, G-6(a)) is flagged for its own pass.
- **Asset Intelligence** (Phase 5) deferred — DEC-033 / Q-018 settled only the Phase-1 owner
  of the Client Asset.
- Further gap-analysis items, owned by their phases, referenced as future-gated: inbound
  community / engagement ingest, AI-monitoring privacy, prompt-injection defense.

---

## Carried / not-owned (DEC-031 G-7)
- R-027 set carried unresolved: Q-003 (Brand placement), Q-004 (Client Brain
  partitioning), the insight→durable-knowledge threshold (`Faraz-OS-Canon/domains.md:1918`).
- Q-016 and Q-017 carried; Q-017's visual-workflow-management home is its own gated,
  multi-phase decision.
- The ~9 remaining Phase-1 entity reopenings the non-canon gap analysis surfaced
  (Engagement / Community, Service Agreement → firm [Q-002], Brand [Q-003], Campaign,
  Cost-ledger / Prompt, Ticket, Ad-Account, Schedule, Consent) — each its own future gated
  decision; only Q-018 (Client Asset) is resolved (DEC-033).
- R-028 reference-altitude discipline held as the active G-1 inversion guard throughout.
