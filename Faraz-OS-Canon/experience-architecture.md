# Experience Architecture — Phase 2

## Purpose
This file defines the human experience layer of Faraz OS.

It establishes the structural framework
for how humans interact with the system:
which personas exist,
what surfaces and portals they receive,
how they navigate,
what cross-domain information they see,
and how their experience differs per channel.

This file is canon for Phase 2.
It records the framework,
enumerates the firm inventory of concrete Operating Surfaces,
enumerates portal contents per persona,
enumerates the concrete Cross-Domain Views,
and defines the Navigation Model (surface-movement).
It does not populate the permission matrix.
Permission matrix population is deferred to later Phase 2 work.

---

## Status
Phase 2 scope is defined and human-confirmed
(see Snapshot-013 and DEC-019).

This file began as the framework canon of Phase 2 content
(Snapshot-014).
The Operating Surfaces section is populated
with the firm sixteen-surface inventory
and its canon-worthy rules
(see DEC-020 / Snapshot-016).
The Portals section enumerates
portal contents per persona,
as a membership and reuse-mode projection
of that inventory.
The Cross-Domain Views section now enumerates
the seven firm views and their canon-worthy rules
(see DEC-022 / Snapshot-019).
The Navigation Model section now defines
the surface-movement model
(see KNI-17 / Snapshot-023).
The Permission Matrix remains unpopulated.

No Phase 1 domain truth,
ownership,
or boundary is changed by this file.
Phase 2 references Phase 1; it does not reinterpret it.

---

## Scope

### What Phase 2 owns
Phase 2 designs the human experience layer
for all human personas of Faraz OS.

Phase 2 owns:
- where humans interact (surfaces, portals)
- to whom interaction is exposed (personas)
- how humans move between views (navigation)
- how multi-domain information is presented to humans (cross-domain views)
- how human experience differs per channel (channel behaviors)
- how persona-to-surface exposure is projected from Governance rules (permission matrix)

### What Phase 2 references but does not own
- human identity → Phase 1 Workforce
- authoritative permission and authorization rules → Phase 1 Governance
- reusable functional abilities → Phase 3 Capability Map
- channel integration and technical channel model → Phase 4 Extensibility
- ordered cross-step flow and approval gates → Phase 6 Workflow Design
- AI / agent-facing surfaces → Phase 7 (likely; see deferred items)
- positioning in the system puzzle board → Phase 8 Puzzle Board Architecture

### What Phase 2 does not cover
Phase 2 is strictly human experience.
AI / agent-facing surfaces are not Phase 2.

Phase 2 does not author rules,
does not own data,
does not define capabilities,
and does not sequence workflows.

---

## Governing Boundary Test
Phase 2 uses one canonical altitude test
to decide whether a concern belongs here:

- Presentation / surface / navigation / human interaction → Phase 2
- Reusable functional ability (UI-independent) → Phase 3 Capability Map
- Ordered cross-step flow and approval gates → Phase 6 Workflow Design

Secondary references:
- Human identity → Phase 1 Workforce
- Permission and authorization rules → Phase 1 Governance
- Channel integration and extension grants → Phase 4 Extensibility
- AI / agent-facing surfaces → Phase 7 System Architecture Blueprint (AI Architecture)
- Experience layer position in the puzzle board → Phase 8

This test governs every sub-item below.
When a concern fails the test,
it does not belong in Phase 2.

---

## Personas

### Definition
A Persona is a Phase 2 experience archetype,
expressed as a role-group
that receives a portal and a set of surfaces.

Persona is distinct from Workforce identity.
Workforce identity is owned by Phase 1.
Phase 2 references Workforce identities;
it never owns them.

### Locked persona set
The following personas are the canonical Phase 2 set:

- Client (external)
- Contractor (external)
- Workforce / Operator (internal)
- Manager (internal)
- System Administrator (internal; manages workflows, credentials, configuration)
- Future Personas (placeholder)

Contractor and Workforce / Operator are distinct personas
with distinct portals and surfaces.
Contractor is a scoped external view.
Workforce / Operator has full internal surfaces.

Client is a single persona for now.
Client sub-personas (for example, client admin and client viewer)
are not designed in this pass and belong to the Future Personas placeholder.

### Future Personas placeholder
Future Personas is an explicit deferred slot
for personas that are not yet designed,
including client sub-personas
and other future humans of the system.

It is carried forward intentionally
and must not be silently resolved.

---

## Operating Surfaces

### Definition
An Operating Surface is a functional workspace
through which a human persona performs work.

An Operating Surface is reusable across portals.
The same surface may appear inside more than one portal
when more than one persona has legitimate access to it.

### What Operating Surfaces are not
- They are not capabilities.
  Capabilities are reusable functional abilities owned by Phase 3.
- They are not workflows.
  Ordered cross-step flow belongs to Phase 6.
- They are not UI components or visual designs.
  Visual design (colors, components, styling) is out of Phase 2.

### Granularity Rule
Operating Surfaces are sized at
one surface per coherent work-mode,
not one per task type.

A surface corresponds to a mode of work
a persona enters,
not to each individual action taken inside it.
This keeps surfaces at presentation altitude
and prevents the inventory from fragmenting
into per-task or per-domain explosion.

### Naming Convention
Persona-facing surfaces are persona-prefixed.
The prefix names the persona who operates the surface
(for example, Client Notifications,
Client Approval Queue, Contractor Assignments).
Wherever a persona word such as "Client" appears as a prefix,
it carries the persona meaning,
not the subject being viewed.

Subject-facing surfaces use distinct subject words
rather than persona names.
For example, the operator's current-client memory workspace
is the Client Brain Surface
(anchored on the Phase 5 Knowledge & Memory concept of Client Brain),
not "Client Context Surface,"
so that "Client" is never overloaded between
the persona doing the work
and the subject the work is about.

### Persona Reuse Vocabulary
An Operating Surface can be exposed to more than one persona.
Each surface↔persona relationship is described
with one of four reuse modes:

- **Full** — the same surface, with the same content.
- **Scoped** — the same surface, with restricted content.
- **Distinct surface** — a different surface serves the
  same intent for that persona, and is added to the inventory
  as its own entry (not a persona-specialized variant of a parent).
- **—** — no access.

#### Scoped marker placement
Phase 2 records "Scoped" as a property
of the surface↔persona relationship.
Phase 2 does not author the rules
that decide what content is restricted.
Those rules come from Phase 1 Governance
and are projected onto the experience layer
through the Permission Matrix,
whose population is deferred
until the Governance rules are concrete.

### Surface Inventory
The following sixteen Operating Surfaces are the firm inventory
for Phase 2, defined and human-confirmed
(see DEC-020 / Snapshot-016).
Each row names the surface, its primary persona,
and the reuse pattern across other personas.
Five additional surfaces remain flagged and deferred;
they are carried in Open and Deferred Items, not here.

| # | Surface | Primary persona | Reuse pattern |
|---|---------|-----------------|---------------|
| 1 | Operator Inbox | Operator | Manager Full; Client → Distinct (*Client Notifications*) |
| 2 | Production Workspace | Operator | Contractor Scoped (own engagement) |
| 3 | Review Queue | Operator | Manager Full; Client → Distinct (*Client Approval Queue*) |
| 4 | Client Brain Surface | Operator | Manager Full; Contractor Scoped (assigned client) |
| 5 | Knowledge Workspace | Operator | Manager Full; Contractor Scoped (engagement-relevant); System Administrator → Distinct (*Admin Knowledge*) |
| 6 | Agent & Workflow Monitor | Operator | Manager Full or Scoped; System Administrator Full |
| 7 | Reports & Analytics Surface | Operator | Manager Full; Contractor Scoped; Client Scoped — hosts four Cross-Domain Views (Performance & Analytics, Team Oversight, Engagement Health, Client Engagement Summary); see Cross-Domain Views |
| 8 | Lead Workspace | Operator | Manager Full; Contractor — |
| 9 | Client Notifications | Client | — |
| 10 | Client Approval Queue | Client | — |
| 11 | Client Deliverable Library | Client | — |
| 12 | Client Billing / Invoices Surface | Client | — (Finance owns the data; this is presentation) |
| 13 | Contractor Assignments | Contractor | — |
| 14 | Admin Knowledge | System Administrator | — |
| 15 | Workflow & Agent Configuration | System Administrator | — |
| 16 | Credentials & Integrations | System Administrator | references Phase 4 (provider/channel/model) and Phase 1 Governance (policy touchpoints) |

The reuse patterns above are a Phase 2 surface property.
They are not the populated Permission Matrix.
The authoritative persona-to-surface projection
still awaits concrete Phase 1 Governance rules
and is deferred (see the Permission Matrix section).

The inventory references other phases at reference altitude only,
without reinterpreting their ownership:
Client Brain Surface anchors on Phase 5 Knowledge & Memory;
Lead Workspace anchors on the CRM domain (Phase 1);
Client Billing / Invoices Surface presents Finance-owned data (Phase 1);
Credentials & Integrations references Phase 4 extensibility
(provider / channel / model) and Phase 1 Governance policy touchpoints.

### Scope of definition in this file
This file defines the Operating Surface concept,
the granularity rule, the naming convention,
the persona reuse vocabulary,
and the firm inventory of sixteen surfaces above.

It does not populate the Permission Matrix.
Portal contents per persona and Cross-Domain Views
are defined in their own sections, not here.
The remaining flagged surfaces stay flagged
in Open and Deferred Items
and must not be silently resolved.

---

## Portals

### Definition
A Portal is the visual panel a persona group receives.

A Portal contains Operating Surfaces.
There is one portal definition per persona group.

### Composition for multi-role humans
A human who carries more than one role
receives one composed portal,
not multiple separate portals.

The composed portal is the union of role-scoped surface entitlements
for that human.
Identity-to-portal is role-based composition.

### What Portals are not
- A Portal is not a Workforce identity.
- A Portal is not a workflow.
- A Portal is not an integration boundary.
  Channel integration belongs to Phase 4.

### Portal Contents per Persona
This section enumerates, for each locked persona,
the Operating Surfaces its portal contains
and the reuse mode for each.
It is a projection of the firm Operating Surfaces inventory
(see DEC-020 / Snapshot-016 and the Operating Surfaces section above).
It is built from the sixteen firm surfaces only;
the five flagged surfaces are noted as pending where relevant
and are not added.

The reuse mode column uses the persona reuse vocabulary
defined in the Operating Surfaces section
(Full / Scoped / Distinct surface / —).

#### Operator portal

| Surface | Reuse mode | Note |
|---------|------------|------|
| Operator Inbox | Full | primary persona |
| Production Workspace | Full | primary persona |
| Review Queue | Full | primary persona |
| Client Brain Surface | Full | primary persona |
| Knowledge Workspace | Full | primary persona |
| Agent & Workflow Monitor | Full | primary persona |
| Reports & Analytics Surface | Full | hosts the Performance & Analytics and Engagement Health views (see Cross-Domain Views) |
| Lead Workspace | Full | primary persona |

#### Manager portal

| Surface | Reuse mode | Note |
|---------|------------|------|
| Operator Inbox | Full | |
| Review Queue | Full | |
| Client Brain Surface | Full | |
| Knowledge Workspace | Full | |
| Agent & Workflow Monitor | Full or Scoped | |
| Reports & Analytics Surface | Full | hosts the Performance & Analytics, Team Oversight, and Engagement Health views (see Cross-Domain Views) |
| Lead Workspace | Full | |

Projection note: the Manager portal does not include Production Workspace.
The inventory assigns that surface to Operator (Full) and Contractor (Scoped) only.
This is a faithful projection of the inventory, not a new exclusion decision.
The former *Team Performance / Oversight Surface* flag is resolved
(DEC-022) to the Team Oversight View, a Cross-Domain View hosted on
the Manager's Reports & Analytics Surface — not a standalone surface.

#### Contractor portal

| Surface | Reuse mode | Note |
|---------|------------|------|
| Contractor Assignments | Full | primary persona |
| Production Workspace | Scoped | own engagement |
| Client Brain Surface | Scoped | assigned client |
| Knowledge Workspace | Scoped | engagement-relevant |
| Reports & Analytics Surface | Scoped | |

Projection note: the Contractor portal does not include Lead Workspace
(inventory: "Contractor —"), Operator Inbox, or Review Queue.

#### Client portal

| Surface | Reuse mode | Note |
|---------|------------|------|
| Client Notifications | Full | primary persona |
| Client Approval Queue | Full | primary persona |
| Client Deliverable Library | Full | primary persona |
| Client Billing / Invoices Surface | Full | primary persona; Finance owns the data |
| Reports & Analytics Surface | Scoped | hosts the Client Engagement Summary View (see Cross-Domain Views) |

Pending / flagged: *Client Profile* — tentative; not added.

#### System Administrator portal

| Surface | Reuse mode | Note |
|---------|------------|------|
| Admin Knowledge | Full | primary persona |
| Workflow & Agent Configuration | Full | primary persona |
| Credentials & Integrations | Full | primary persona |
| Agent & Workflow Monitor | Full | |

Pending / flagged: *System Configuration / Settings* — not added.

#### Future Personas
Future Personas carry no portal contents in this pass.
The placeholder is carried forward and not designed here.

#### Multi-role composition
A human who carries more than one role
receives one composed portal,
per the persona-to-portal rule above.
The composed portal is the union of the per-persona memberships
listed in this section.
Resolving the effective reuse mode
when the same surface is reached through more than one role
is a Permission Matrix concern and remains deferred.

#### Boundary note
Portal membership here is derived from the inventory's reuse markers.
It is not the populated Permission Matrix.
The authoritative per-surface entitlement projection,
and the resolution of reuse mode across multiple roles,
come from Phase 1 Governance rules
and are projected via the Permission Matrix,
whose population is deferred until those rules are concrete.

### Scope of definition in this file
This file defines the Portal concept and the persona-to-portal rule,
and enumerates portal contents per persona
at membership and reuse-mode altitude.

It does not order, group, or assign a landing surface
within a portal,
does not populate the Permission Matrix,
and does not resolve multi-role reuse-mode overlap.
The five flagged surfaces remain flagged
in Open and Deferred Items
and must not be silently resolved.

---

## Navigation Model

### Definition
The Navigation Model describes how a persona moves
between the Operating Surfaces available
within that persona's composed portal.

### Scope in this pass
The Navigation Model stays at surface-movement level.
It defines movement between surfaces inside a portal,
nothing deeper in this pass.

### Movement model
- Flat peer movement.
  Within a persona's composed portal,
  the Operating Surfaces are navigable peers.
  The persona moves directly between them
  with no prescribed order and no gate between surfaces.
- Within-surface views.
  Where an Operating Surface hosts Cross-Domain Views
  (for example, the Reports & Analytics Surface),
  the persona reaches those views within the host surface.
  A view is not a separate portal entry (DEC-022);
  reaching it is movement within its host surface.
- Composed-portal navigation.
  A multi-role human navigates across the union of surfaces
  in the single composed portal
  (per the persona-to-portal rule),
  not across separate portals.
- Within own portal only.
  A persona does not navigate into another persona's portal.

This model is uniform.
It applies to each persona's composed portal
over whatever surfaces that portal contains
(see Portal Contents per Persona);
it does not restate the per-persona surface lists.

### What the Navigation Model does not decide
- It does not assign an entry or landing surface,
  and it does not order or group surfaces within a portal.
  Landing-surface designation is a marked future item,
  consistent with the Portals section.
- It does not decide who may reach a surface.
  Entitlement is a Permission Matrix concern and remains deferred.
  Navigation describes movement, not permission.
- Contextual item-level navigation
  (moving from a list or entry surface
  to a specific item's surface)
  is deep-linking, a deferred sub-detail;
  it is not populated here.

### Deferred future sub-detail
Notification routing, deep-linking,
and landing-surface designation
are deferred Phase 2 sub-detail.

They are carried as marked future items
and must not be silently resolved here.

### What Navigation is not
- It is not workflow orchestration.
  Ordered cross-step flow and approval gates belong to Phase 6.
- It is not channel integration.
  Channel integration belongs to Phase 4.
- It is not the Permission Matrix.
  Entitlement (who may reach a surface) is deferred.

### Scope of definition in this file
This file defines the surface-movement model
for each persona's composed portal.

It does not assign a landing surface,
order or group surfaces within a portal,
populate the Permission Matrix,
or decide entitlement.

---

## Permission Matrix

### Three-altitude separation
Permission concerns sit at three distinct altitudes
across the phase map:

- Phase 1 Governance owns authoritative permission,
  authorization, and policy rules
  as the system source of truth.
  Governance is explicitly not a UI permission table.
- Phase 4 Extensibility owns extension, plugin, and provider
  capability grants via contracts.
- Phase 2 owns the read-only experience projection
  of Governance rules onto the experience layer.

### What the Phase 2 Permission Matrix is
The Phase 2 Permission Matrix is a read-only projection.
It expresses which personas are exposed to which surfaces,
portals,
and views.

- Rows = personas
- Columns = surfaces / portals / views

The matrix columns are surfaces, portals, and views.
The matrix columns are not capabilities.
Capabilities belong to Phase 3,
and using them as columns would collapse the boundary.

### What the Permission Matrix is not
- It is not a rule store.
  Phase 2 authors no permission or authorization rules.
- It is not an extension grant model.
  Extension and plugin grants belong to Phase 4.
- It is not a Workforce identity model.
  Identity belongs to Phase 1.

### Scope of definition in this file
This file defines the matrix structure and altitude.
It does not populate matrix rows and columns.
Population requires concrete surfaces and Governance rules
and is a later refinement.

---

## Cross-Domain Views

### Definition
A Cross-Domain View is a persona-facing presentation
that composes information from multiple domains
onto a single surface for a human.

### What Cross-Domain Views are
Cross-Domain Views are presentation and composition.
They consume multi-domain information for the human.

### What Cross-Domain Views are not
- They do not own domain data.
  Domain data ownership belongs to Phase 1.
- They do not compute the underlying values.
  Computation belongs to Phase 3.

### KPI altitude split
For metrics and KPIs that appear on dashboards:

- KPI computation is Phase 3.
- The dashboard surface that displays the computed KPI is Phase 2.

The altitude rule is presents / computes / owns,
held in that order across Phase 2, Phase 3, and Phase 1.

### Granularity Rule
Cross-Domain Views are sized at
one view per coherent persona decision-context,
composed from a stable domain-set.

A view corresponds to a decision or oversight question
a persona is trying to answer
(for example, "understand this client",
"oversee the team", "read performance"),
not to each individual metric or domain slice.
This keeps views at presentation altitude
and prevents the inventory from fragmenting
per domain-combination or per KPI cluster.

### Naming Convention
Cross-Domain Views are named by their decision-context or subject,
with a "View" suffix (for example, Client Brain View,
Team Oversight View, Engagement Health View).
A persona word is used only when the composition
is persona-specific (for example, Client Engagement Summary View).

### Surface and View relationship
A Cross-Domain View is a named multi-domain composition
rendered on an Operating Surface.
A single Operating Surface may host more than one view.
A view is not itself a portal entry;
the host surface is the portal entry,
and the view is the composition it presents.

### View Inventory
The following seven Cross-Domain Views are the firm inventory
for Phase 2, defined and human-confirmed
(see DEC-022 / Snapshot-019).
Each row names the view, the persona decision-context it serves,
the domains it composes, its host Operating Surface,
and its primary persona.

| # | View | Decision-context | Domains composed | Host surface | Primary persona |
|---|------|------------------|------------------|--------------|-----------------|
| 1 | Client Brain View | understand this client | Client Brain (Phase 5) + CRM + Service Delivery + Client Success + Finance + Brand | Client Brain Surface | Operator (Manager full; Contractor scoped) |
| 2 | Lead Context View | understand this lead | CRM + Intelligence (lead scoring) + Client Success | Lead Workspace | Operator (Manager full) |
| 3 | Performance & Analytics View | read performance | Intelligence + Finance + Service Delivery + CRM | Reports & Analytics Surface | Operator / Manager (Contractor / Client scoped) |
| 4 | Team Oversight View | oversee the team | Workforce + Service Delivery + Client Success + Intelligence | Reports & Analytics Surface (manager scope) | Manager |
| 5 | Engagement Health View | is this engagement healthy / profitable? | Service Delivery + Finance + Client Success + Workforce | Reports & Analytics Surface (operator / manager scope) | Operator / Manager |
| 6 | Client Engagement Summary View | how is my engagement going? | Service Delivery + Finance + Client Success | Reports & Analytics Surface (client-scoped) | Client |
| 7 | Contractor Assignment-in-Context View | my assigned work in context | Workforce + Service Delivery + Client Brain (scoped) + Knowledge | Contractor Assignments | Contractor |

The **Reports & Analytics Surface hosts four distinct views**
— the Performance & Analytics View, the Team Oversight View,
the Engagement Health View, and the Client Engagement Summary View —
kept separately named so the compositions do not collapse
into one.

System Administrator has no Cross-Domain View.
The System Administrator surfaces are configuration and management
at single-domain Governance / Extensibility altitude,
not multi-domain human compositions.

The inventory references other phases at reference altitude only,
without reinterpreting their ownership.
Views consume multi-domain information;
they do not own it (Phase 1) or compute it (Phase 3).
The altitude rule is presents / computes / owns.
The Intelligence domain (Phase 1) owns derived insights and scores
as source of truth, while Phase 3 owns computation;
a Cross-Domain View consumes those outputs
and does not resolve that Phase 1 / Phase 3 boundary,
which is upstream of Phase 2.
Which personas are exposed to which view
is not decided here; entitlement is deferred
to the Permission Matrix (see that section).

### Flag resolutions
Two previously flagged Operating Surfaces are resolved here:

- **Reports & Analytics Surface → both.**
  It remains the firm Operating Surface from DEC-020 (unchanged)
  and hosts two Cross-Domain Views
  (the Performance & Analytics View and the Team Oversight View).
- **Team Performance / Oversight Surface → pure Cross-Domain View.**
  It is the Team Oversight View,
  hosted on the Manager's Reports & Analytics Surface.
  It is not a standalone Operating Surface
  and is removed from the flagged-surface list.

### Host assignments
The host surfaces for the Engagement Health View
and the Client Engagement Summary View are resolved (DEC-023)
by scoped reuse — both are hosted on the Reports & Analytics Surface
(no new Operating Surface was added).

The operator-finance gap (DEC-020) is resolved (DEC-023)
for the per-engagement financial-context need:
the operator reaches engagement revenue (Finance),
contractor payment and effort (Workforce),
delivery (Service Delivery), and health (Client Success)
through the Engagement Health View
on the Reports & Analytics Surface,
a surface the operator already holds.
A later cross-engagement financial-rollup need,
if one surfaces, is a new item — not a reopening of this gap.

### Scope of definition in this file
This file defines the Cross-Domain View concept,
the granularity rule, the naming convention,
the surface-and-view relationship,
and the firm inventory of seven views above.

It does not populate the Permission Matrix,
decide the deferred host surfaces,
or assign which personas are entitled to which view.
Entitlement remains deferred to the Permission Matrix.

---

## Channel Behaviors

### Definition
Channel Behaviors describe how the human experience
differs across channels.

In Phase 2, Channel Behaviors are narrowly scoped to:

- rendering differences per channel
- preview behavior per channel
- notification user experience per channel

### What Channel Behaviors are not
- They are not channel integration.
  Channel integration and the technical channel model belong to Phase 4.
- They are not workflow.
  Ordered cross-step flow belongs to Phase 6.

Channel Behaviors in Phase 2 stay on the human-experience side
of the boundary.

---

## Non-Goals
Phase 2 explicitly does not cover the following:

- AI / agent-facing surfaces → Phase 7 (likely; see deferred items)
- authoring permission or authorization rules → Phase 1 Governance
- defining capabilities → Phase 3 Capability Map
- workflow orchestration and approval-gate sequencing → Phase 6 Workflow Design
- channel integration and the technical channel model → Phase 4 Extensibility
- owning domain data or human identity → Phase 1
- visual or brand design system (pixels, components, styling)
- actual screen or UI implementation → later build phases (Phase 10 roadmap)

These non-goals are explicit
and must not be silently absorbed into Phase 2 later
without an explicit decision.

---

## Open and Deferred Items

### Open Question — AI / agent-surface home
Q-013 (deferred, repo-only):
the exact home of AI / agent-facing surfaces
between Phase 7 System Architecture Blueprint (AI Architecture)
and Phase 8 AI Layer.

This is not blocking Phase 2.
It is carried in `open-questions.md` as a deferred item.

### Deferred — Future Personas
Future Personas is carried as an explicit placeholder
inside the Personas section.
It is not designed in this pass.

### Deferred — Navigation sub-detail
Notification routing, deep-linking,
and landing-surface designation
are carried as deferred sub-detail of the Navigation Model.
They are not designed in this pass.

### Deferred — Concrete enumeration
The following enumerations are deferred to later Phase 2 refinement:

- populated permission matrix rows and columns

This item requires additional explicit decisions
and must not be introduced silently.

The firm Operating Surfaces inventory
is no longer deferred; it is enumerated
in the Operating Surfaces section above.
Portal contents per persona are likewise no longer deferred;
they are enumerated in the Portals section above.
The Cross-Domain Views are likewise no longer deferred;
they are enumerated in the Cross-Domain Views section above.

### Flagged — Operating Surfaces carried forward
Three Operating Surfaces are flagged, not firm,
and are deferred until a separate explicit decision.
They must not be silently resolved into the firm inventory:

- **Client Profile** (Client persona) — tentative;
  needs later confirmation that it is a real surface
  and not absorbed by other Client-persona surfaces.
- **System Configuration / Settings** (System Administrator) —
  depends on Phase 4 Extensibility / Phase 9 Infrastructure maturity
  before its real shape can be named.
- **Onboarding / first-time-use surfaces** — none named
  for any persona; may be a Phase 2 oversight or out of scope; defer.

The previously flagged *operator-finance gap* is resolved
(DEC-023) for the per-engagement financial-context need:
the operator reaches engagement financial context through
the Engagement Health View on the Reports & Analytics Surface
(no new Operating Surface was added).
A later cross-engagement financial-rollup need,
if one surfaces, is a new item — not a reopening of this gap.

The previously flagged *Team Performance / Oversight Surface*
is resolved (DEC-022): it is the Team Oversight View,
a Cross-Domain View hosted on the Manager's
Reports & Analytics Surface — not a standalone surface.

Informational (FIND-024):
the System Administrator surface count is growing
(Admin Knowledge, Workflow & Agent Configuration,
Credentials & Integrations, plus full reuse of
Agent & Workflow Monitor, plus the flagged
System Configuration / Settings).
This is defensible because admin work is genuinely multi-headed,
but it is a potential later refactor candidate.
Informational only; no action in this pass.

---

## Cross-Phase References

- Phase 1 Domain Discovery (`domains.md`):
  Workforce owns human identity;
  Governance owns permission, authorization, and policy rules
  and is not a UI permission table.
- Phase 3 Capability Map (`capabilities.md`):
  owns reusable functional abilities and KPI computation.
- Phase 4 Extensibility Model (`extensibility.md`):
  owns extension contracts, plugin and provider models,
  channel integration, and extension capability grants.
- Phase 6 Workflow Design (`workflows.md`):
  owns ordered cross-step flow and approval gates.
- Phase 7 System Architecture Blueprint
  (`system-architecture-blueprint.md`):
  AI Architecture is the likely home of AI / agent-facing surfaces.
- Phase 8 Puzzle Board Architecture (`architecture.md`):
  positions the Experience Layer in the puzzle board.

---

## Risks Carried Forward

### R-023 (active, reduced)
Phase 2 risks drifting into Phase 3 Capability Map
or Phase 6 Workflow Design territory.

Mitigation in this file:
each sub-item section names what it is not
and refers to the governing boundary test.

Partial mitigation added with the Operating Surfaces population:
the granularity rule, the naming convention,
the persona reuse vocabulary,
and the rename of "Workflow Control Panel"
to "Agent & Workflow Monitor"
all sharpen the Phase 2 / Phase 3 / Phase 6 altitude marker.

This risk stays active
until Phase 2 content matures and the boundary holds in practice.

---

## Provenance
Scope and definitions in this file derive from:

- DEC-019 in `snapshots/Snapshot-013 - Phase 2 Experience Architecture Scope Defined.md`
- the scoping capture in
  `brainstorms/2026-06-05-phase-2-experience-architecture.md`
- DEC-020 in
  `snapshots/Snapshot-016 - Phase 2 Operating Surfaces Scope Defined.md`
  (the Operating Surfaces inventory and canon-worthy rules)
- the scoping capture in
  `brainstorms/2026-06-06-phase-2-operating-surfaces.md`
- portal contents per persona derive from the DEC-020 inventory
  and the persona-to-portal rule (DEC-019),
  produced under plan → build → review
  and recorded in DEC-021 / Snapshot-018
- the Cross-Domain Views inventory and rules derive from DEC-022,
  recorded in Snapshot-019 and captured in
  `brainstorms/2026-06-06-phase-2-cross-domain-views.md`
- the Cross-Domain View host assignments
  (Engagement Health View and Client Engagement Summary View
  on the Reports & Analytics Surface)
  and the operator-finance gap resolution
  derive from DEC-023, recorded in Snapshot-021
- the Navigation Model derives from composing over the
  Operating Surfaces inventory (DEC-020)
  and the Portal Contents (DEC-021),
  per KNI-17, recorded in Snapshot-023
- the Phase 2 sub-item list in `Faraz-OS-Canon.md`
- Phase 1 references in `Faraz-OS-Canon/domains.md`

No Phase 1 domain truth was modified by this file.
