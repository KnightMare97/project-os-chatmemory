# Brainstorm — Q-002: Service Agreement ownership (2026-06-08)

**Status:** Working reasoning behind DEC-034. Immutable history once landed; cites
resolve against the landing commit. Not canon.

## The question
Q-002: the final ownership model for Service Agreement — drafted as a Business Artifact
with unresolved ownership (`domains.md:3016-3210`). The #2 first gated decision in the
non-canon gap analysis (the commercial-spine keystone). Three sub-questions: G-2 owner,
G-3 classification, G-6 Q-006 disposition.

## Three-lens trio (Product / Workflow / System)
**Consensus on two:**
- **G-3 = Entity (not yet Aggregate).** All three: the drafted lifecycle
  (draft→proposed→agreed→active→revised→closed→superseded) + revision history are
  load-bearing — scope-change (active→revised) and renewal (superseded/closed) *cannot
  be expressed* without revision identity. "An artifact you can revise and supersede
  while preserving identity is, by definition, an Entity." Aggregate must wait for Q-006
  (the SA↔Engagement-Scope consistency boundary) — promoting now would silently draw the
  boundary Q-006 owns (classification-collapse).
- **G-6 = carry Q-006.** All three: Q-002 is ownership/classification; Q-006 is the
  lifecycle/propagation mechanism. The directional invariant (Engagement Scope
  derived-from/constrained-by SA, no drift without explicit revision logic) is already
  settled in canon and workflow-sufficient. Q-006 is the gate that later upgrades SA
  Entity→Aggregate; its safe deferral depends on G-3 landing as revisionable Entity.

**Divergence on G-2 (owner):**
- **Product → CRM.** CRM already owns the pre-sales funnel where SA is born; a new domain
  slows v1 (its first-class dependents — package catalog, SLA, renewals — are T2/T3);
  "create a domain for a vacuum, not to relocate something with a good home."
- **System → CRM.** The Media & Assets precedent (DEC-033) is an **orphan test** — a new
  domain wins only when *no existing domain's responsibility covers the entity*. Media &
  Assets was created because the Client Asset was orphaned. Service Agreement is **not**
  orphaned: CRM is "the commercial-facing layer" (`domains.md:714-715`), already owns
  "high-level service relationship visibility" (`:751-754`); canon already leans
  `Service Agreement → CRM / Client Success` (`:690`). Absorbing SA *sharpens* CRM rather
  than distorting it. New domain = carried fallback if CRM later strains.
- **Workflow → new Commercial/Agreements owner preferred, but with a strong CRM fallback.**
  Clean create/amend/renew seams favor a dedicated owner; *but* for a single-tenant
  showcase a full new domain "may be heavier than the seams justify." The hard requirement
  either way: **SA must be a first-class artifact with one owner, addressable by
  reference — not folded into the CRM Client entity.**

## The reconciled call (→ DEC-034)
The divergence is narrower than it looks: the Workflow lens's *hard requirement* (SA =
first-class, single-owner, reference-addressable, **not folded into the Client Account
entity**) is fully satisfied by **CRM-owns-as-a-distinct-Entity**. Its preference for a
separate domain is conditioned on funnel heaviness, which Product and System both judge
insufficient at launch. So:
- **G-2: CRM owns Service Agreement as a first-class Entity**, reference-addressable, not
  absorbed into the Client Account entity. New "Commercial/Agreements" domain = recorded
  carried fallback if the commercial-spine reopenings (Proposal/Package/SLA) later show
  CRM straining.
- **G-3: Entity** (identity + lifecycle + revision history); Aggregate-pending-Q-006.
- **G-6: carry Q-006** untouched.

## Two narrowings (Phase-1 owning-phase content, not new architecture)
- `domains.md:690` `Service Agreement → CRM / Client Success` → narrowed to CRM-owns /
  Client-Success-references (resolving an existing draft slash).
- Finance open note (`domains.md:2141`, "Is Service Agreement owned outside Finance?") →
  answered: yes (CRM); Finance's *other* open questions stay open.

## Scope discipline (DEC-033 precedent)
Resolve Service Agreement ownership + classification only. Dependents (Proposal, Service
Package, SLA, Contract-lifecycle/renewal/e-sign, Amendment) and Q-006 are each their own
later gate. R-027 set, Q-016/Q-017, the other ~8 reopenings untouched. Landing shape: one
isolated called-out commit (DEC-034 + domains.md edits + Q-002→Resolved + Current-State +
this brainstorm).
