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

This file is written in batches (DEC-025). **Batch A is landed:** the file
skeleton, the Provider Model and Channel Model entries, the deferred-sub-item
stubs, the non-goals, and the open/inherited flags. **Pending:** Batch B
(Extension Contracts, Permission, Plugin Model) and Batch C (Model, AI Model
Routing, Runtime vs Config-Time Extensions).

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

---

## Deferred sub-items (flagged, not written)
These four in-scope-for-Phase-4-overall sub-items are deferred per DEC-025 and
carry flagged stubs only — no content this phase:
- **Versioning & Compatibility** — deferred per DEC-025 (Philosophy #11,
  backward compatibility). How extension contracts evolve over time; needs the
  core contract model first.
- **External Integrations** — deferred per DEC-025 (Philosophy #9,
  third-party-ready but internal-first; `non-goals.md:11`). The concrete
  channel/provider integration mechanics deferred from the Channel Model land
  here.
- **Feature Modules** — deferred per DEC-025 (Philosophy #12, repeated extensions
  may become core).
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
Carried from DEC-025 / Snapshot-027; referenced, not resolved:
- **Agent / subagent identity** — likely Phase 7 AI Architecture
  (`experience-architecture.md:809` Workforce owns *human* identity; `:821` AI
  Architecture is the likely home of agent surfaces). Open cross-phase question.
- **Safety-controls vocabulary** — "safety controls" (`extensibility-philosophy.md:30`)
  vs Governance's "safety constraints / safety rules / Safety Constraint"
  (`domains.md:2189, :2226, :2262`); cross-doc alignment deferred to a later
  normalization pass.
- **Philosophy #7 annotation** — `extensibility-philosophy.md:25` ("routing and
  orchestration are part of extensibility") is read, within the phase map, as
  routing/selection only; orchestration is Phase 6. Optional doc annotation
  deferred to normalization.
- **Inherited Phase 1 questions** — referenced, not resolved:
  `domains.md:1915-1916` (Intelligence vs Analytics/Reporting), `:1917` (when an
  insight becomes durable knowledge), `:1918-1919` (lead-scoring home), and Q-014
  (Permission Matrix ↔ Governance).
- **Citation drift (FIND-028)** — prior inherited-question refs are off by one;
  alignment deferred to a normalization pass.
