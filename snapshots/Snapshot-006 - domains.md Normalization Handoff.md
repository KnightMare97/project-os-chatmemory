# Snapshot-006 - domains.md Normalization Handoff

## Current Phase
Phase 1 Domain Discovery

## Current Topic
Normalization handoff preparation for `domains.md`

## Status
In Progress

`domains.md` remains the active source of truth for Phase 1 Domain Discovery.

The project has now moved far enough through domain discovery
that the next major step should be a dedicated normalization pass
rather than broad new expansion.

This does not mean all architectural questions are fully finalized.

It means the file is ready enough
that structural cleanup,
deduplication,
canonicalization,
and wording alignment
should become the main focus.

---

## Document Updates

### DOC-003 Draft
A normalization planning step has now been explicitly introduced
for `domains.md`.

The working direction is that normalization should be handled
as a dedicated pass,
not as scattered ad hoc edits during ongoing discovery.

### DOC-004 Draft
Normalization should be treated as a controlled architecture-editing task,
not as freeform rewriting.

The pass should preserve existing architectural intent,
canonical classifications,
and explicit draft boundaries.

### DOC-005 Draft
Because normalization is now structurally significant
and cross-cutting across many sections,
it should be executed later with AI assistance
through Claude Code,
with human review and approval,
rather than by manual broad editing alone.

---

## Decisions

### DEC-020 Draft
The next major step after current Phase 1 discovery work
is a dedicated normalization pass for `domains.md`,
not broad domain expansion.

This follows the existing Definition of Done direction
that once remaining work is mostly cleanup,
alignment,
deduplication,
and wording stabilization,
the file is ready for normalization.

### DEC-021 Draft
Normalization must preserve the canonical interpretation baseline already established in `domains.md`.

In particular,
the normalization pass must continue to respect the distinctions between:
- Domain
- Subdomain
- Bounded Context
- Entity
- Candidate Aggregate
- Memory Object
- Shared Service or Shared Service Artifact
- Business Artifact
- Domain Artifact
- Capability
- Workflow
- Plugin
- Provider

### DEC-022 Draft
Normalization must not silently finalize unresolved architectural boundaries.

Open questions such as:
- final Client Brain ownership
- final Brand placement
- final Service Agreement ownership
- final Aggregate boundaries
should remain visible as draft unless explicitly changed by a separate decision.

### DEC-023 Draft
Normalization should be delegated later to Claude Code
because this pass is likely to require:
- large-scale consistency review
- repeated cross-reference checking
- terminology alignment
- section-by-section comparison
- careful non-destructive editing

This reduces the chance of accidental concept drift
from manual cleanup by a non-specialist editor.

---

## Findings

### FIND-045
The file now has a stronger readiness basis for normalization
because Phase 1 already includes:
- a canonical classification layer
- explicit domain sections
- explicit boundary treatment for major client-context concepts
- explicit draft labeling through Assumption, Open Question, and Risk

### FIND-046
The main remaining work is increasingly document stabilization work,
including:
- repeated definition cleanup
- canonical wording consolidation
- heading consistency
- cross-reference consistency
- reducing duplicated explanations of key concepts

### FIND-047
Normalization is not the same as discovery.

Normalization should improve clarity and consistency
without inventing new architecture
or force-resolving still-draft boundaries.

### FIND-048
A human-guided but AI-assisted normalization pass
is now the safest operating model
because the task is broad,
tedious,
and structurally sensitive.

---

## Assumptions

- Assumption: `domains.md` remains the only active source of truth for Phase 1 domain modeling.
- Assumption: the next valuable work is normalization rather than broad architectural expansion.
- Assumption: Claude Code should later perform the normalization pass under explicit constraints.
- Assumption: human review remains required before accepting broad normalization edits.
- Assumption: unresolved draft concepts must remain unresolved unless separately decided.

---

## Risks

### R-012
If normalization is done manually through large ad hoc edits,
important distinctions may blur across:
- Client Brain
- Engagement Scope
- Service Agreement
- Brand
- CRM Client Account
- Client Success Relationship

### R-013
If Claude Code performs normalization without strict constraints,
it may accidentally:
- invent architecture
- collapse meaningful distinctions
- over-finalize draft concepts
- remove useful ambiguity markers

### R-014
If normalization is delayed too long,
`domains.md` may accumulate more duplicated wording,
repeated definitions,
and section inconsistency.

### R-015
If normalization removes open questions instead of preserving them,
later aggregate modeling may become less trustworthy rather than more stable.

---

## Open Questions

### Q-021
Should normalization produce only a cleaned `domains.md`,
or also a short change log summarizing what was consolidated and why?

### Q-022
Should Claude Code update `domains.md` directly,
or prepare a proposed normalized draft plus a review summary first?

### Q-023
Should a dedicated normalization checklist be added before Claude Code begins the pass?

---

## Next Focus
The next recommended focus is:

- prepare the normalization handoff for Claude Code
- define strict normalization constraints
- require preservation of canonical classifications
- require preservation of draft open questions and risks
- prefer minimal-diff cleanup over architectural redesign
- perform normalization on `domains.md` as a controlled pass with human review
