# Snapshot-004

## Current Phase
Phase 1 — Domain Discovery

## Current Topic
Candidate Entities / Aggregates per Domain

## Status
In Progress

---

## Document Structure Updates

### DOC-001
Phase 1 working drafts have been consolidated into:

- Faraz-OS-Canon/domains.md

This file is now the primary working source for:
- Ubiquitous Language
- Core Concepts
- Scope Object / Client Brain
- Context Map Draft
- Domain Discovery outputs

### DOC-002
Earlier Phase 1 draft files have been moved to:

- Faraz-OS-Canon/archive/

These archived files remain historical reference material,
but are no longer the primary source of truth.

---

## Context Corrections

### DEC-014 (Correction)
For Phase 1, the canonical working file is now:

- domains.md

not multiple parallel draft files.

This aligns the repository structure more closely
with Faraz-OS-Canon.md.

---

## Decisions

### DEC-015 (Draft)
The current Scope Object concept continues to be treated
as a transitional concept.

The preferred architectural direction remains:
- Client Brain
- Engagement Scope

This remains draft until:
- CRM relationship
- Brand relationship
- Service Agreement relationship
- Workforce relationship
- candidate entities and aggregates per domain

are clarified more precisely.

---

## Findings

### FIND-036
Phase 1 material has now been structurally consolidated
into a single working file: `domains.md`.

### FIND-037
The current Phase 1 source-of-truth structure is now clearer:
- Canon file defines the map
- domains.md holds the active domain discovery content
- archive holds superseded drafts

### FIND-038
Client Brain is currently best treated as:
- Memory Object
- Shared Service Artifact

pending deeper entity and aggregate analysis.

### FIND-039
Engagement Scope is currently best treated as:
- Memory Object
- Domain Artifact

pending deeper entity and aggregate analysis.

### FIND-040
The relationship between Client Brain / Engagement Scope
and the following domain concepts remains architecturally critical:
- CRM Client
- Brand
- Service Agreement
- Human Operator / Workforce

---

## Open Questions

### Q-013
What are the candidate Entities, Aggregates, and Bounded Contexts
for each Phase 1 Domain?

### Q-014
Should Brand be modeled as:
- its own Entity
- a child entity
- a client-scoped concept inside CRM
- a memory-scoped concept inside Client Brain

### Q-015
Is Service Agreement best owned by:
- CRM
- Client Success
- a separate bounded context

and how exactly does it constrain Engagement Scope?

### Q-016
Should assigned_human_operator_refs remain a simple reference field
inside Engagement Scope,
or evolve later into a more formal assignment artifact
connected to Workforce?

---

## Risks

### R-007
If domains.md remains only a copy-paste merge
without normalization,
internal duplication or inconsistent wording may persist
inside Phase 1 documentation.

### R-008
If Client Brain, Engagement Scope, CRM Client, Brand,
and Service Agreement are not separated clearly,
aggregate boundaries may become unstable later.

---

## Next Focus

Continue Phase 1 through domain-by-domain analysis,
starting with candidate:
- Entities
- Aggregates
- Bounded Contexts
- Responsibilities
- What it owns
- Inbound events
- Outbound events

for each domain,
starting with CRM.
