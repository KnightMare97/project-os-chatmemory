# Extensibility Model — Phase 4

## Purpose
This file defines the extensibility layer of Faraz OS: the intentional
extension points, the contracts through which extensions reach the core, and the
capability grants by which providers, channels, models, plugins, and (later)
domains attach to a stable core.

It names **what is swappable and how it attaches, at altitude**. It does not
author domain truth, the experience layer, ordered workflow, authoritative
governance rules, or implementation technology.

It records each extension point on a fixed entry skeleton.

---

## Status
Phase 4 scope is defined and human-confirmed (DEC-025 / Snapshot-027).

This file is written in batches (DEC-025). **All eight in-scope entries are
written** (Batches A–C): the file skeleton; the Provider Model, Channel Model,
Extension Contracts, Permission, Plugin Model, Model, and AI Model Routing
entries; the Runtime vs Config-Time Extensions framing section; the
deferred-sub-item stubs; the non-goals; and the open/inherited flags. The four
deferred sub-items (Versioning & Compatibility, External Integrations, Feature
Modules, Future Domains) remain flagged stubs per DEC-025.

No Phase 1 domain truth, ownership, or boundary is changed by this file. Phase 4
references Phase 1; it does not reinterpret it.

---

## Governing rules (referenced, not restated here)
This file **applies** the Phase 4 rules; it does not restate them. They are
recorded in **DEC-025 / Snapshot-027**:
- the Phase 4 definition / altitude;
- the locked distinction set (Model and AI Model Routing separate; Channel Model
  a typed Provider-Model specialization — a DEC-025 inference, not pre-existing
  canon);
- the closed boundary set (definition/altitude + six cross-phase boundaries, with
  Phase 6 and Phase 7 split and Phase 1 a single Governance boundary);
- the selection-vs-sequence test; the grant-altitude rule (R-028); the
  contract-altitude rule; the runtime/config attribute rule;
- the six-field entry skeleton; and the non-goals.

It also respects, by reference: the **Governing Boundary Test**
(`experience-architecture.md`, §Governing Boundary Test); the **Extensibility
Philosophy** and **AI Philosophy** (Phase 0); and the three-altitude permission
separation recorded in DEC-019 / FIND-022, of which this file states only Phase
4's altitude — extension / plugin / provider capability grants via contracts; the
full triad is referenced there, not restated here.

Altitude rule, by reference: what is swappable + how it attaches = Phase 4;
authoritative rule / human identity / domain truth = Phase 1; the experience
projection = Phase 2; the ordered flow = Phase 6; the system wiring = Phase 7.

---

## How to read an entry
Each extension point is recorded on six fields:

- **Definition** — what the extension point is, as an intentional extension point
  (Extensibility Philosophy #2).
- **Contract surface** — how the core and the extension interact (APIs, events,
  permissions, schemas, versioned interfaces — Philosophy #4), named **at
  altitude**; the field names the interaction surface, it does not specify it.
- **Provider-agnostic note** — what is swappable behind the contract
  (Philosophy #6).
- **Governance touchpoints** — which governance concerns an extension must
  respect: *authentication, authorization, validation, auditability, safety
  controls, and policy enforcement* (Philosophy #8), named **at altitude**; the
  authoritative rules are Phase 1 Governance (DEC-019 / FIND-022) and are not
  enumerated here.
- **Runtime vs Config-Time** — which mode(s) the extension point supports
  (Philosophy #10); naming the mode is the attribute, not the deployment /
  governance policy that decides it.
- **Boundary notes / inherited flags** — cross-phase boundary notes and any
  inherited Phase 1 question, referenced and preserved unresolved.

---

## Extension points

### Provider Model
- **Definition.** The contract for any swappable external **provider** — an AI
  model provider, media tool, channel/platform, or third-party service — that the
  core can bind to without depending on any specific one. Providers are an
  intentional extension point (Philosophy #2): they are exactly where long-term
  change (swapping externals) is expected.
- **Contract surface.** A provider reaches the core only through the explicit
  contract surface — the APIs, events, permissions, schemas, and versioned
  interfaces named by Extension Contracts (Philosophy #4) — never through direct
  database access or private internal state. Named here at altitude; the contract
  mechanism itself is the Extension Contracts extension point (Batch B).
- **Provider-agnostic note.** This model is the embodiment of
  provider-agnosticism (Philosophy #6): AI models, media tools, channels, and
  third-party services are swappable behind the provider contract without forcing
  architectural rewrites, and the core must not depend on the presence of any
  specific provider (Philosophy #3).
- **Governance touchpoints.** A provider binding must respect the governance
  concerns defined by the core — authentication, authorization, validation,
  auditability, safety controls, and policy enforcement (Philosophy #8) — at
  altitude; the authoritative rules belong to Phase 1 Governance (DEC-019 /
  FIND-022) and are not enumerated here.
- **Runtime vs Config-Time.** Provider bindings may be swappable at runtime or
  changed through configuration / deployment policy (Philosophy #10); which mode
  applies to a given provider is a per-binding attribute, not a rule set here.
- **Boundary notes / inherited flags.**
  - ↔ Phase 3: a capability names the *ability*; the Provider Model names the
    swappable *tool* it binds — the inverse of the DEC-024 capability boundary.
    The eight capability provider-dependencies
    (`capabilities.md:83, :106, :128, :150, :166, :179, :199, :229`) bind here.
  - ↔ Phase 6: the Provider Model makes providers *selectable* (order-free);
    choosing among them by policy is routing (see AI Model Routing, Batch C), not
    orchestration — ordered flow / gates are Phase 6 (selection-vs-sequence test).
  - ↔ Phase 7: the contract surface is Phase 4; the system wiring that realizes
    it is Phase 7.
  - No inherited Phase 1 question is resolved here.

### Channel Model
*The Channel Model is the Batch A binding deliverable: it carries the DEC-025
four-item minimum (taxonomy · the three experience attributes · the
specialization statement · the deferral boundary) and is gated by the DEC-025
acceptance test, restated at the end of this entry.*

- **Definition.** The contract for a **channel** — a typed **specialization of the
  Provider Model** for providers whose role is to deliver content to (or receive
  it from) an external destination. A channel is a swappable external reached
  through the provider contract; the Channel Model adds the channel-specific
  elements the general Provider Model does not carry. *This specialization is a
  DEC-025 scoping inference, not pre-existing canon:* the canon phase map lists
  Channel Model and Provider Model as parallel sub-items; the typing is reasoned
  from Philosophy #5/#6 and from Publishing's provider-dependency field
  (`capabilities.md:82-83`).
- **Channel taxonomy (typed categories — evidence-grounded).** Channels are typed
  by **delivery role**. The taxonomy is seeded only from what domains/capabilities
  already reference, and grows only as new references appear (it is not invented):
  - **Outbound content channel** — receives a dispatched, approved content item.
    Grounded in the Publishing capability ("push a piece of approved content to a
    channel", `capabilities.md:74-75`).
  Named platforms (e.g. Instagram, LinkedIn, YouTube) are **illustrative instances
  of a category, never core entities** (`non-goals.md:9`). Other candidate
  categories (e.g. notification-delivery, inbound/ingestion) are **not asserted**
  here: no current domain or capability names them, and seeding them would invent
  a taxonomy (R-028). They enter the taxonomy when a domain/capability references
  them.
- **Channel experience attributes (the three Phase 2 reads).** Each channel
  category carries three channel-level properties, mapped 1:1 to the Phase 2
  Channel Behaviors dimensions (`experience-architecture.md:696-698`):
  1. **Format / media constraints** — what content formats and media the channel
     accepts (the property Phase 2 reads to write *rendering differences per
     channel*).
  2. **Preview affordance** — whether and how the channel supports previewing
     content before dispatch (→ *preview behavior per channel*).
  3. **Notification capability** — whether and how the channel surfaces
     notifications (→ *notification user experience per channel*).
  Phase 4 defines these as channel-level properties; Phase 2 writes the
  human-experience behaviors that hang off them. The behaviors themselves are
  Phase 2, not authored here.
- **Contract surface.** A channel inherits the Provider Model contract surface
  (the APIs, events, permissions, schemas, versioned interfaces named by
  Extension Contracts / Philosophy #4), named at altitude, and adds the
  channel-specific contract elements implied by the three attributes above. The
  concrete integration mechanics — credential / auth, API binding, delivery /
  dispatch semantics, rate limits — are **deferred to External Integrations** and
  are not specified here.
- **Provider-agnostic note.** Channels are swappable behind the channel contract
  (Philosophy #6); the core depends on no specific channel or platform.
- **Governance touchpoints.** A channel binding must respect the same governance
  concerns at altitude — authentication, authorization, validation, auditability,
  safety controls, and policy enforcement (Philosophy #8); authoritative rules are
  Phase 1 Governance (DEC-019 / FIND-022), not enumerated here.
- **Runtime vs Config-Time.** Channel bindings, like other provider bindings, may
  be runtime-swappable or config/deployment-time (Philosophy #10); the mode is a
  per-binding attribute.
- **Boundary notes / inherited flags.**
  - ↔ Phase 2 (the unblock handoff): this entry provides the taxonomy and the
    three attributes; Phase 2 Channel Behaviors (KNI-18) writes rendering /
    preview / notification UX per channel type from them. Phase 4 provides the
    channel properties; Phase 2 owns the human-experience behaviors.
  - **Deferral boundary:** integration mechanics (credential/auth, API binding,
    delivery/dispatch semantics, rate limits) and concrete per-platform
    integrations are deferred to External Integrations; not in this file.
  - ↔ Phase 6 / Phase 7: channel *selection* is order-free (Phase 4); ordered
    publish/dispatch flow is Phase 6; the wiring that realizes the channel
    contract is Phase 7.
  - No inherited Phase 1 question is resolved here.
- **Acceptance test (DEC-025, verbatim).** *"The Channel Model is deep enough iff
  Phase 2 can later write rendering / preview / notification behaviors for each
  channel type using only the taxonomy and the three experience attributes
  (format/media constraints · preview affordance · notification capability), with
  no further Phase 4 content required."* This entry meets it: the taxonomy gives
  the channel type(s) and the typing axis, and the three attributes give Phase 2
  the per-type properties it needs — no further Phase 4 content required.

### Extension Contracts
- **Definition.** The contract surface itself: the explicit, versioned boundary
  through which every extension — plugin, provider, channel, model — interacts
  with the core. An intentional extension point (Philosophy #2): the contract is
  the stable boundary that lets the core and extensions change independently.
  Extensions reach the core **only** through explicit APIs, events, permissions,
  schemas, and versioned interfaces, never through direct database access or
  private internal state (Philosophy #4, `extensibility-philosophy.md:13-15`).
- **Contract surface.** This entry names the surface the other extension points
  reference. Its interaction modes — APIs, events, permissions, schemas, and
  versioned interfaces (Philosophy #4) — are named here **at altitude**; the
  concrete interface definitions, payload schemas, and versioning mechanics are
  not specified. The core remains stable and independent of any specific
  extension (Philosophy #3, `extensibility-philosophy.md:10-11`).
- **Provider-agnostic note.** The contract is what makes provider-agnosticism
  possible (Philosophy #6, `extensibility-philosophy.md:22-23`): because
  extensions bind only through it, any provider, channel, model, or plugin is
  swappable behind it without forcing core rewrites.
- **Governance touchpoints.** The contract is the boundary at which governance is
  enforced: every extension interaction must respect authentication,
  authorization, validation, auditability, safety controls, and policy
  enforcement (Philosophy #8, `extensibility-philosophy.md:29-30`) at altitude.
  Permissions are one of the contract's interaction modes (Philosophy #4); the
  authoritative rules are Phase 1 Governance (DEC-019 / FIND-022) and are not
  enumerated here.
- **Runtime vs Config-Time.** The contract is the stable element; whether a given
  extension binds at runtime or through configuration / deployment policy is a
  per-binding attribute (Philosophy #10, `extensibility-philosophy.md:36-38`).
  Contract *evolution over time* (backward compatibility, Philosophy #11) belongs
  to the deferred Versioning & Compatibility sub-item, not here.
- **Boundary notes / inherited flags.**
  - Within Phase 4: the Provider, Channel, Permission, and Plugin entries
    reference this contract surface at altitude; this entry formalizes it. It
    names the contract machinery; it does not specify it (contract-altitude rule).
  - ↔ Phase 7: the contract is the Phase 4 boundary definition; the system wiring
    that realizes it (transport, storage, runtime) is Phase 7.
  - Deferral: concrete interface/schema specs are Phase 7 / External Integrations;
    contract versioning is Versioning & Compatibility — both deferred.
  - No inherited Phase 1 question is resolved here.

### Permission
- **Definition.** The model for **capability grants** to extensions — what a
  plugin, provider, channel, or model is permitted to do — expressed as grants
  carried through the contract surface. This is Phase 4's altitude in the
  three-altitude permission separation: Phase 4 owns extension / plugin / provider
  capability grants via contracts. The full triad is recorded in DEC-019 /
  FIND-022 and **referenced there, not restated here**. (The boundary with Phase 1
  Governance and the Phase 2 Permission Matrix is drawn in the Boundary notes
  below.)
- **Contract surface.** Grants are expressed through the contract's *permissions*
  interaction mode (Philosophy #4): an extension declares the capabilities it
  requires and is granted them through the contract, never by reaching past it.
  Named at altitude; the concrete grant schema is not specified.
- **Provider-agnostic note.** Because grants are contract-carried, any provider,
  channel, or plugin is bound under the same grant model regardless of vendor
  (Philosophy #6).
- **Governance touchpoints.** A grant operates **within**, and is bounded by, the
  governance concerns the core defines — authentication, authorization,
  validation, auditability, safety controls, and policy enforcement (Philosophy
  #8). A Phase 4 grant never authors or overrides a Governance rule; the
  authoritative rules belong to Phase 1 Governance (DEC-019 / FIND-022) and no
  concrete policy is enumerated here.
- **Runtime vs Config-Time.** Grants may be issued or changed at runtime or
  through configuration / deployment policy (Philosophy #10); which mode applies
  is a per-grant attribute, not a rule set here.
- **Boundary notes / inherited flags.**
  - ↔ Phase 1 Governance (grants ≠ rules): Phase 4 grants capability to
    extensions; Phase 1 Governance authors the authoritative authorization rules
    that bound those grants. Referenced at altitude (DEC-019 / FIND-022); never
    authored here.
  - ↔ Phase 2: the Permission Matrix is the read-only experience projection of
    Governance rules onto personas/surfaces — it is not this grant model, and this
    grant model is not the matrix.
  - Q-014 (Permission Matrix population ↔ concrete Phase 1 Governance rules) is
    referenced, not resolved.
  - No inherited Phase 1 question is resolved here.

### Plugin Model
- **Definition.** The model for a **plugin**: a packaged unit that attaches
  extensions — channels, providers, or specialized integrations — to the core
  through the contract surface. Plugins are the packaging / attachment axis,
  distinct from domains (business responsibility) and capabilities (reusable
  functions), and a plugin *attaches* channels, providers, or specialized
  integrations (Philosophy #5, `extensibility-philosophy.md:17-20`). An
  intentional extension point (Philosophy #2).
- **Contract surface.** A plugin attaches and interacts only through the contract
  surface (APIs, events, permissions, schemas, versioned interfaces — Philosophy
  #4); it bundles one or more providers / channels / integrations and registers
  them through the contract, never through private internal state. Named at
  altitude; the concrete plugin manifest / registration schema is not specified.
- **Provider-agnostic note.** A plugin can bundle any swappable provider or
  channel behind the contract (Philosophy #6); the core depends on no specific
  plugin (Philosophy #3).
- **Governance touchpoints.** A plugin, and everything it attaches, must respect
  the core's governance — authentication, authorization, validation, auditability,
  safety controls, and policy enforcement (Philosophy #8) — at altitude; a
  plugin's grants follow the Permission grant model above, and the authoritative
  rules are Phase 1 Governance (DEC-019 / FIND-022), not enumerated here.
- **Runtime vs Config-Time.** Plugins may be enabled, disabled, or changed at
  runtime or through configuration / deployment policy (Philosophy #10); which
  mode applies is a per-plugin attribute.
- **Boundary notes / inherited flags.**
  - Within Phase 4: the Plugin Model is the *packaging / attachment* axis;
    Provider Model and Channel Model are *what* is attached. Distinct axes
    (Philosophy #5) — a plugin is not a provider and not a channel.
  - ↔ Phase 6: a plugin makes capabilities / providers *available* (order-free);
    when they run, in what order, is Phase 6 orchestration (selection-vs-sequence
    test).
  - ↔ Phase 7: the plugin attachment contract is Phase 4; the runtime that loads,
    enables, or disables plugins is Phase 7.
  - No inherited Phase 1 question is resolved here.

### Model
- **Definition.** The abstraction for an **AI model** as a swappable unit — a
  specific model (and tier) the system invokes through a provider. A Model is the
  unit an AI model provider supplies; the Provider Model is the general
  swappable-provider contract, and AI Model Routing (below) is the policy that
  selects among Models — kept as separate concerns. An intentional extension
  point (Philosophy #2): models change often and must be swappable. Backed by the
  multi-model principle (`ai-philosophy.md:18-19`, multiple model providers and
  model tiers).
- **Contract surface.** A Model is reached through the provider contract surface —
  the APIs, events, permissions, schemas, and versioned interfaces named by
  Extension Contracts (Philosophy #4) — named at altitude; a model exposes its
  capabilities and tier through that contract, not through private internal state.
  Not specified here.
- **Provider-agnostic note.** Models are swappable behind the contract (Philosophy
  #6; `ai-philosophy.md:18-19`): the system supports multiple model providers and
  tiers (paid / free / premium / fallback) without architectural rewrites, and the
  core depends on no specific model (Philosophy #3).
- **Governance touchpoints.** Model invocation must respect the core's governance
  — authentication, authorization, validation, auditability, safety controls, and
  policy enforcement (Philosophy #8, `extensibility-philosophy.md:29-30`) — at
  altitude; the authoritative rules are Phase 1 Governance (DEC-019 / FIND-022)
  and are not enumerated here.
- **Runtime vs Config-Time.** A model may be swapped at runtime (e.g. tier or
  fallback selection) or set through configuration / deployment policy (Philosophy
  #10); which mode applies is a per-model / per-binding attribute, not a rule set
  here (see the Runtime vs Config-Time Extensions framing section below).
- **Boundary notes / inherited flags.**
  - Within Phase 4: Model is the *unit*; Provider Model is the general provider
    contract it is supplied through; AI Model Routing is the *policy* that selects
    among Models — three distinct concerns (Model and AI Model Routing kept
    separate per the locked distinction set).
  - ↔ Phase 6: selecting *which* model by policy is routing (order-free, Phase 4 —
    see AI Model Routing); *when* a model runs within an ordered workflow is
    Phase 6.
  - ↔ Phase 7: the model contract is Phase 4; the AI Architecture that executes
    models is Phase 7.
  - Agent / subagent identity (registered open flag): agents/subagents that wrap
    models are likely Phase 7 AI Architecture (`experience-architecture.md:821`);
    not resolved here. **Scoped to Phase 7 per DEC-031** (un-deferred into Phase 7
    AI Architecture; defined in the Phase 7 content write).
  - No inherited Phase 1 question is resolved here.

### AI Model Routing
- **Definition.** The **policy-driven selection** mechanism that chooses among
  interchangeable models, providers, agents, and execution paths by policy — cost,
  quality, latency, availability, risk, and task type. It is the order-free
  selection layer over the Model and Provider abstractions; it is not a workflow.
  Backed by both philosophies: routing is part of extensibility (Philosophy #7,
  `extensibility-philosophy.md:25-27`) and model routing is a core architectural
  capability (`ai-philosophy.md:21-22`). An intentional extension point
  (Philosophy #2).
- **Contract surface.** Routing selects among contract-bound providers and models;
  it operates over the Extension Contracts surface (Philosophy #4) and the
  selection policy is named at altitude — the concrete routing-policy schema and
  engine are not specified (routing *execution* wiring is Phase 7).
- **Provider-agnostic note.** Routing operationalizes provider-agnosticism at run
  time (Philosophy #6; `ai-philosophy.md:18-19`, routing strategies across paid /
  free / premium / fallback): it selects among swappable providers and models
  without binding the core to any.
- **Governance touchpoints.** Routing decisions must respect the core's governance
  — authentication, authorization, validation, auditability, safety controls, and
  policy enforcement (Philosophy #8) — at altitude. "Risk" as a routing dimension
  *references* Governance / safety policy; it does not author it (authoritative
  rules are Phase 1 Governance, DEC-019 / FIND-022). No concrete policy is
  enumerated here.
- **Runtime vs Config-Time.** Routing may operate at runtime (dynamic selection)
  or be set through configuration / deployment policy (Philosophy #10; fallback
  options per `ai-philosophy.md:18-19`); the mode is an attribute, not a rule set
  here.
- **Boundary notes / inherited flags.**
  - ↔ Phase 6 (the sharpest line — the selection-vs-sequence test, verbatim): *"If
    it defines how the system selects among interchangeable providers / models /
    agents / execution paths by policy (cost, quality, latency, availability,
    risk, task-type) — the swappable, order-free selection mechanism — it is
    Phase 4. If it requires naming a predecessor, successor, gate, or
    step-sequence — what runs, in what order, with which hand-offs — it is
    Phase 6."* Routing is the Phase 4 side; orchestration — agent chains, approval
    gates, workflow runtime — is Phase 6.
  - Philosophy #7 refinement: `extensibility-philosophy.md:25` reads "routing and
    orchestration are part of extensibility"; per DEC-025, within the phase map
    orchestration is owned by Phase 6 and Phase 4 retains routing / selection only
    (registered philosophy-#7 annotation flag).
  - ↔ Phase 7: the routing policy is Phase 4; the engine that executes routing is
    Phase 7 AI Architecture.
  - Agent / subagent routing is in scope as *selection*; agent identity itself is
    likely Phase 7 (registered open flag), not resolved here. **Scoped to Phase 7
    per DEC-031** (routing/selection stays Phase 4; identity is Phase 7 AI
    Architecture).
  - No inherited Phase 1 question is resolved here.

### Runtime vs Config-Time Extensions
*Framing section (per DEC-025 / OQ-K) — it defines the cross-cutting attribute;
it is not an extension point on the six-field skeleton, and it does not enumerate
which extensions are runtime vs config-time (that is each entry's Runtime vs
Config-Time field).*

- **The attribute.** Extensibility supports both runtime and configuration-time
  evolution (Philosophy #10, `extensibility-philosophy.md:36-38`): some providers
  and execution paths are swappable **at runtime**, while other integrations and
  plugins are enabled, disabled, or changed through **configuration or deployment
  policy**.
- **Cross-cutting use.** Every extension-point entry records, in its *Runtime vs
  Config-Time* field, which mode(s) it supports. This is an **attribute** of the
  binding — analogous to the Phase 3 execution-mode attribute — not the
  deployment or governance policy that decides it.
- **What this section does not do.** It does not enumerate extensions or assign
  modes (that lives in each entry's field), and it does not author the deployment
  or governance policy that selects a mode — concrete deployment policy is Phase 7,
  and any governing rule is Phase 1 Governance (DEC-019 / FIND-022), referenced at
  altitude.
- **Boundary note.** Contract *evolution over time* (backward compatibility,
  Philosophy #11) is a distinct concern owned by the deferred Versioning &
  Compatibility sub-item, not by this attribute. No inherited Phase 1 question is
  resolved here.

---

### Feature Modules
- **Definition.** A **Feature Module**: a first-class, **mountable unit of product
  functionality** — a cohesive, base-mountable slice of the product — that mounts on the
  base and **may aggregate plugins**, declared to the core through the Extension Contracts
  surface. Per DEC-032 (Option A) it **composes** the Plugin Model and Extension Contracts
  and **never re-defines** either. Module-vs-plugin altitude line (DEC-032, verbatim): *"A
  plugin attaches a single extension — a channel, provider, or integration — to the core
  through the contract surface (the Plugin Model entry, `:273-284`). A Feature Module is a
  coarser-grained, mountable unit of product functionality that may aggregate plugins; it
  composes the Plugin Model and Extension Contracts, and never re-defines either."* An
  intentional extension point (Philosophy #2); the foreseen un-defer of the DEC-025
  deferral (Philosophy #12).
- **Contract surface.** A module declares and registers itself to the core **only**
  through the Extension Contracts surface (APIs, events, permissions, schemas, versioned
  interfaces — Philosophy #4); it aggregates one or more plugins / providers / channels and
  exposes them as a single mountable unit, never through private internal state. Named at
  altitude; the concrete module manifest / registration schema is not specified. The
  contract also carries the **Philosophy-#12 promotion hook** — the contract-level seam by
  which a widely-used, strategically-central module *could* be promoted into the
  configurable core; the actual promotion-to-core decision is a product / governance call
  (`extensibility-philosophy.md:43-45`), not Phase 4's per-module business decision and not
  authored here.
- **Provider-agnostic note.** A module composes whatever swappable plugins, providers, or
  channels it aggregates behind the contract (Philosophy #6); the core depends on no
  specific module (Philosophy #3).
- **Governance touchpoints.** A module, and everything it aggregates, must respect the
  core's governance — authentication, authorization, validation, auditability, safety
  controls, and policy enforcement (Philosophy #8) — at altitude; grants follow the
  Permission grant model above, and the authoritative rules are Phase 1 Governance
  (DEC-019 / FIND-022), not enumerated here.
- **Runtime vs Config-Time.** A module may be mounted, enabled, disabled, or updated at
  runtime or through configuration / deployment policy (Philosophy #10); which mode applies
  is a per-module attribute. The **mounting / running / composing mechanism** itself is
  Phase 7, not this attribute.
- **Boundary notes / inherited flags.**
  - Within Phase 4: a Feature Module is the *mountable product-unit* axis; the Plugin Model
    is the *attachment* axis and Provider / Channel Models are *what* is attached. A module
    composes plugins; it is not a plugin (DEC-032).
  - ↔ Phase 7: Phase 4 owns *what a module is / its contract*; the runtime that **mounts,
    runs, or composes** modules is Phase 7 — referenced, never defined here (DEC-031 G-6(c)).
  - ↔ Phase 8: the **assembled** set of mounted modules is the Phase 8 Plugins Layer
    (`Faraz-OS-Canon.md:144`); no assembled-layer content here.
  - No inherited Phase 1 question is resolved here.

---

## Deferred sub-items (flagged, not written)
These three remaining sub-items are deferred per DEC-025 and
carry flagged stubs only — no content this phase:
- **Versioning & Compatibility** — deferred per DEC-025 (Philosophy #11,
  backward compatibility). How extension contracts evolve over time; needs the
  core contract model first.
- **External Integrations** — deferred per DEC-025 (Philosophy #9,
  third-party-ready but internal-first; `non-goals.md:11`). The concrete
  channel/provider integration mechanics deferred from the Channel Model land
  here.
- **Future Domains** — carried, **marked-future placeholder; not silently
  resolvable** (DEC-025).

---

## Non-goals
Per DEC-025, `extensibility.md` does **not** contain: UI / surfaces / views /
portals / the Permission Matrix (Phase 2); ordered sequences, approval gates,
agent-chain orchestration, or workflow runtime (Phase 6); domain-entity
definitions, ownership, or authoritative meaning (Phase 1); authoritative
permission / authorization / policy rules (Phase 1 Governance); human identity
(Phase 1 Workforce); storage / retention / memory structure (Phase 5); data-paths
/ wiring / AI-Architecture implementation (Phase 7); capability *definitions*
(Phase 3); implementation technology — language, runtime, packaging, deployment
(build / handoff); build order / MVP sequencing (Phase 10); the deep content of
the four deferred sub-items; and the resolution of any inherited Phase 1 open
question.

---

## Open and inherited flags
Carried from DEC-025 / Snapshot-027 (some since resolved this normalization pass,
noted inline):
- **Agent / subagent identity** — likely Phase 7 AI Architecture
  (`experience-architecture.md:809` Workforce owns *human* identity; `:821` AI
  Architecture is the likely home of agent surfaces). **Resolved: scoped to Phase 7
  per DEC-031** (un-deferred into Phase 7 AI Architecture; defined in the content write).
- **Safety-controls vocabulary** — resolved (mapping): "safety controls"
  (`extensibility-philosophy.md:30`, Philosophy #8) is the same governance
  touchpoint category as Governance's "safety constraints / safety rules / Safety
  Constraint" (`domains.md:2191, :2228, :2264`) — a naming variance (Governance uses
  "control" / "constraint" interchangeably), not an altitude distinction. Philosophy
  #8's wording is preserved; the OQ-H "#8-only" provenance (`decisions.md:845`) stands.
- **Philosophy #7 annotation** — resolved (no Phase-0 edit): the refinement is
  already recorded at reference altitude — `extensibility-philosophy.md:25`
  ("routing and orchestration are part of extensibility") is read, within the phase
  map, as routing/selection only, with orchestration owned by Phase 6 (DEC-025 /
  DEC-028; see `extensibility.md:387-389`). Philosophy #7's wording is intentionally
  preserved (the principle stays a principle; the phase-map narrowing lives in the
  decision / consuming layer), so the immutable DEC quotes of #7 stay verbatim.
- **Inherited Phase 1 questions** — referenced, not resolved:
  `domains.md:1916-1917` (Intelligence vs Analytics/Reporting), `:1918` (when an
  insight becomes durable knowledge), `:1919-1920` (lead-scoring home), and Q-014
  (Permission Matrix ↔ Governance; since resolved, DEC-026).
- **Citation drift (FIND-028)** — resolved this normalization pass:
  inherited-question refs re-derived from ground truth; see findings.md.
