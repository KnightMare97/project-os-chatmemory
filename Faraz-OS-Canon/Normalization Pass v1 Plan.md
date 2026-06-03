# Normalization Pass v1 Plan

## Purpose
This file defines the scope of Normalization Pass v1
for Phase 1 Domain Discovery.

The goal is to stabilize `domains.md`
without reopening broad discovery
and without inventing new architecture.

---

## In Scope
Normalization Pass v1 may do the following:

- remove duplicated definitions
- keep one canonical definition for major architectural terms
- align wording across Domain sections
- normalize repeated section naming patterns
- consolidate repeated cross-domain concept explanations
- reduce structural inconsistency
- improve readability and reference flow
- preserve explicit Assumption, Open Question, and Risk labels

---

## Out of Scope
Normalization Pass v1 must not do the following:

- invent new Domains
- invent new Bounded Contexts without existing evidence
- finalize unresolved ownership questions prematurely
- force final Aggregate boundaries
- resolve Brand placement beyond current evidence
- resolve final Client Brain ownership beyond current evidence
- resolve final Service Agreement ownership beyond current evidence
- introduce Phase 2+ architecture into Phase 1 cleanup

---

## Concepts Requiring Canonical Treatment
These concepts should have one primary canonical explanation
and should not be redefined in conflicting ways across `domains.md`:

- Domain
- Subdomain
- Bounded Context
- Entity
- Candidate Aggregate
- Memory Object
- Shared Service / Shared Service Artifact
- Business Artifact
- Domain Artifact
- Capability
- Workflow
- Plugin
- Provider
- Client
- Client Account
- Client Relationship
- Client Brain
- Engagement Scope
- Service Agreement
- Brand
- Human Operator

---

## Structural Goals
Normalization Pass v1 should improve:

- heading consistency
- section ordering consistency
- terminology consistency
- cross-reference consistency
- distinction between identity, memory, execution, and governance concepts

---

## Discovery Preservation Rule
If normalization reveals a true missing Domain
or a truly missing critical boundary,
mark it explicitly as:

- Assumption
- Open Question
- Risk
- Follow-up Discovery Item

Do not silently redesign the file during normalization.

---

## Desired Outcome
After Normalization Pass v1:

- `domains.md` remains the source of truth
- duplicated definitions are reduced
- the canonical classification layer becomes the main reference point
- cross-domain concepts are easier to interpret consistently
- remaining unresolved issues stay visible without destabilizing the model
