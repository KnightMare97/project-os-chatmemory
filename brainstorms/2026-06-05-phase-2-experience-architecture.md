# Phase 2 Experience Architecture: Brainstorm / Discovery Notes
Date: 2026-06-05 · Goal: Define Phase 2 scope, its boundaries with Phase 3 (Capability Map) and Phase 4 (Extensibility), and what `experience-architecture.md` should contain. Starting from Open Question Q-011.

## Status
Interview in progress. Repository is source of truth; this is a Phase 11
operating-method capture feeding Phase 2 content decisions. Nothing here is
canon until promoted via an explicit decision and snapshot. Per CLAUDE.md,
this session must not silently finalize boundaries — decisions are flagged
for explicit human confirmation.

## Grounding already read (no need to re-ask)
- Canon phase map (`Faraz-OS-Canon.md`): Phase 2 sub-items are Personas,
  Operating Surfaces, Portals, Navigation Model, Permission Matrix,
  Cross-Domain Views, Channel Behaviors. Phase 3 = Capability Map
  (Research, Strategy, Content/Video Creation, Publishing, Analytics,
  Reporting, Lead Scoring). Phase 4 = Extensibility Model (Permission,
  Extension Contracts, Plugin/Provider/Channel Model, ...).
- Phase 8 Puzzle Board has an "Experience Layer [ADDED]" and "AI Layer".
- `domains.md` Governance domain OWNS permission/authorization/policy RULES
  as source of truth and is explicitly "not a UI permission table"
  (domains.md:2170-2173). Human Operator identity lives in Workforce.
- No `experience-architecture.md` / `capabilities.md` / `extensibility.md`
  files exist yet — only the canon map defines these phases.

## Summary / key decisions
(running synthesis — all items below CONFIRMED in interview, pending
promotion to canon via explicit decision + snapshot)

**Phase 2 purpose.** Designs the human experience layer of Faraz OS: which
human personas exist, what portals/surfaces they get, how they navigate,
what cross-domain info they see, and how the experience differs per channel.

**Scope.**
- Human experience ONLY, all human personas. AI/agent-facing surfaces are
  OUT (Phase 7 likely; confirm vs Phase 8 AI Layer later — not blocking).
- Phase 2 owns *where / to whom / how* humans interact. It does NOT own:
  human identity (Workforce/Phase 1), capabilities (Phase 3), authorization
  rules (Governance/Phase 1), channel integration (Phase 4), or workflow
  orchestration (Phase 6).

**Governing boundary test (Q3).** Presentation/surface/navigation -> Phase 2.
Reusable functional ability -> Phase 3. Ordered cross-step flow + gates ->
Phase 6.

**Personas (Q1, Q5).** Client (ext), Contractor (ext), Workforce/Operator
(int), Manager (int), System Administrator (int), + Future Personas
placeholder. Contractor ≠ Operator (distinct portals/surfaces). Client is a
single persona for now; client admin/viewer split deferred. Persona = P2
experience archetype/role-group; Workforce identity = P1 (referenced,
never owned).

**Portals & Surfaces (Q4).** Portal = visual panel per persona group; one
portal definition per persona group; contains Operating Surfaces. Operating
Surface = functional workspace, reusable across portals. Multi-role human
gets ONE composed portal (union of role-scoped surfaces). identity->portal
is role-based composition. Navigation Model = movement between surfaces
within a persona's composed portal.

**Permission Matrix (Q2, Q-011).** Three-altitude separation: Governance
(P1) = authoritative permission RULES (source of truth, "not a UI table");
Phase 4 = extension/plugin/provider capability grants; Phase 2 Matrix =
read-only projection of Governance rules onto the experience layer. Matrix
rows = personas, columns = surfaces/portals/views (NOT capabilities). No
rule authorship in P2.

**Cross-Domain Views (Q6).** Persona-facing presentation/composition of
multi-domain info (e.g. Manager view = CRM + Service Delivery + Finance).
Consumes, never owns or computes. KPI computation = Phase 3; the dashboard
surface that displays it = Phase 2.

**Channel Behaviors (Q3).** In Phase 2 but narrow: only human-experience
differences per channel — rendering, preview, notification UX. Not channel
integration (P4), not workflow (P6).

**Q-011 status: fully RESOLVED** (both parts A and B).

## Q&A log

### Q1 — Q-011 part A: operator surfaces in scope? + human-vs-AI experience
- Asked: Does Phase 2 cover operator-facing surfaces or interaction design
  only? And is Phase 2 strictly human experience or also AI/agent-facing?
- Captured:
  - Phase 2 covers ALL human personas including operators. Confirmed.
  - Personas named: clients, contractors, workforce, managers,
    administrator of the AI-native system (responsible for managing
    workflows, credentials, etc.), and future humans of the system.
  - Phase 2 is STRICTLY human experience. AI/agent-facing surfaces are
    NOT Phase 2 — they belong to AI Architecture (user said "Phase 7 likely").
- Flags: confirm the exact home of AI/agent-facing surfaces (Phase 7
  System Architecture Blueprint > AI Architecture, vs Phase 8 AI Layer)
  -> owner: a later Phase 7/8 scoping session, not blocking Phase 2.

### Q2 — Q-011 part B: Permission Matrix overlap with Phase 4?
- Asked: Does the Phase 2 Permission Matrix overlap Phase 4 "Permission"?
  Is the matrix persona→surface (no rule authorship)? Rows/columns?
- Captured:
  - Three-altitude separation confirmed correct (Governance rules / Phase 4
    extension grants / Phase 2 experience projection).
  - Phase 2 Permission Matrix is PURELY persona → surface exposure. No rule
    authorship.
  - Rows = personas; columns = surfaces/portals/views. NOT capabilities
    (that would pull Phase 3 in and break the boundary).
- Flags: none. Q-011 fully resolved.

### Q3 — Governing decision test (Phase 2 vs 3 vs 6) + Channel Behaviors
- Asked: Confirm the three-way test? Does Channel Behaviors stay in Phase 2?
- Captured:
  - **Three-way boundary test CONFIRMED** (this is the scope doc's boundary
    statement): Phase 2 = what a human SEES/DOES, on which SURFACE, and how
    they MOVE between views (presentation/surface/navigation/interaction).
    Phase 3 = what functional ABILITY the system has (UI-independent).
    Phase 6 = the ORDERED SEQUENCE of steps + approval gates across
    capabilities. Rule: presentation/surface/nav -> P2; reusable ability ->
    P3; ordered cross-step flow -> P6.
  - **Channel Behaviors stays in Phase 2 but NARROWLY scoped**: only
    human-experience differences per channel — rendering, preview,
    notification UX. Nothing about integration (Phase 4 Channel Model) or
    workflow (Phase 6).
- Flags: none.

### Q4 — Portal vs Operating Surface
- Asked: Portal-contains-Surface relationship? Portals 1:1 per persona or
  role-based / many-to-many?
- Captured:
  - **Portal = the visual panel per persona group.** Portal CONTAINS
    Operating Surfaces. Confirmed (portals are the top-level container;
    surfaces are functional workspaces within, reusable across portals).
  - **One portal definition per persona group.**
  - A multi-role human (e.g. manager who is also an operator) gets **ONE
    composed portal** with surfaces scoped to their combined role — NOT two
    separate portals.
  - identity -> portal is **role-based composition**, not strictly 1:1.
    The rendered portal = union of the human's role-scoped surface
    entitlements.
  - Navigation Model = how a persona moves between the surfaces available
    within their (composed) portal.
- Flags: none.

### Q5 — Canonical persona list + Persona ↔ Workforce-identity boundary
- Asked: Lock persona set? Contractor vs Operator distinct? Confirm Persona
  (P2) vs Workforce identity (P1) boundary? Client sub-personas?
- Captured:
  - **Canonical persona set (locked for now):** Client (external),
    Contractor (external), Workforce/Operator (internal), Manager
    (internal), System Administrator (internal, manages workflows/
    credentials/config), + Future Personas placeholder.
  - **Contractor and Workforce/Operator are DISTINCT personas** — different
    portals and surfaces. Contractor = scoped external view; internal
    operator = full internal surfaces.
  - **Boundary CONFIRMED:** Persona = Phase 2 experience archetype /
    role-group. Workforce identity = Phase 1. Phase 2 references Workforce
    identities, never owns them.
  - **Client is a SINGLE persona for now.** Client sub-personas (admin vs
    viewer) -> Future Personas placeholder. Do NOT design for it now.
- Flags: none.

### Q6 — Cross-Domain Views vs Phase 3 Reporting/Analytics
- Asked: Define Cross-Domain View? Confirm KPI-computation/dashboard-surface
  split?
- Captured:
  - **Cross-Domain View = presentation/composition ONLY.** Consumes,
    never owns or computes the underlying data.
  - **KPI computation = Phase 3; the dashboard surface that displays it =
    Phase 2.** The altitude split holds (presents / computes / owns).
- Flags: none.

### Q7 — Out-of-scope confirmation + completeness backstop
- Asked: Confirm non-goals list? Design system in/out? Navigation depth?
  Phase 2 ↔ Phase 8 relationship? Anything untouched?
- Captured:
  - **Design system (colors/components/styling) is OUT of Phase 2.**
    Structure only, not pixels.
  - **Navigation Model stays at surface-movement level.** Notification
    routing and deep-linking = noted FUTURE sub-detail, not in scope now.
  - **Phase 2 = design source; Phase 8 = positions it in the puzzle board.**
    Confirmed.
  - No additional untouched items raised. Interview complete.

## Non-goals (explicit, confirmed) — Phase 2 does NOT cover
- AI/agent-facing surfaces -> Phase 7
- authoring permission/authorization rules -> Phase 1 Governance
- defining capabilities -> Phase 3
- workflow orchestration / approval-gate sequencing -> Phase 6
- channel integration / technical channel model -> Phase 4
- owning domain data or human identity -> Phase 1
- visual/brand design system (pixels, components, styling)
- actual screen/UI implementation -> later build phases (Phase 10 roadmap)

## Open flags (pending input)
- AI/agent-facing surfaces home: Phase 7 vs Phase 8 — confirm later, not
  blocking Phase 2. -> Phase 7/8 scoping.
- Future Personas placeholder must be carried into experience-architecture.md
  (client admin/viewer split; other future humans). Not designed now.
- Navigation: notification routing + deep-linking deferred as a future
  sub-detail. Capture in experience-architecture.md as a marked future item.
