# Snapshot-003

## Current Phase
Phase 1 — Domain Discovery

## Current Topic
Client Brain / Engagement Scope Model

## Status
In Progress

---

## Context Corrections

### DEC-012 (Correction)
The active workstream should be tracked under:

Phase 1 — Domain Discovery

not:

Phase 2 — DDD Analysis

Reason:
According to Faraz-OS-Canon.md, both Ubiquitous Language and Scope Object / Client Brain belong to Phase 1 — Domain Discovery.

---

## Decisions

### DEC-013 (Draft)
The original Scope Object should be treated as a transitional concept, not as a standalone Domain.

The preferred direction is to reinterpret it as two separate architectural artifacts:

- Client Brain
- Engagement Scope

This remains draft until ownership, field groups, lifecycle, versioning, and update rules are defined more precisely.

## Language Status Note

The general Ubiquitous Language baseline is accepted.

However, the following client-context terms remain draft
until their model is specified more precisely:

- Scope Object
- Client Brain
- Engagement Scope

These terms must be revisited after defining:
- ownership
- field groups
- update authority
- lifecycle
- versioning

---

## Findings

### FIND-030
Scope Object is best understood as a structured, living, executable customer-context artifact rather than a Domain.

### FIND-031
Client Brain is the likely persistent client-level memory artifact used across services, workflows, and time.

### FIND-032
Engagement Scope is the likely service-level or project-level executable context for a package, campaign, deliverable set, or bounded engagement.

### FIND-033
Keeping all customer context inside one undifferentiated Scope Object would likely create:
- memory fragmentation
- domain confusion
- tighter workflow coupling

### FIND-034
The current best ownership direction is:

- Client Brain → Client Success + Knowledge
- Engagement Scope → Service Delivery

### FIND-035
Credentials, tokens, API keys, certificates, and client secrets should not be stored inside Client Brain or Engagement Scope.

Business memory artifacts may store only:
- non-sensitive metadata
- connection status
- secret references

Sensitive credentials must be handled by a dedicated Secrets Management subsystem.

---

## Open Questions

### Q-009
What is the concrete secrets architecture of Faraz OS?

This includes:
- where agency secrets are stored
- where client secrets are stored
- how secret references are modeled
- how runtime retrieval works
- how rotation is handled
- how revocation is handled
- how auditing is handled
- which agents, workflows, and services are allowed to access which secrets

### Q-010
Is Client Brain ultimately only a Memory Object, or will it also require aggregate-like ownership and consistency rules once its relation to Client, Brand, and Service Agreement is modeled more precisely?

### Q-011
What are the exact:
- field groups
- update authorities
- lifecycle rules
- versioning rules

for:
- Client Brain
- Engagement Scope

### Q-012
- Is Client Brain only a Memory Object,
  or will it also need aggregate-like ownership rules?
- What is the exact relationship between Client Brain and:
  - CRM Client
  - Brand
  - Service Agreement
- Should assigned_human_operator_refs remain a simple reference list,
  or evolve into a more formal assignment artifact through Workforce?

---

## Next Focus

Define the detailed model for:

- ownership
- field groups
- update authority
- lifecycle
- versioning

for:

- Client Brain
- Engagement Scope
