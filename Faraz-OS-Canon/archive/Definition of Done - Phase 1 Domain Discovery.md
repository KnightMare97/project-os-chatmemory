# Definition of Done - Phase 1 Domain Discovery

## Purpose
This file defines when Phase 1 Domain Discovery
is complete enough
to move from active discovery
into a dedicated normalization pass.

It is not a claim
that all architectural questions are fully resolved.

It is a working completion rule
for the current markdown-based architecture process.

---

## Source of Truth
Phase 1 Domain Discovery is considered complete enough
only when `domains.md`
is the active source of truth
for the current domain model.

Snapshots may record changes and decisions,
but `domains.md` remains the main working file.

---

## Minimum Completion Criteria

### 1. Core Domain Coverage
Each core Phase 1 Domain should exist in `domains.md`
with an explicit section.

Current expected Domains:
- CRM
- Service Delivery
- Finance
- Workforce
- Knowledge
- Intelligence
- Client Success
- Governance

---

### 2. Minimum Structure Per Domain
Each Domain should contain,
at minimum:

- Domain Position or equivalent framing
- Responsibilities
- What it owns
- Candidate Entities
- Candidate Aggregates
- Candidate Bounded Contexts
- Candidate Inbound Events
- Candidate Outbound Events
- Risks
- Open Questions

Not every section must be equally mature,
but every core Domain should be structurally present.

---

### 3. Canonical Classification Baseline
`domains.md` should contain
an explicit classification baseline
for key architectural concepts.

This includes at least:
- Domain
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

---

### 4. Critical Boundary Coverage
The most architecturally sensitive cross-domain concepts
should have explicit draft treatment.

At minimum,
this includes:
- Client
- Client Account
- Client Relationship
- Client Brain
- Engagement Scope
- Service Agreement
- Brand
- Human Operator

These concepts do not need final answers,
but they should not remain implicit.

---

### 5. Explicit Draft Status
Important unresolved items should be marked clearly as:
- Assumption
- Open Question
- Risk

Phase 1 is not blocked by unresolved questions,
but ambiguity should be made visible.

---

### 6. No Hidden Ownership
If an important concept is referenced across multiple Domains,
the file should make its likely ownership direction visible,
even if final ownership is still draft.

This matters especially for:
- Client Brain
- Engagement Scope
- Service Agreement
- Brand
- Human Operator
- approval-related artifacts

---

### 7. Discovery Before Cleanup
Phase 1 Domain Discovery is done enough for normalization
when the major missing content is no longer about
missing Domains or missing concept boundaries,
but mostly about:
- duplicated wording
- repeated definitions
- inconsistent phrasing
- structural cleanup
- section ordering
- cross-reference cleanup

This is the key signal
that discovery has become stabilization work.

---

## Not Required Before Normalization
The following do not need to be fully finalized
before starting the normalization pass:

- final Aggregate boundaries
- final Service Agreement ownership
- final Client Brain ownership
- final Brand placement
- final Subdomain strategy
- full implementation detail
- technical schema design
- infrastructure design
- Phase 2 or later architecture details

Phase 1 is about usable domain discovery,
not total certainty.

---

## Ready for Normalization Pass
Phase 1 Domain Discovery should be considered ready
for a normalization pass
when all statements below are true:

- all core Domains are present
- each core Domain has the minimum section structure
- critical cross-domain concepts are explicitly addressed
- canonical classification rules exist
- unresolved issues are visible as draft questions or risks
- most new work would now be cleanup,
  alignment,
  deduplication,
  and wording stabilization
  rather than major new discovery

---

## Normalization Pass Goal
Once the Definition of Done is met,
the next step is not broad expansion.

The next step is to:
- remove duplicated definitions
- keep one canonical definition for important concepts
- align wording across Domains
- move repeated cross-domain explanations into reference sections
- reduce ambiguity without inventing new architecture

---

## Working Rule
If a new addition creates a major new missing Domain
or reveals a major missing boundary,
Phase 1 discovery is still active.

If new additions mostly clarify or restate known concepts,
Phase 1 discovery is likely complete enough
for normalization.
