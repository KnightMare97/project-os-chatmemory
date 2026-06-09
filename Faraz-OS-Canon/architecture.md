# Faraz OS — Puzzle Board Architecture (Phase 8)

## Purpose

`architecture.md` defines the **layered assembly** (the Puzzle Board) of Faraz OS: what
named building blocks exist and which of the seven layers each sits in. It is the Phase 8
target (`Faraz-OS-Canon.md:140`, DEC-040) — the one-way downstream from Phase 7.

This file answers boundary test item #2 (DEC-030, `decisions.md:1491-1499`): *"What
concrete building blocks exist, and which layer do they sit in — Core / Domains /
Capabilities / Plugins / Infrastructure / Experience / AI?"* → **Phase 8** (the assembled
board). It is governed by DEC-040 (scope gate G-1…G-8, commit `abcc84a`).

---

## Altitude

Phase 8 architects the layered assembly as a *logical assembly view*: block names,
source-phase provenance, and cross-layer boundary rules. It does **not** specify physical
infrastructure (Phase 9), implementation technology (Phase 10), or concern-view mechanics
(Phase 7). Block names are at layer altitude — no named framework, runtime, vendor, or
physical technology.

---

## Disambiguation

**Blueprint ≠ Board (DEC-040 G-1).**
- `system-architecture-blueprint.md` = the **Blueprint** — Phase 7's cross-cutting
  concern-view document (lenses; `Faraz-OS-Canon.md:131`).
- `architecture.md` (this file) = the **Puzzle Board** — Phase 8's layered-assembly
  document (blocks; `Faraz-OS-Canon.md:140`).
- These are not synonyms. No concern-view content from the Blueprint is reproduced
  here; no assembled-layer content from the Board belongs in the Blueprint.
- The seven Phase 7 concern-views and the seven Phase 8 layers are **not a 1:1 map**
  (DEC-030, `decisions.md:1483-1489`): P7 views are lenses; P8 layers are assembled
  groupings. No P7 view "becomes" a P8 layer.

**AI Architecture ≠ AI Layer (DEC-040 G-1, highest-collision callout).**
- Phase 7 AI Architecture (`system-architecture-blueprint.md`) answers *how the system
  executes AI* — a cross-cutting concern-view (a lens).
- Phase 8 AI Layer (this file) *assembles the named execution blocks into the board* —
  it places and names; it never re-defines or re-executes.
- This principle applies to every layer pair: the concern-view is Phase 7; the
  assembled grouping is Phase 8.

---

## Governing boundary test

DEC-030 (`decisions.md:1491-1499`), governing every Phase 8 boundary call — verbatim:

> 1. *"How does the system handle [data / execution / AI / integration / security /
>    runtime] as a cross-cutting concern?"* → **Phase 7** (a concern-view / lens).
> 2. *"What concrete building blocks exist, and which layer do they sit in — Core /
>    Domains / Capabilities / Plugins / Infrastructure / Experience / AI?"* →
>    **Phase 8** (the assembled board).
> 3. *Re-defines what a domain / capability / plugin / experience-surface **is**, who
>    owns it, or its sequence* → **neither**; that is Phases 1 / 2 / 3 / 4 / 6,
>    **referenced**.

Phase 8 NAMES and PLACES. Any re-definition refers back to the owning phase.

---

## How to read this file

Each layer entry uses the **five-field skeleton**:

1. **Definition** — what the layer IS in one sentence (an assembled grouping, not a
   concern-view).
2. **Source phases** — which phases' blocks are assembled here (referenced, never
   re-authored).
3. **Assembled blocks** — the named building blocks in this layer at layer altitude,
   each with source-phase provenance.
4. **Boundary notes** — explicit cross-phase cuts and what this layer does NOT own.
5. **Carried / deferred** — open questions and deferred items affecting this layer,
   not resolved by Phase 8.

---

## Non-goals

Per DEC-040 G-5, `architecture.md` authors **no**:
- Re-definition of what a domain, capability, plugin, or experience surface *is* —
  those are Phases 1 / 2 / 3 / 4; referenced only.
- New entity or domain — Phase 1 exclusively.
- Concern-view content — Phase 7 (`system-architecture-blueprint.md`).
- Implementation technology or physical infrastructure specifics — Phase 9 / 10.
- Workflow sequences or ordered execution patterns — Phase 6 (`workflows.md`).
- Resolution of any carried-open question (Q-004, Q-006, Q-016, Q-017, Q-020, Q-022,
  Q-024, R-027 set) — all referenced where they affect a layer, none resolved here.
- Re-authoring of Phase 6 constructs (approval gate mechanism, lifecycle state machine,
  loop / exception pattern router) as Core Layer blocks — Phase 8 references the Phase 6
  workflow runtime as a dependency; those constructs are Phase 6-owned (`workflows.md`).

---

## Core Layer

- **Definition.** The product-level building blocks that constitute what Faraz OS IS as
  a platform — the platform shell: base application, mounting and enforcement machinery,
  and cross-cutting context services. Removing any Core block changes what the platform
  fundamentally is.

- **Source phases.** Phase 7 Application Architecture + Phase 7 Security Architecture
  (`system-architecture-blueprint.md:157-159, :361-369`) + Phase 4 Extension Contracts
  (`extensibility.md:196`); assembled from multiple sources (DEC-040 G-6).

- **Assembled blocks.**

  | # | Block | Source and note |
  |---|---|---|
  | 1 | **Configurable Core Host** | P7 Application Architecture (`system-architecture-blueprint.md:157-159`): "a configurable core hosts the persona portals... and mounts Feature-Modules through the Phase-4 contract." The base application that hosts Phase-2 persona portals and mounts Feature-Modules. IS the platform product. |
  | 2 | **Feature-Module Mounting Engine** | P7 (`extensibility.md:458-459, :464-465`): "the mounting / running / composing mechanism itself is Phase 7." Runtime mechanism that mounts, runs, and composes Feature-Modules. Distinct from: the Phase-4 module contract (→ Plugins Layer) and the assembled mounted modules (→ Plugins Layer, `extensibility.md:466`). |
  | 3 | **Extension Contract Surface** | P4 Extension Contracts (`extensibility.md:196`): "the explicit, versioned boundary through which every extension — plugin, provider, channel, model — interacts with the core." Core holds the stable boundary face; Phase 4 authors the contract definition (→ Plugins Layer). |
  | 4 | **Authorization Enforcement Block** | P7 Security Architecture (`system-architecture-blueprint.md:361-363`): "the Phase-2 Permission Matrix and the Phase-1 Governance rules (DEC-026) are enforced at the application and data boundaries; Security adds no rule." Enforcement engine only — rules are Phase 1 (DEC-026) / Phase 2. |
  | 5 | **Per-Client Isolation Enforcer** | P7 Security Architecture (`system-architecture-blueprint.md:364-366`): "the Data view's per-client logical scoping is enforced as an access boundary (one client's data unreachable from another's context), within single-tenant (DEC-031 G-5)." Enforcement logic above the storage layer — the storage substrate is Infrastructure. |
  | 6 | **Credential / Secret Handling Block** | P7 Security Architecture (`system-architecture-blueprint.md:367-369`): "how credentials are scoped, held, rotated, and re-authed (including the dual-path manual re-auth) — not the crypto / implementation (Phase-10)." Credential handling logic — the secret vault it reads is Infrastructure. |
  | 7 | **Platform Context Services** | Canon-endorsed by exclusion (THREE-LENS TRIO, 2026-06-09; DEC-040 G-6): client session context, client identity context, and per-client operational context are cross-cutting Core services placed in no other layer (not a domain, not a capability, not an infrastructure substrate). No direct named canon cite; confirmed unanimous. |

- **Boundary notes.**

  *Core ↔ Infrastructure cut (governing rule):*
  > Core = product-level building blocks that constitute what Faraz OS IS as a platform
  > (the platform shell). Infrastructure = abstract substrate blocks the platform runs ON.
  > Enforcement logic sits in Core; the backing resource it enforces against sits in
  > Infrastructure.

  Governing examples:

  | Core block | Its Infrastructure counterpart |
  |---|---|
  | Authorization Enforcement Block | Auth Backing Service |
  | Per-Client Isolation Enforcer | Per-Client Data Scoping Scheme |
  | Credential / Secret Handling Block | Secret Store |

  *Phase-6-not-Core guard (explicit):* The **approval gate mechanism**, **lifecycle state
  machine**, and **loop / exception pattern router** are **Phase 6-owned constructs**
  (`Faraz-OS-Canon/workflows.md:5-6, :35, :173`). Phase 8 Core Layer references the
  Phase 6 workflow runtime as a dependency; it does not name these constructs as Core
  blocks.

  *↔ Phase 1 Governance.* Authorization rules are Phase 1 (DEC-026); the Authorization
  Enforcement Block enforces them, authors none.

  *↔ Phase 2.* The Permission Matrix is Phase 2; the Authorization Enforcement Block
  enforces it. Persona portals are Phase 2; the Configurable Core Host runs them.

  *↔ Phase 4 / Plugins Layer.* The Feature-Module contract definition is Phase 4
  (→ Plugins Layer); the Feature-Module Mounting Engine (Core) is the runtime that
  mounts modules under that contract. The Extension Contract boundary definition is
  Phase 4; the Core face of that boundary is the Extension Contract Surface block.

  *↔ Phase 7.* Core blocks are named and placed here; the concern-view mechanics
  (how the application structure runs, how security enforces, how credentials are
  managed) are Phase 7 (`system-architecture-blueprint.md`).

- **Carried / deferred.** No open questions are owned by Core directly. Referenced
  dependencies: the Phase 6 workflow runtime (approval gate, lifecycle state machine,
  loop / exception router) is a dependency of the platform — owned by Phase 6, not
  resolved here. Q-004 (Client Brain partitioning) and Q-024 (Ticket lifecycle coupling)
  affect downstream Domains Layer entries. DEC-026 (authorization rules) governs the
  Authorization Enforcement Block.

---

## Infrastructure Layer

- **Definition.** The abstract substrate building blocks the platform runs on —
  persistence, compute, queuing, auth, and secrets beneath the Core and domain blocks.
  Named at abstract altitude only; physical technology is Phase 9.

- **Source phases.** Phase 7 Data Architecture (per-client scoping and persistent data
  substrate), Phase 7 Runtime Architecture (job runtime, worker, event bus), and Phase 7
  Security Architecture (auth backing service, secret store, observability) — each
  Phase-7 view names the substrate its concern runs on; Phase 8 assembles those substrate
  references into a single Infrastructure Layer. DEC-040 G-7.

- **Assembled blocks.**

  | # | Block | Abstract definition |
  |---|---|---|
  | 1 | **Persistent Store** | Abstract durable storage substrate for domain entities and artifacts. |
  | 2 | **Job Queue / Event Bus** | Abstract queuing and event-distribution substrate for async work and domain events. |
  | 3 | **Worker / Job Runtime** | Abstract compute substrate for background and async job execution. |
  | 4 | **Auth Backing Service** | Abstract authentication and identity substrate that the Core Authorization Enforcement Block enforces over. |
  | 5 | **Secret Store** | Abstract secrets vault that the Core Credential / Secret Handling Block reads from. |
  | 6 | **Observability Infrastructure** | Abstract logging, metrics, and tracing substrate for runtime visibility. |
  | 7 | **Per-Client Data Scoping Scheme** | Data-organization layout within the Persistent Store that makes per-client logical data separation a storage-level reality — the substrate beneath the Core Per-Client Isolation Enforcer. |

  Physical technology for each block is assigned by Phase 9 Infrastructure Design
  (`infrastructure.md`). No technology name is authored here.

- **Boundary notes.**

  *P8 ↔ P9 cut (structural — must not be crossed in this file):*
  > Phase 8 Infrastructure Layer names blocks at **abstract** altitude — no named
  > technology, framework, database, or service. Phase 9 Infrastructure Design
  > (`infrastructure.md`) assigns physical technology to each abstract block.

  *↔ Core Layer.* Enforcement and handling logic sits in Core; the substrate it enforces
  against or reads from sits here. The Per-Client Isolation Enforcer (Core) enforces
  over the Per-Client Data Scoping Scheme (Infrastructure). The Credential / Secret
  Handling Block (Core) reads the Secret Store (Infrastructure). The Authorization
  Enforcement Block (Core) enforces over the Auth Backing Service (Infrastructure).
  Core blocks activate as product logic; Infrastructure blocks are the resources Core
  and domain blocks consume.

  *↔ Phase 7 (Data / Runtime / Security Architecture).* The Phase 7 concern-views
  describe *how* the system handles data, runtime, and security as cross-cutting
  concerns; they name the substrate each concern runs on. Phase 8 assembles those
  substrate references into this layer; nothing is re-authored from Phase 7.

  *↔ Phase 9.* This layer holds abstract block names only. Technology selection is Phase
  9; Phase 8 must not anticipate it.

- **Carried / deferred.** Phase 9 Infrastructure Design (`infrastructure.md`) is the
  next downstream phase for each abstract block. No open question is resolved here. The
  physical implementation of per-client data isolation (partitioning strategy) is a
  Phase 9 decision.

---

## Domains Layer

- **Definition.** The assembled named business-responsibility domains constituting Faraz OS's
  domain model — every Phase 1-confirmed domain, placed on the board at naming altitude.

- **Source phases.** Phase 1 Domain Discovery (`domains.md`). Eleven domains are confirmed;
  their entities, aggregates, bounded contexts, inbound/outbound events, and Phase 1 open
  questions are Phase 1 truth and are **not re-authored** by Phase 8.

- **Assembled blocks.**

  | # | Domain block | Source |
  |---|---|---|
  | 1 | **CRM** | Phase 1 (`domains.md:695`): Lead Acquisition & Conversion + Current Client Management + Dead Lead Recovery + CRM Reporting. Entities include Lead, Client Account, Brand (DEC-036), Service Agreement (DEC-034). |
  | 2 | **Workforce** | Phase 1 (`domains.md:1010`): Human Operator identity, role, capacity, skills, and assignment eligibility. |
  | 3 | **Knowledge** | Phase 1 (`domains.md:1225`): Agency Brain, Knowledge Artifacts, Decision Log, Learning Records, Client Brain (DEC-027 — owned by Knowledge). |
  | 4 | **Client Success** | Phase 1 (`domains.md:1458`): Client Relationship, Approval Response, Escalation Case, Coordination Request, Ticket (DEC-039). |
  | 5 | **Intelligence** | Phase 1 (`domains.md:1742`): Insights, Recommendations, Scores, Anomaly and Trend signals. |
  | 6 | **Finance** | Phase 1 (`domains.md:1949`): Invoice, Payment, Receivable, Payable, Settlement. Per-job AI cost (UsageRecord) is AI Operations (DEC-038), not Finance. |
  | 7 | **Governance** | Phase 1 (`domains.md:2179`): Policy, Authorization Rules, Checkpoint Definitions, Audit Records, Routing Constraints. |
  | 8 | **Service Delivery** | Phase 1 (`domains.md:3281`): Engagement, Deliverable, Revision Cycle, Delivery Task, Engagement Scope (Domain Artifact). |
  | 9 | **Media & Assets** | Phase 1 (`domains.md:3801`; DEC-033, Q-018): Client Asset entity — raw upload, client-uploaded, AI-generated, and produced states. |
  | 10 | **Community** | Phase 1 (`domains.md:3900`; DEC-035, Q-019): Comment, Direct Message, Conversation/Thread, Engagement Reply — the B2C post-publish audience axis. |
  | 11 | **AI Operations** | Phase 1 (`domains.md:4005`; DEC-038, Q-021): UsageRecord (per-job AI usage/cost record). |

- **Boundary notes.**

  *Phase 8 names domains — it does not re-define them.* Each domain block is placed here
  at naming altitude. Entities, aggregates, bounded contexts, business rules, and domain
  events are Phase 1 truth (`domains.md`); this file references, never re-authors.

  *Concepts that are NOT domain blocks (key disambiguation):*
  - Brand → CRM Entity (DEC-036), not a domain.
  - Service Agreement → CRM Entity (DEC-034), not a domain.
  - Client Brain → Memory Object / Shared Service Artifact owned by Knowledge (DEC-027), not
    a domain.
  - Engagement Scope → Domain Artifact aligned to Service Delivery, not a domain.

  *↔ Capabilities Layer.* Capabilities (Phase 3) are reusable functions, not domains. The
  Intelligence domain and the Analytics/Reporting capabilities overlap at altitude — that
  boundary is a Phase 1 open question (`domains.md:1939-1940`), referenced only.

  *↔ AI Layer.* UsageRecord is a Domains Layer entity (AI Operations); AI Layer blocks are
  execution-time infrastructure, not business-domain entities.

- **Carried / deferred.** Q-004 (Client Brain per-Client/per-Brand partitioning), Q-006
  (Service Agreement ↔ Engagement Scope consistency), Q-022 (prompt/template versioning,
  registered DEC-038), Q-024 (Ticket ↔ Escalation Case lifecycle coupling, registered
  DEC-039) — all referenced; none resolved by Phase 8. Approximately 4 Phase-1 entity
  reopenings remain pending (Campaign, Ad-Account, Schedule, Consent).

---

## Capabilities Layer

- **Definition.** The assembled named reusable business capabilities of Faraz OS — every
  Phase 3-defined capability block placed on the board at naming altitude.

- **Source phases.** Phase 3 Capability Map (`capabilities.md`). All eight capabilities are
  written (Batches A–B, Snapshot-025 / DEC-024); referenced-never-redefined.

- **Assembled blocks.**

  | # | Capability block | Source |
  |---|---|---|
  | 1 | **Publishing** | Phase 3 (`capabilities.md:73`): push a piece of approved content to a channel. |
  | 2 | **Reporting** | Phase 3 (`capabilities.md:95`): assemble and generate a report artifact from domain-held data. |
  | 3 | **Content Creation** | Phase 3 (`capabilities.md:121`): produce a non-video content asset. |
  | 4 | **Research** | Phase 3 (`capabilities.md:140`): gather and synthesize information into a research output. |
  | 5 | **Strategy** | Phase 3 (`capabilities.md:156`): analyze inputs and produce a strategic recommendation. |
  | 6 | **Video Creation** | Phase 3 (`capabilities.md:172`): produce a video asset. |
  | 7 | **Analytics** | Phase 3 (`capabilities.md:189`): compute metrics and aggregations from domain-held data. |
  | 8 | **Lead Scoring** | Phase 3 (`capabilities.md:215`): compute a score for a lead. |

- **Boundary notes.**

  *Phase 8 names capabilities — it does not re-define them.* Each capability block is
  placed here at naming altitude. Definition, execution mode, produces, provider
  dependencies, and boundary notes are Phase 3 truth (`capabilities.md`); not re-authored
  here.

  *Capabilities ≠ Domains.* A capability is a reusable function (Phase 3); a domain is a
  business-responsibility area (Phase 1). Analytics and Reporting are capabilities;
  Intelligence is a domain. The boundary between them is a Phase 1 open question
  (`domains.md:1939-1940`), referenced only.

  *Capabilities ≠ Plugins.* Provider dependencies named in Phase 3 entries bind through
  Phase 4 extension points (→ Plugins Layer). The capability names the function; the
  plugin names the swappable tool.

  *↔ Phase 6.* Ordered sequences that invoke capabilities (e.g. Approval → Publishing →
  Reporting) are Phase 6 workflows. Capabilities are order-free, gate-free functions.

  *↔ Phase 7.* Provider wiring that realizes capability execution is Phase 7.

- **Carried / deferred.** Phase 3 "Serves" inference fields are pending Phase 1 domain
  confirmation. Intelligence vs Analytics/Reporting boundary is an inherited open question
  (`domains.md:1939-1940`).

---

## Plugins Layer

- **Definition.** The assembled named extensibility-mechanism blocks of Faraz OS — every
  Phase 4-defined extension-point type placed on the board at naming altitude. This layer
  includes the AI Model Routing **policy** (Phase 4) and Feature Modules (DEC-032).

- **Source phases.** Phase 4 Extensibility Model (`extensibility.md`). Eight named
  extension-point types (Batches A–C plus Feature Modules, DEC-032);
  referenced-never-redefined.

- **Assembled blocks.**

  | # | Plugin Layer block | Source and note |
  |---|---|---|
  | 1 | **Provider Model** | Phase 4 (`extensibility.md:84`): the contract for any swappable external provider — AI model provider, media tool, channel/platform, or third-party service. |
  | 2 | **Channel Model** | Phase 4 (`extensibility.md:120`): the contract for a channel — a typed specialization of the Provider Model for content-delivery providers. |
  | 3 | **Extension Contracts** | Phase 4 (`extensibility.md:196`): the explicit, versioned boundary through which every extension — plugin, provider, channel, model — interacts with the core. Distinct from: the Core Layer's Extension Contract Surface (the core face of this boundary). |
  | 4 | **Permission (Capability Grant Model)** | Phase 4 (`extensibility.md:236`): the model for capability grants to extensions — what a plugin, provider, channel, or model is permitted to do, expressed as grants carried through the contract surface. |
  | 5 | **Plugin Model** | Phase 4 (`extensibility.md:273`): the model for a plugin — a packaged unit that attaches extensions (channels, providers, or specialized integrations) to the core through the contract surface. |
  | 6 | **Model (AI Model)** | Phase 4 (`extensibility.md:308`): the abstraction for an AI model as a swappable unit — a specific model and tier the system invokes through a provider. |
  | 7 | **AI Model Routing Policy** | Phase 4 (`extensibility.md:351`): the **policy-driven selection** mechanism that chooses among interchangeable models, providers, agents, and execution paths by policy — cost, quality, latency, availability, risk, task type. **This is the routing POLICY (Phase 4).** The executing routing engine is the AI Layer's Routing Engine block (`extensibility.md:391-392`: "the routing policy is Phase 4; the engine that executes routing is Phase 7 AI Architecture"). |
  | 8 | **Feature Modules** | Phase 4 (`extensibility.md:426`; DEC-032): a mountable unit of product functionality that mounts on the base and may aggregate plugins. The **mounting/running/composing mechanism** is the Core Layer's Feature-Module Mounting Engine block (`extensibility.md:464-465`: "the runtime that mounts, runs, or composes modules is Phase 7"). |

- **Boundary notes.**

  *Phase 8 names extension-point types — it does not re-define them.* Each block is
  placed here at naming altitude. Contract surfaces, governance touchpoints, runtime/config
  attributes, and per-entry boundary notes are Phase 4 truth (`extensibility.md`); not
  re-authored here.

  *AI Model Routing Policy ≠ Routing Engine (AI Layer) — critical guard:*
  > The routing **policy** (cost, quality, latency, availability, risk, task type) sits in
  > this layer (Phase 4, `extensibility.md:391-392`). The executing routing **engine** —
  > the runtime block that applies the policy — is the Phase 8 AI Layer's **Routing
  > Engine** block. Two distinct blocks at two distinct layer altitudes.

  *Feature Modules ↔ Core:* The Feature-Module Mounting Engine (Core Layer) is the Phase
  7-originated runtime that mounts modules under the Phase 4 contract. Feature Modules
  (this layer) are what is mounted. The runtime mechanism is Core; the mountable product
  units are Plugins.

  *Extension Contracts ↔ Core:* The Extension Contract Surface (Core Layer) is the
  **core face** of the versioned boundary. Extension Contracts (this layer) is the Phase 4
  **definition** of that contract. Distinct blocks: boundary face (Core) vs contract
  definition (Plugins).

  *↔ Phase 4 deferred sub-items:* Versioning & Compatibility, External Integrations, and
  Future Domains are Phase 4-deferred stubs (`extensibility.md:472-483`); not named as
  Plugins Layer blocks.

  *↔ Phase 1 Governance.* The Permission grant model carries grants within the bounds of
  Phase 1 authorization rules (DEC-026); it does not author those rules.

  *↔ Phase 7.* The contract surface and plugin attachment contract are Phase 4; the system
  wiring that realizes them is Phase 7.

- **Carried / deferred.** Q-014 resolved (DEC-026). Q-020 (access-status/connection-health
  owner — Phase 4 carried open). Versioning & Compatibility, External Integrations, and
  Future Domains: Phase 4 deferred sub-items, not authored here.

---

## Experience Layer

- **Definition.** The assembled named experience-architecture blocks of Faraz OS — the Phase
  8 grouping of all Phase 2-defined structural elements placed on the board at naming
  altitude. The Experience Layer is the render side of the system: what personas see, what
  surfaces they work in, and how access is governed.

- **Source phases.** Phase 2 Experience Architecture (`experience-architecture.md`).
  Referenced-never-redefined.

- **Assembled blocks.**

  | # | Experience Layer block | Source |
  |---|---|---|
  | 1 | **Persona Model** | Phase 2 (`experience-architecture.md:109`): the locked set of 5 experience archetypes — Operator, Manager, Contractor, Client, System Administrator — plus a Future Personas deferred placeholder (`experience-architecture.md:121`). Persona is distinct from Workforce identity (Phase 1). |
  | 2 | **Operating Surfaces** | Phase 2 (`experience-architecture.md:151`): functional workspaces through which personas perform work. 16-surface firm inventory (`experience-architecture.md:223`). **Agent & Workflow Monitor** (`experience-architecture.md:239`) is surface #6 and is the Experience Layer's render-side face of the Experience↔AI seam: it presents AI and workflow execution state; the executing blocks are AI Layer (not here). |
  | 3 | **Persona Portals** | Phase 2 (`experience-architecture.md:280`): the visual panel each persona group receives — one portal per persona, containing its scoped set of Operating Surfaces (`experience-architecture.md:303`). Five portals: Operator, Manager, Contractor, Client, System Administrator. |
  | 4 | **Navigation Model** | Phase 2 (`experience-architecture.md:423`): the movement model across portals and surfaces — how personas navigate within and between workspaces. |
  | 5 | **Permission Matrix** | Phase 2 (`experience-architecture.md:502`): the three-altitude governing access structure that projects Phase 1 Governance authorization rules onto persona↔surface exposure. The authoritative projection of who sees what. |
  | 6 | **Cross-Domain Views** | Phase 2 (`experience-architecture.md:651`): cross-domain data aggregation surfaces hosted inside the Reports & Analytics Surface — Performance & Analytics, Team Oversight, Engagement Health, Client Engagement Summary. |
  | 7 | **Channel Behaviors** | Phase 2 (`experience-architecture.md:792`): per-channel UX property definitions — format/media constraints, preview affordance, notification capability — the Phase 2 rendering behaviors that hang off Phase 4 channel-level properties. |

- **Boundary notes.**

  *Phase 8 names Experience Layer blocks — it does not re-define them.* Each block is
  placed here at naming altitude. Surface definitions, portal compositions, permission
  rules, view inventories, and navigation mechanics are Phase 2 truth
  (`experience-architecture.md`); not re-authored here.

  *Experience↔AI cut — produce vs render (governing seam):*
  > The **AI Layer** ENDS at what executes and produces execution results (agents run,
  > chains resolve, routing fires, models are invoked). The **Experience Layer** BEGINS
  > at what renders those results for a persona. The Agent & Workflow Monitor (Operating
  > Surface #6, `experience-architecture.md:239`) is the render-side face: it presents AI
  > and workflow execution state — it does **not** execute it. Agent-facing surface
  > rendering stays here (Phase 2 / the Q-013 split; DEC-031 G-6(b));
  > `blueprint.md:265-266`.

  *↔ Phase 1 Governance.* The Permission Matrix projects Phase 1 authorization rules
  (DEC-026); it does not author them. Persona identity is Workforce (Phase 1 Workforce);
  Phase 2 references it.

  *↔ Phase 4 / Plugins Layer.* Channel Behaviors (this layer) define per-channel UX
  properties; the channel contract is Phase 4 (→ Plugins Layer). Phase 2 writes behaviors
  that hang off Phase 4 channel attributes.

  *↔ Phase 3 / Capabilities Layer.* Operating Surfaces are not capabilities. The KPI
  computation is Phase 3 (Analytics capability); displaying it on the Reports & Analytics
  Surface is Phase 2 (`experience-architecture.md:668`).

  *↔ Phase 6.* Operating Surfaces are not workflows. Ordered execution paths are Phase 6.

- **Carried / deferred.** Q-004 (Client Brain per-Client/per-Brand partitioning) affects
  the Client Brain Surface — referenced, not resolved. Q-017 (visual workflow management)
  may add a surface or view to this layer pending its own gated resolution (`blueprint.md:474-475`).
  Five flagged Operating Surfaces remain pending in Phase 2 Open and Deferred Items.
  Permission Matrix population is deferred until Phase 1 Governance rules are concrete.

---

## AI Layer

- **Definition.** The assembled named AI-execution blocks of Faraz OS — the Phase 8
  grouping of the Phase 7 AI Architecture execution blocks placed on the board. The AI
  Layer is the produce side of the system: what executes, what has identity, what runs
  agents, routes models, and handles human integration paths.

- **Source phases.** Phase 7 AI Architecture (`system-architecture-blueprint.md:245-294`),
  DEC-040 G-8. Five blocks fully named; two deferred slots carried. Referenced-never-redefined.

- **Assembled blocks.**

  | # | AI Layer block | Source and note |
  |---|---|---|
  | 1 | **Chain Orchestrator** | Phase 7 AI Architecture (`blueprint.md:250-252`): "the system invokes models and composes agent / subagent execution into chains, selecting per part by policy." The execution spine that composes agent/subagent steps into chains and manages handoffs. |
  | 2 | **Agent / Subagent Execution Unit** | Phase 7 AI Architecture (`blueprint.md:252-255`): "what an agent / subagent *is* architecturally — a defined executing entity with a lifecycle-as-architecture (instantiated, executes, hands off, retires)." The execution unit with identity — distinct from the role it plays in a Phase-6 sequence (role-vs-identity litmus, DEC-031 G-6(a)). |
  | 3 | **Routing Engine** | Phase 7 AI Architecture (`blueprint.md:262-264`): "This view *executes* the routing engine but authors no selection policy — Phase 4 owns it." The runtime block that applies the Phase 4 AI Model Routing Policy (Plugins Layer) at per-chain-step invocation. Policy source: `extensibility.md:391-392`. |
  | 4 | **Model Invocation Interface** | Phase 7 AI Architecture (`blueprint.md:261-262`): executes against the Phase 4 Model abstraction (`extensibility.md:308`) — the abstraction layer between the orchestration tier and the actual model call. The swappable contract is Phase 4 (Plugins Layer, Model block); this block is the Phase 7 execution of that interface. |
  | 5 | **Human / Hybrid Execution Path** | Phase 7 AI Architecture (`blueprint.md:276-278`): "Human / hybrid execution paths are first-class alternatives to AI-default execution (HITL), never an afterthought." The execution path that routes steps requiring a human and manages the human-response re-entry into the chain. |
  | — | ***Deferred slot 1:* Q-017 Workflow Management Engine** | *Deferred pending Q-017 gate* (`blueprint.md:474-475`: "Q-017's visual-workflow-management home is its own gated, multi-phase decision"). If resolved into this layer, adds a named block here. |
  | — | ***Deferred slot 2:* Agent Supervision / Observability** | *Deferred — own gated pass* (`blueprint.md:462-463`: "Deeper agent supervision / observability is flagged for its own pass"). Not authored here. |

- **Boundary notes.**

  *Phase 8 names AI Layer execution blocks — it does not re-define them.* Each block is
  placed here at naming altitude. The AI Architecture concern-view mechanics — how the
  chain-modelling execution works, the lifecycle-as-architecture of agents, the HITL
  integration model — are Phase 7 truth (`blueprint.md:245-294`); not re-authored here.

  *Experience↔AI cut — produce vs render (governing seam):*
  > The AI Layer ENDS at what executes and produces results. The Experience Layer BEGINS
  > at what renders those results for a persona. Agent-facing surface rendering is
  > Experience (Phase 2 / Q-013 split, DEC-031 G-6(b)). The Agent & Workflow Monitor
  > (`experience-architecture.md:239`) renders AI Layer execution state — it does not
  > execute it. The produce→render handoff is the seam between this layer and the
  > Experience Layer.

  *AI Layer exclusions (four explicit guards):*
  - **Surface rendering → Experience Layer.** No surface, portal, or UX block belongs
    here. Agent-facing rendering is the Agent & Workflow Monitor (Experience Layer).
  - **Routing policy → Plugins Layer.** The AI Model Routing Policy is a Phase 4
    extension point (Plugins Layer block 7). The Routing Engine (this layer) executes it.
    Policy ≠ engine (`extensibility.md:391-392`).
  - **UsageRecord → Domains Layer.** Per-job AI cost records are AI Operations domain
    (Domains Layer). This layer holds execution blocks, not business-domain entities.
  - **Prompt/template versioning → Q-022.** Unresolved (registered DEC-038). Not
    authored here.

  *↔ Phase 3 / Capabilities Layer.* AI Layer blocks execute capabilities (Phase 3);
  they do not define them. The abilities invoked are Phase 3; the execution infrastructure
  is Phase 7 (`blueprint.md:280`: "↔ Phase 3: executes capabilities; defines none").

  *↔ Phase 6.* Phase 6 names where an agent-performed step sits in a sequence (its
  *role*); Phase 7 defines what the agent *is* (its *identity*). Role-vs-identity litmus:
  `workflows.md:129-133`; DEC-028.

  *↔ Phase 4 / Plugins Layer.* The Routing Engine (this layer) executes the Phase 4
  AI Model Routing Policy (Plugins Layer). The Model Invocation Interface (this layer)
  executes against the Phase 4 Model abstraction (Plugins Layer). Execution here; policy
  and contract there.

- **Carried / deferred.** Q-017 (Workflow Management Engine — own gated decision, may
  add block 6 to this layer). Agent Supervision / Observability (own gated pass, may add
  block 7). Q-022 (prompt/template versioning — separate gate). DEC-040 G-8 deferred
  slots registered; neither resolved here.

---

## Status

Phase 8 Puzzle Board Architecture — **first-write complete** (DEC-040; Batches A, B, C).

All seven layers have their first-write entries:
Core (7 blocks) · Infrastructure (7 abstract blocks) · Domains (11 domains) ·
Capabilities (8 capabilities) · Plugins (8 extension-point types) ·
Experience (7 structural blocks) · AI (5 blocks + 2 deferred slots).

Pending gated events (separate decisions, not Phase 8's to resolve):
- Phase 9 Infrastructure Design (`infrastructure.md`) — assigns physical technology to
  each abstract Infrastructure block.
- Q-017 Workflow Management Engine — own gated, multi-phase decision; may add a block to
  the AI Layer (deferred slot 1).
- Agent Supervision / Observability — own gated pass; may add a block to the AI Layer
  (deferred slot 2).
- Phase-1 entity reopenings (Campaign, Ad-Account, Schedule, Consent) — each its own
  future gated decision; may extend the Domains Layer when resolved.

This file does not author those decisions. It will be updated when gates close.
