# Snapshot-005 - domains.md Stabilization Baseline

## Current Phase
Phase 1 Domain Discovery

## Current Topic
domains.md stabilization and classification baseline

## Status
In Progress

Phase 1 working content continues to be consolidated inside the active `domains.md` working file.

The current updated working draft is now reflected by:
- domain-draft-v3

This snapshot is a concise record of what changed,
why it changed,
and what should be treated as the current interpretation baseline.

---

## Decisions

### DEC-016 Draft
`domains.md` remains the canonical working source for Phase 1 Domain Discovery.

Earlier drafts and snapshots remain useful as historical reference,
but active interpretation should now follow the current working draft structure.

### DEC-017 Draft
`Canonical Classification Rules Draft v1` has been added to the working draft.

This section should now be treated as the default interpretation layer
for key architectural terms used across `domains.md`.

### DEC-018 Draft
The current working classification baseline is now:

- Domain = major business responsibility area
- Bounded Context = semantic boundary inside a Domain
- Entity = identity-bearing business object
- Candidate Aggregate = draft consistency boundary
- Memory Object = reusable structured memory artifact
- Shared Service / Shared Service Artifact = cross-domain reusable support artifact without owning business truth
- Business Artifact = important business object with unresolved final ownership or placement
- Domain Artifact = structured artifact aligned strongly to one Domain without final Entity/Aggregate commitment
- Capability = reusable business function across workflows, channels, or providers
- Workflow = executable business path
- Plugin = extension mechanism
- Provider = swappable execution option

### DEC-019 Draft
The current canonical direction for the most sensitive client-context concepts is now:

- Client = Entity in CRM
- Client Account = Entity or Candidate Aggregate in CRM
- Client Relationship = Entity or Candidate Aggregate in Client Success
- Client Brain = Memory Object and Shared Service Artifact direction
- Engagement Scope = Memory Object and Domain Artifact direction aligned to Service Delivery
- Human Operator = Entity in Workforce
- Service Agreement = Business Artifact with unresolved final ownership

These directions remain draft,
but should now be treated as the interpretation baseline
unless explicitly revised later.

---

## Findings

### FIND-041
The working draft is now more stable than earlier versions
because it contains an explicit classification layer
instead of relying only on local explanations inside each Domain section.

### FIND-042
The addition of canonical classification rules should reduce:
- duplicated definitions
- inconsistent wording
- concept drift
- cross-domain classification confusion

### FIND-043
`Boundary Decisions Draft v1` now has a stronger foundation
because the terms it depends on
such as Entity,
Memory Object,
Domain Artifact,
and Business Artifact
are now defined centrally.

### FIND-044
The current draft still contains meaningful unresolved boundaries,
but these are now more visible as explicit draft decisions
rather than hidden ambiguity.

---

## Open Questions

### Q-017
Should the older definitional material in earlier sections
be reduced later
so that `Canonical Classification Rules Draft v1`
becomes the single definitional source inside `domains.md`?

### Q-018
Should `Subdomain` receive a stronger and more explicit role in the file,
or should current modeling continue to rely mainly on Domain and Bounded Context?

### Q-019
When `Service Agreement` ownership is clarified,
should it remain only a Business Artifact
or evolve into a more explicit Entity, Aggregate, or Bounded Context placement?

### Q-020
Will `Client Brain` remain only a Memory Object direction,
or eventually require aggregate-like ownership rules in later phases?

---

## Risks

### R-009
If future additions ignore the canonical classification rules,
`domains.md` may drift back into inconsistent concept usage.

### R-010
If the canonical rules are duplicated in multiple places
instead of referenced,
the file may accumulate competing definitions again.

### R-011
If unresolved concepts such as `Service Agreement`,
`Client Brain`,
and `Engagement Scope`
are treated as finalized too early,
later aggregate modeling may become unstable.

---

## Next Focus

The next recommended focus is:

- normalize repeated definitions across `domains.md`
- keep one canonical definition for major client-context concepts
- clarify `Service Agreement` ownership and role
- continue Phase 1 through targeted boundary refinement
  rather than broad expansion
