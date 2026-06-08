# Brainstorm: Ticket Entity Ownership — Three-Lens Trio

Date: 2026-06-09
Resolves: Q-023 → DEC-039
Registers: Q-024 (Ticket ↔ Escalation Case lifecycle coupling, open)

---

## Context

The gap analysis (`grounding/Gap-Analysis-and-Roadmap.md` §10) flagged "Self-serve client
controls + ticketing" as a T3 Phase-1 reopening. Client Success carries no structured
client-request entity — client-submitted issues, complaints, and queries were implied by
Escalation Case and Coordination Request but never separately modeled as an intake form
with its own lifecycle. This is the 6th of the ~10 Phase-1 entity reopenings.

---

## Lens 1 — Senior PM

**Orphan test (DEC-033):** Does any existing domain cover structured client-request intake?
Yes — Client Success already owns `Escalation Handling` (bounded context: complaints,
blockers, dissatisfaction signals, issue intake, client-facing escalation routing;
`domains.md:1607-1614`). Ticket is not orphaned; it belongs in an existing domain.

**Extend test (DEC-034):** Is Ticket a new first-class Entity in that domain, or is it
absorbed into an existing entity? Ticket has:
- Its own lifecycle (submitted → routed → in-progress → resolved/closed)
- An identity (a structured, submitted request with category + priority + handler ref)
- Revision history (resubmissions, status updates)

These criteria satisfy Entity classification. It cannot be absorbed into Escalation Case
(different trigger, different lifecycle semantics) or Coordination Request (different
origin, different consumer). → **Extend Client Success**.

**Tier:** T3 — post-launch build; does not block P1 decision.

**Business case:** A structured intake form is prerequisite to self-serve client experience
(P2 surface) and the "Client Ticket → Resolution" workflow (P6 8th flow). Without the P1
entity, neither can land cleanly.

---

## Lens 2 — Senior Workflow Designer

**Workflow evidence:** The existing Escalation Loop (P6, `workflows.md:200-213`) handles
severity-driven escalations that originate internally from workflow conditions. Ticket
originates externally from client submission — a distinct trigger. These are two different
workflow entry points and should remain separate entities so the Escalation Loop pattern
does not have to accommodate two different trigger modes.

**Non-collapse analysis (four dimensions):**

| Dimension         | Escalation Case                  | Ticket                               | Coordination Request              |
|-------------------|----------------------------------|--------------------------------------|-----------------------------------|
| Trigger           | Internal severity / workflow     | Explicit client submission           | Internal operational coordination |
| Routing           | Implicit (severity-driven)       | Explicit (named handler destination) | Explicit (meeting/schedule type)  |
| Lifecycle          | Resolution + root-cause          | Request fulfillment                  | Confirmation / response           |
| CRM behavior      | May or may not notify CRM        | May trigger CRM-notify side-effect   | No CRM side-effect                |

All four dimensions differ. The non-collapse is firm.

**Coupling question (Q-024):** A Ticket may *spawn* an Escalation Case when severity is
met (Model A: two independent entities). Alternatively a Ticket could *become* an Escalation
Case at a severity threshold (Model B: single lifecycle). The current posture is Model A
(DEC-039 default); the coupling is its own gated question because it affects aggregate
boundaries and the Escalation Loop interaction. The existing open question at
`domains.md:1712-1714` ("When a client repeatedly rejects proposed timing or deliverables,
does that remain normal coordination, or become an Escalation Case?") is in the same scope
— folded into Q-024.

**Community exclusion:** Community is B2C public audience engagement (comments, DMs,
conversations — post-publish, anonymous/public, DEC-035). Ticket is B2B private
client-submitted request. These share no lifecycle and no ownership boundary. Firm exclusion.

---

## Lens 3 — Senior System Designer

**Data model implications:** Ticket as a first-class Entity means:
- Its own identity key (not a subtype of Escalation Case)
- Its own aggregate (pending Q-024 — could share with Escalation Case if Model B wins)
- Its own persistence boundary (Phase 7 realizes storage; Client Success owns the entity)

**Inversion guard (DEC-031 G-1):** Phase 7 realizes storage and notify-dispatch but does
not own the entity. The entity definition is Phase 1. ✓

**CRM-notify as side-effect:** Ticket triggers a CRM-notify event but does not own the CRM
record. This is an outbound event from Client Success to CRM — Client Success OWNS, CRM
receives and references. Clean boundary. ✓

**Routing-destination reference:** The "named handler destination" is a reference to a
Service Delivery resource (or potentially a Workforce resource). Ticket holds the reference;
the routing rules live in Governance. Clean altitude. ✓

**Aggregate placement:** Left draft/pending because Q-024 lifecycle coupling determines
whether Ticket and Escalation Case can share an aggregate root or must be separate aggregates
with an event link. Deferral is correct. ✓

---

## Reconciled Recommendation

**Owner:** Client Success (unanimous — extend test passes, orphan test fails)
**Entity name:** Ticket (not "Support Ticket" — keep naming simple and domain-clear)
**Classification:** Entity; aggregate placement draft/pending
**Critical pre-write requirement (DEC-034 discipline):** explicitly non-collapse from
  Escalation Case and Coordination Request in the landing DEC
**Boundary set:** Client Success owns; CRM / Service Delivery / Finance / Governance /
  Knowledge reference; Community excluded; Phase 7 realizes
**Tier:** T3

**Q-024 recommendation:** Register as open; two-entity posture (Model A) is the default
from DEC-039. Resolve when Escalation Case aggregate boundary work is ready.

**Follow-ons (each a separate later gate):**
- P6 8th flow "Client Ticket → Resolution"
- P2 self-serve submit surface
- P4 inbound channel
- Ticket ↔ Escalation Case aggregate boundary (Q-024)

---

*Brainstorm for DEC-039. Trio was unanimous on owner and classification. Q-024 registered
as open — the coupling question is meaningful but does not block the P1 entity decision.*
