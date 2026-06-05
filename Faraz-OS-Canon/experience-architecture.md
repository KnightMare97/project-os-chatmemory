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
It records the framework only.
It does not enumerate concrete surfaces,
populate the permission matrix,
or design specific portal contents.
Those refinements are deferred to later Phase 2 work.

---

## Status
Phase 2 scope is defined and human-confirmed
(see Snapshot-013 and DEC-019).

This file is the first canon write of Phase 2 content.

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

### Scope of definition in this file
This file defines the Operating Surface concept.
It does not enumerate concrete surfaces.
Concrete surfaces are introduced as later Phase 2 refinements.

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

### Scope of definition in this file
This file defines the Portal concept and the persona-to-portal rule.
It does not enumerate portal contents per persona.
Per-persona portal composition is a later Phase 2 refinement.

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

### Deferred future sub-detail
Notification routing and deep-linking
are deferred Phase 2 sub-detail.

They are carried as a marked future item
and must not be silently resolved here.

### What Navigation is not
- It is not workflow orchestration.
  Ordered cross-step flow belongs to Phase 6.
- It is not channel integration.
  Channel integration belongs to Phase 4.

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

Example of the intent (not an enumeration of concrete views):
- a manager view that composes information from CRM,
  Service Delivery,
  and Finance

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
Notification routing and deep-linking
are carried as a deferred sub-detail of the Navigation Model.
They are not designed in this pass.

### Deferred — Concrete enumeration
The following enumerations are deferred to later Phase 2 refinement:

- concrete Operating Surfaces by name
- portal contents per persona
- populated permission matrix rows and columns
- concrete Cross-Domain Views by name

These items require additional explicit decisions
and must not be introduced silently.

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

This risk stays active
until Phase 2 content matures and the boundary holds in practice.

---

## Provenance
Scope and definitions in this file derive from:

- DEC-019 in `snapshots/Snapshot-013 - Phase 2 Experience Architecture Scope Defined.md`
- the scoping capture in
  `brainstorms/2026-06-05-phase-2-experience-architecture.md`
- the Phase 2 sub-item list in `Faraz-OS-Canon.md`
- Phase 1 references in `Faraz-OS-Canon/domains.md`

No Phase 1 domain truth was modified by this file.
