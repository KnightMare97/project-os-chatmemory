# Snapshot-013 - Phase 2 Experience Architecture Scope Defined

## Current Phase
Phase 11 Claude Code Operating System — operational
Phase 2 Experience Architecture — active, scope defined, content not yet written

## Current Topic
Scoping session for Phase 2 Experience Architecture.
Resolving Open Question Q-011 and defining the working
scope, boundaries, and contents of `experience-architecture.md`
before any content is produced.

## Status
A structured scoping interview (grill-me) was completed.
Open Question Q-011 is fully resolved.
The full Phase 2 scope, persona set, sub-item definitions,
and explicit non-goals are captured and human-confirmed.
No architecture content file has been written yet:
`experience-architecture.md` is deferred to a separate session.
This snapshot records the decisions; it does not write canon content.
Repository is in a stable, confirmed state.

---

## Document Updates

### DOC-018
`brainstorms/2026-06-05-phase-2-experience-architecture.md` created.
It is the full scoping capture for Phase 2: purpose, scope,
governing boundary test, persona set, all seven canon
sub-item definitions, explicit non-goals, and open flags.
It is a working capture, not canon.

### DOC-019
`experience-architecture.md` has NOT been created or modified.
Writing Phase 2 canon content from the approved scope is
deferred to a separate session (plan -> build -> review).

---

## Decisions

### DEC-019
Open Question Q-011 is resolved, and the Phase 2 Experience
Architecture scope is defined and human-confirmed:

- **Scope:** Phase 2 designs the human experience layer only,
  for all human personas. AI/agent-facing surfaces are out of
  scope (they belong to AI Architecture, Phase 7 likely).
- **Governing boundary test:** presentation / surface /
  navigation -> Phase 2; reusable functional ability -> Phase 3
  Capability Map; ordered cross-step flow and approval gates ->
  Phase 6 Workflow Design.
- **Q-011 part A:** operator-facing surfaces ARE in Phase 2
  scope. Phase 2 owns where / to whom / how humans interact;
  it does not own human identity (Workforce/Phase 1),
  capabilities (Phase 3), or authorization rules
  (Governance/Phase 1).
- **Q-011 part B (Permission):** three-altitude separation.
  Governance (Phase 1) owns authoritative permission/
  authorization rules (source of truth, explicitly "not a UI
  permission table"). Phase 4 Extensibility "Permission" =
  extension/plugin/provider capability grants via contracts.
  Phase 2 "Permission Matrix" = read-only projection of
  Governance rules onto the experience layer; rows = personas,
  columns = surfaces/portals/views (not capabilities). Phase 2
  authors no rules.
- **Personas (locked for now):** Client (external), Contractor
  (external), Workforce/Operator (internal), Manager (internal),
  System Administrator (internal; manages workflows,
  credentials, config), plus a Future Personas placeholder.
  Contractor and Workforce/Operator are distinct personas with
  distinct portals/surfaces. Client is a single persona for now;
  client admin/viewer sub-personas are deferred. Persona is a
  Phase 2 experience archetype/role-group, distinct from
  Workforce identity (Phase 1), which Phase 2 references but
  never owns.
- **Portals & Surfaces:** Portal = the visual panel per persona
  group; one portal definition per persona group; a portal
  contains Operating Surfaces. Operating Surface = a functional
  workspace, reusable across portals. A multi-role human gets
  one composed portal (union of role-scoped surfaces); identity
  -> portal is role-based composition. Navigation Model =
  movement between surfaces within a persona's composed portal.
- **Cross-Domain Views:** persona-facing presentation/
  composition of multi-domain information; consumes, never owns
  or computes. KPI computation is Phase 3; the dashboard surface
  that displays it is Phase 2.
- **Channel Behaviors:** in Phase 2 but narrowly scoped to
  human-experience differences per channel (rendering, preview,
  notification UX). Not channel integration (Phase 4), not
  workflow (Phase 6).
- **Phase 2 <-> Phase 8:** Phase 2 is the design source; Phase 8
  Puzzle Board "Experience Layer" positions it.

This decision records scope only. It does not finalize any
Phase 1 domain boundary and does not write Phase 2 canon content.

---

## Findings

### FIND-022
Governance (Phase 1, `domains.md`) owns permission,
authorization, and policy rules as the source of truth and is
explicitly modeled as "not a UI permission table"
(`domains.md` ~2170-2173). This is the evidentiary basis for
the three-altitude permission separation in DEC-019 and removes
the apparent Phase 2 / Phase 4 permission overlap raised in Q-011.

---

## Assumptions

- Assumption: the scope captured in DEC-019 reflects
  human-confirmed decisions made this session; the canon write
  to `experience-architecture.md` is pending and will be done
  under plan -> build -> review in a separate session.
- Assumption: no Phase 1 domain truth, ownership, or boundary
  was changed this session. Phase 2 references Phase 1; it does
  not reinterpret it.
- Assumption: the locked persona set is stable for initial
  Phase 2 design; Future Personas (client admin/viewer, other
  future humans) remain an explicit deferred placeholder.

---

## Risks

### R-023 (carried forward, now reduced)
Phase 2 risked drifting into Phase 3 Capability Map or Phase 6
Workflow Design territory. Mitigation applied: the governing
boundary test and an explicit non-goals list are now defined
and confirmed before any content is written. Keep active until
`experience-architecture.md` is written in a way that respects
these boundaries.

### R-025 (carried forward, active)
Session close-out is applied by discipline, not enforced by
tooling. Mitigation: the procedure is codified and executable
in `workflows/sync-protocol.md`.

### R-026 (carried forward, active)
`workflows/sync-protocol.md` references Linear MCP tools by
logical name; if those tool names change, its Tooling section
must be updated.

---

## Open Questions

### Q-011 — RESOLVED
Phase 2 <-> Phase 3 boundary and the Permission Matrix question
are resolved (see DEC-019). To be reflected in Linear (`KNI-10`
-> Done, citing this snapshot).

### Q-012 (deferred)
Phase 7 <-> Phase 8 boundary. Unchanged; deferred until Phase 6,
lives in `open-questions.md`.

### Q-013 (new, deferred, repo-only)
Exact home of AI/agent-facing surfaces (Phase 7 System
Architecture Blueprint > AI Architecture vs Phase 8 AI Layer).
Not blocking Phase 2. Lives in `open-questions.md`; not tracked
as an active Linear issue.

---

## Next Focus

1. Write `Faraz-OS-Canon/experience-architecture.md` from the
   approved scope (DEC-019 / the brainstorm capture), under
   plan -> build -> review, in a separate session. Carry the
   Future Personas placeholder and the deferred navigation
   sub-detail (notification routing, deep-linking) as marked
   future items.
2. After repo approval of this close-out, reconcile Linear:
   set `KNI-10` (Q-011) to Done citing this snapshot; mark
   `KNI-8` (Define scope for Phase 2) Done now that scope is
   defined, and open a new `architecture`/`Phase 2` issue for
   writing `experience-architecture.md` content.

Use the established discipline:
- plan mode with scope, out-of-scope, risks
- build only after explicit approval
- preserve canonical distinctions throughout
