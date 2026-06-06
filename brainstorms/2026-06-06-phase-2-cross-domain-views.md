# Phase 2 Cross-Domain Views: Brainstorm / Discovery Notes
Date: 2026-06-06 · Goal: Full enumeration of Cross-Domain Views by name across all personas for Phase 2 Experience Architecture, and resolve the classification of the two flagged surfaces (Reports & Analytics Surface; Team Performance / Oversight Surface). KNI-14 final sub-item. This is a grill-me scoping session — real discovery, not a projection.

## Status
Interview complete. Repository is source of truth; this is a Phase 11 operating-method capture feeding Phase 2 content decisions. Per CLAUDE.md, this session must not silently finalize boundaries — decisions are flagged for explicit human confirmation. Nothing here is canon until promoted via an explicit decision and a separate canon write. A `grill-me` skill is not registered in this environment; the established grill-me method was run directly (precedent: the Operating Surfaces scoping session, `brainstorms/2026-06-06-phase-2-operating-surfaces.md` → DEC-020 / Snapshot-016).

## Grounding already read (no need to re-ask)
- CDV framework in `Faraz-OS-Canon/experience-architecture.md` §Cross-Domain Views:
  a persona-facing presentation that composes information from multiple domains onto a single surface for a human. Consumes; does not own (Phase 1) or compute (Phase 3). KPI altitude: computes = P3, presents = P2, owns = P1.
- 8 Phase 1 domains (`domains.md`): CRM, Service Delivery, Finance, Workforce, Knowledge, Client Success, Intelligence, Governance (+ cross-cutting Client Brain / Engagement Scope, Service Agreement, Brand drafts).
- **Boundary finding:** the Intelligence domain (Phase 1) owns derived insights / scores / analytical findings as source of truth (`domains.md`:1750), while the framework says computation = Phase 3. A CDV *consumes* those outputs; it does not resolve the Intelligence-vs-Phase-3 computation question. That stays upstream / out of Phase 2 scope.
- Operating Surfaces inventory (DEC-020): the dashboard/composition-bearing surfaces are Client Brain Surface, Lead Workspace, Reports & Analytics Surface, Contractor Assignments.
- Personas (DEC-019): Client (external), Contractor (external), Workforce/Operator (internal), Manager (internal), System Administrator (internal), + Future Personas.

## Out-of-scope for this session (locked)
- **Entitlement** — who is exposed to which view. This session defines WHICH views exist, not WHO sees them. Entitlement stays with the Permission Matrix / Phase 1 Governance, deferred until Governance rules are concrete (same split that held for Operating Surfaces and Portals).
- The Intelligence(P1)-owns-insights vs Phase-3-computes question (upstream).
- KPI computation (Phase 3); domain data ownership (Phase 1).
- Host-surface decisions for views whose host was deferred (DEC-020 follow-up).
- The canon write into `experience-architecture.md` (a separate plan → build → review session).
- Visual / brand design, screen layout, UI components.

## Summary / key decisions (final synthesis)

**Discovery method (Q1).** Persona-anchored, domain-keyed: anchor on each persona; identify each view by the domain-combination it composes; seed from the flagged + dashboard-bearing surfaces. (Rejected: pure domain-combination — explosion risk; surface-anchored — too narrow.)

**Surface↔View relationship (Q2).** A Cross-Domain View is a named multi-domain composition **rendered on an Operating Surface**. A surface may host one or more views. Views are not themselves portal entries — the host surface is. (Rejected: view-is-a-kind-of-surface — blurs the DEC-020 taxonomy; strict separation — adds a parallel artifact layer.)

**Granularity rule (Q3) — canon-worthy.** One view per coherent persona decision-context composed from a stable domain-set (e.g. "understand this client", "oversee the team", "read performance"). (Rejected: per domain-combination — explosion; per KPI/dashboard cluster — Phase 3 drift.)

**Naming convention (Q6c) — canon-worthy.** Decision/subject + "View"; a persona word only when the composition is persona-specific (e.g. Client Engagement Summary View). Mirrors the Operating Surfaces naming convention.

**Flagged-surface classification (Q4 — reconsidered individually).**
- *Reports & Analytics Surface* → **Both.** It stays the firm Operating Surface from DEC-020 (unchanged). It **hosts two distinct, separately-named Cross-Domain Views** — the Performance & Analytics View and the Team Oversight View — kept separate so the "both" classification does not collapse the two compositions into one. No DEC-020 change.
- *Team Performance / Oversight Surface* → **Pure Cross-Domain View** (the Team Oversight View), hosted on the Manager's Reports & Analytics Surface. Not a standalone surface; removed from the flagged-surface list. DEC-020 stays closed.

**Cross-Domain Views inventory — 7 firm views.** Consume-only; named composed domains; host surface; primary persona.

| # | View | Decision-context | Domains composed | Host surface | Primary persona |
|---|------|------------------|------------------|--------------|-----------------|
| 1 | Client Brain View | understand this client | Client Brain (P5) + CRM + Service Delivery + Client Success + Finance + Brand | Client Brain Surface | Operator (Manager full; Contractor scoped) |
| 2 | Lead Context View | understand this lead | CRM + Intelligence (lead scoring) + Client Success | Lead Workspace | Operator (Manager full) |
| 3 | Performance & Analytics View | read performance | Intelligence + Finance + Service Delivery + CRM | Reports & Analytics Surface | Operator / Manager (Contractor / Client scoped) |
| 4 | Team Oversight View | oversee the team | Workforce + Service Delivery + Client Success + Intelligence | Reports & Analytics Surface (manager scope) | Manager |
| 5 | Engagement Health View | is this engagement healthy / profitable? | Service Delivery + Finance + Client Success + Workforce | **deferred** (DEC-020 follow-up) | Operator / Manager |
| 6 | Client Engagement Summary View | how is my engagement going? | Service Delivery + Finance + Client Success | **deferred** (DEC-020 follow-up) | Client |
| 7 | Contractor Assignment-in-Context View | my assigned work in context | Workforce + Service Delivery + Client Brain (scoped) + Knowledge | Contractor Assignments | Contractor |

Note: Reports & Analytics Surface hosts **two** of these views (#3 and #4), kept separately named.

**System Administrator: no Cross-Domain View (Q6a).** Admin surfaces (Admin Knowledge, Workflow & Agent Configuration, Credentials & Integrations) are config/management at single-domain Governance / Extensibility altitude — not multi-domain human compositions.

**Flags carried forward.**
- **Operator-finance gap (DEC-020) — STILL FLAGGED.** The Engagement Health View (#5) names the composition that will eventually address it, but the gap is **not resolved**: the view's host surface is deferred (DEC-020 follow-up) and the gap's resolution is deferred with it. State: view named; host + resolution deferred.
- **Host surfaces for Engagement Health View (#5) and Client Engagement Summary View (#6)** — DEC-020 follow-up (possible new surfaces, or scoped reuse of existing surfaces).
- Resolved flags (no longer carried): *Reports & Analytics Surface* (→ both) and *Team Performance / Oversight Surface* (→ pure view).

**Boundary discipline held.** Views consume; do not own (Phase 1) or compute (Phase 3). KPI: compute = P3, present = P2, own = P1. The Intelligence(P1)-vs-P3 question is upstream and was not resolved here. Entitlement (who sees which view) is deferred to the Permission Matrix / Phase 1 Governance. No Phase 1 domain truth reinterpreted.

**Decisions implied for the canon write (separate session).**
- Populate `experience-architecture.md` §Cross-Domain Views from framework-only to the 7-view inventory, with the granularity rule, the naming convention, and the surface↔view relationship stated.
- State explicitly that Reports & Analytics Surface hosts two distinct named views.
- Carry the host flags (#5, #6) and the still-flagged operator-finance gap forward in Open and Deferred Items.
- Do NOT populate the Permission Matrix. Do NOT decide deferred hosts.

## Q&A log

### Q1 — Discovery method
- Asked: persona-anchored domain-keyed, domain-combination-driven, or surface-anchored?
- Captured: **persona-anchored, domain-keyed.** Anchor on each persona; identify each view by the domain-combination it composes; seed from flagged + dashboard-bearing surfaces.
- Flags: none.

### Q2 — Surface↔View relationship
- Asked: is a CDV rendered on a surface, a kind of surface, or strictly separate?
- Captured: **a CDV is a named multi-domain composition rendered on an Operating Surface.** Consequence: the 2 flagged surfaces can be "both" (surface = inventory/portal entry; view = the composition it hosts). DEC-020 stays closed.
- Flags: none.

### Q3 — Granularity rule
- Asked: per decision-context, per domain-combination, or per KPI/dashboard cluster?
- Captured: **per decision-context** (canon-worthy).

### Q4 — Flagged-surface classification (each reconsidered individually)
- Asked: classify Reports & Analytics Surface and Team Performance / Oversight Surface each.
- Captured:
  - *Reports & Analytics Surface* → **Both** (firm surface unchanged; hosts the Performance & Analytics View — and, after Q4 on Team Performance, also the Team Oversight View).
  - *Team Performance / Oversight Surface* → **Pure Cross-Domain View** (Team Oversight View), hosted on the Manager's Reports & Analytics Surface; removed from the flagged-surface list.
- Emerged: Reports & Analytics Surface therefore hosts **two** distinct named views; keep them separately named so "both" doesn't collapse the compositions. (Confirmed by human in plan review.)

### Q5 — Enumeration: Engagement Health + external personas
- Asked (a): is there a distinct Engagement Health View, or is it absorbed? (also the operator-finance gap)
- Captured (a): **distinct, host deferred.** Real CDV (Service Delivery + Finance + Client Success + Workforce). Names the composition that will address the operator-finance gap, but host is deferred → the operator-finance gap **remains flagged**, not resolved.
- Asked (b): do external personas get their own named CDVs, or scoped reuse only?
- Captured (b): **distinct views for both.** Client → Client Engagement Summary View; Contractor → Contractor Assignment-in-Context View (host: existing Contractor Assignments surface).

### Q6 — Completeness backstop + host policy + naming convention
- Captured (a) Completeness: **complete; System Administrator gets no CDV.**
- Captured (b) Host policy: **defer hosts** for Engagement Health View and Client Engagement Summary View as a DEC-020 follow-up.
- Captured (c) Naming convention: **decision/subject + "View"** (persona word only when persona-specific) — canon-worthy.

## Open flags (pending input / future sessions)
- Host surface for Engagement Health View (#5) — DEC-020 follow-up.
- Host surface for Client Engagement Summary View (#6) — DEC-020 follow-up.
- Operator-finance gap — still flagged; view named, host + resolution deferred.
- Canon write of §Cross-Domain Views — separate plan → build → review session.
- Permission Matrix population (entitlement) — deferred until Phase 1 Governance rules are concrete.

(Final synthesis lives at the top of this file under "Summary / key decisions (final synthesis)".)
