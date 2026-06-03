# Snapshot-004 - CRM Refinement from Backend Evidence

## Current Phase
Phase 2 DDD Analysis

## Current Topic
CRM domain refinement using current CRM backend evidence

---

## Status
CRM draft has been refined using the current operational backend.

The CRM domain remains valid,
but its internal structure is now clearer.

CRM should currently be modeled
as one Domain with two major Bounded Context directions:
- Lead Acquisition & Conversion
- Current Client Management

The first is strongly evidenced in the current implementation.
The second is architecturally valid,
but still more draft and extensible.

---

## Key Findings

### FIND-001
The current CRM backend is strongly lead-centric and pipeline-centric,
not yet a full client-account platform.

### FIND-002
The strongest implementation evidence supports:
- lead intake
- sales stage progression
- follow-up scheduling
- signal-based prioritization
- manager assignment
- call summary history
- dead lead archiving
- dead lead recheck
- dashboard reporting

### FIND-003
CRM should not be modeled only as lead management.

It also needs a second bounded context direction
for managing current clients,
even if that part is not yet strongly implemented.

### FIND-004
Inside CRM,
`Lead Acquisition & Conversion`
and `Current Client Management`
should be treated as distinct Bounded Contexts,
not as one undifferentiated block.

### FIND-005
Manager tabs and dashboard views are better treated
as projections or read models,
not primary source-of-truth aggregates.

### FIND-006
Dead lead archiving and reactivation
is a real operational concern
and deserves explicit modeling inside CRM.

---

## Decisions

### DEC-001
CRM remains a Domain.

### DEC-002
CRM will be modeled with two major Bounded Context directions:
- Lead Acquisition & Conversion
- Current Client Management

### DEC-003
`Lead Acquisition & Conversion`
is implementation-grounded
and should drive the current CRM draft.

### DEC-004
`Current Client Management`
remains inside CRM,
but should be marked draft
until stronger evidence or richer implementation appears.

### DEC-005
Client Brain is not a CRM Entity,
Aggregate,
or Bounded Context.

It remains a separate memory-centric concept.

### DEC-006
Manager queue tabs and CRM dashboards
should be treated as projections,
not core Aggregates.

---

## Risks

### R-001
If CRM is modeled only from the current backend,
the current-client side of CRM may be underrepresented.

### R-002
If CRM is modeled too broadly,
it may absorb responsibilities
that belong to Client Success,
Service Delivery,
or Knowledge.

### R-003
The boundary between `Current Client Management`
and `Client Success`
is still not finalized.

### R-004
The boundary between CRM commercial/client visibility
and Service Delivery operational ownership
must remain explicit.

---

## Open Questions

### Q-001
When a Lead becomes a signed client,
does the same Entity evolve into a Client Account,
or is a new Entity created?

### Q-002
How much of current-client management
should stay inside CRM
versus move into Client Success?

### Q-003
Should Service Relationship Record exist inside CRM
as a commercial/account view,
while Engagement Scope remains in Service Delivery?

### Q-004
What is the final boundary between:
- CRM Client Account
- Client Success account handling
- Client Brain memory ownership

---

## Recommended Update Target
Update `domains.md`
by replacing the previous CRM draft
with `CRM (Draft v2)`.

Do not duplicate the full CRM text into this snapshot.

This snapshot should remain a concise record
of why the CRM model changed.

---

## Next Focus
Clarify the boundary between:
- CRM
- Client Success
- Service Delivery

This is now more important
because CRM has been split into:
- lead conversion concerns
- current-client management concerns
