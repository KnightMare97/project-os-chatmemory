# Snapshot-018 - Phase 2 Portal Contents Written

## Current Phase
Phase 11 Claude Code Operating System — operational
Phase 2 Experience Architecture — active; portal contents per
persona now written into canon (this session)

## Current Topic
Canon write of the Portal Contents per Persona projection in the
Portals section of `Faraz-OS-Canon/experience-architecture.md`.
KNI-14 sub-task 2. Done as plan-then-write (the approved plan was
the scoping artifact; no separate grill-me brainstorm), at
membership + reuse-mode altitude. The content is a faithful
re-projection of the DEC-020 Operating Surfaces inventory, not
new architecture.

## Status
The Portals section of
`Faraz-OS-Canon/experience-architecture.md` now enumerates, for
each of the five locked personas, which Operating Surfaces its
portal contains and in what reuse mode (Full / Scoped / Distinct
surface / —). Built from the 16 firm surfaces only; all 16 appear
in at least one portal. The 5 flagged surfaces remain flagged and
are noted as pending per portal where relevant — none added. The
Permission Matrix remains unpopulated; concrete Cross-Domain Views
remain deferred. Multi-role reuse-mode overlap is explicitly
deferred to the Permission Matrix. Repository is in a stable,
confirmed state.

---

## Document Updates

### DOC-036
`Faraz-OS-Canon/experience-architecture.md` updated
(single-file, minimal-diff; +130 / −10). Changes:
- `## Portals`: new `### Portal Contents per Persona` subsection
  added between "What Portals are not" and the scope note. Five
  per-persona tables (Operator, Manager, Contractor, Client,
  System Administrator), each Surface | Reuse mode | Note;
  per-persona tables (not a persona×surface matrix) to avoid
  resembling the deferred Permission Matrix. Inline projection
  notes (Manager has no Production Workspace; Contractor has no
  Lead Workspace / Operator Inbox / Review Queue), pending-flag
  notes (Team Performance, Client Profile, System Configuration),
  a Future Personas placeholder note, a Multi-role composition
  reaffirmation, and a Boundary note (membership derived from
  inventory reuse markers, not the populated Permission Matrix).
  The Portals "Scope of definition in this file" subsection
  rewritten to state the new membership + reuse-mode altitude and
  what it still defers.
- `## Purpose` and `## Status` disclaimers nuanced: the file now
  enumerates portal contents per persona; Permission Matrix and
  concrete Cross-Domain Views remain unpopulated.
- `## Open and Deferred Items` → Deferred — Concrete enumeration:
  removed the "portal contents per persona" bullet (now done);
  added a note that portal contents are enumerated in the Portals
  section. Permission Matrix and Cross-Domain Views stay deferred.
  The "Flagged — Operating Surfaces carried forward" subsection is
  unchanged.
- `## Provenance`: added that portal contents derive from the
  DEC-020 inventory and the persona-to-portal rule (DEC-019),
  recorded in DEC-021 / Snapshot-018.

### DOC-037
`Current-State.md` updated to reflect that portal contents per
persona are written (this snapshot), and to re-point the next
focus at the sole remaining KNI-14 sub-item (concrete
Cross-Domain Views).

---

## Decisions

### DEC-021
Portal contents per persona for Phase 2 are defined and
human-confirmed (recorded in full in `decisions.md`). They are a
membership + reuse-mode projection of the DEC-020 Operating
Surfaces inventory; built from the 16 firm surfaces only; no new
surfaces invented; the 5 flagged surfaces remain flagged.
Multi-role reuse-mode overlap and authoritative entitlement remain
deferred to the Permission Matrix / Phase 1 Governance. Produced
as plan-then-write (the approved plan was the scoping artifact).

---

## Findings
No new findings this session.

---

## Open Questions
No new open questions this session.
- Q-011 resolved (unchanged; via DEC-019).
- Q-012 deferred (unchanged; Phase 7 ↔ Phase 8).
- Q-013 deferred (unchanged; AI / agent-surface home).

---

## Assumptions
- Assumption: the portal projection faithfully reflects the
  DEC-020 inventory's reuse-pattern column; reuse modes were
  copied verbatim, including the disjunctive "Full or Scoped" for
  the Manager view of Agent & Workflow Monitor.
- Assumption: no Phase 1 domain truth, ownership, or boundary was
  modified. Portal membership references Phase 1/4/5 concepts at
  reference altitude only.
- Assumption: portal membership is a Phase 2 surface-composition
  property and does not constitute the populated Permission
  Matrix; effective entitlement and multi-role overlap remain
  deferred.
- Assumption: the 5 flagged surfaces remain explicitly flagged
  and must not be silently folded into any portal.

---

## Risks

### R-023 (carried forward, active, reduced)
Phase 2 may drift into Phase 3 / Phase 6 territory as detail is
populated. Mitigation held this session: portal contents stayed
at membership + reuse-mode altitude; ordering, landing surface,
and grouping were explicitly excluded (kept with Navigation
Model / UI). Keep active through Phase 2 refinement.

### R-025 (carried forward, active)
Session close-out is applied by discipline; the propose-then-
review gate was reaffirmed and is being followed this session.

### R-026 (carried forward, active)
`workflows/sync-protocol.md` references Linear MCP tools by
logical name; update its Tooling section if those names change.

---

## Next Focus
1. The remaining KNI-14 sub-item is concrete Cross-Domain Views
   (which will resolve the Reports & Analytics Surface and Team
   Performance / Oversight Surface flags).
2. Permission Matrix population remains deferred until Phase 1
   Governance rules in `domains.md` are concrete.
3. Revisit the 5 flagged Operating Surfaces in their owning
   sessions; do not silently fold them into the firm inventory.
4. Carry the Future Personas placeholder and the deferred
   navigation sub-detail (notification routing, deep-linking)
   forward as marked future items.
5. Keep Claude Project input limited to high-signal current
   files; prepare later controlled handoff to Claude Code.
