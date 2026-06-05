# Snapshot-014 - Phase 2 Experience Architecture First Canon Write

## Current Phase
Phase 11 Claude Code Operating System — operational
Phase 2 Experience Architecture — active, first canon write complete

## Current Topic
Writing the first canon content for Phase 2 Experience Architecture
from the approved DEC-019 scope, and backfilling tracker files
(`open-questions.md`, `decisions.md`, `findings.md`) with the
Phase 2 entries that previously lived only inside Snapshot-013.

## Status
`Faraz-OS-Canon/experience-architecture.md` created at framework
level. It defines purpose, scope, governing boundary test, all
seven sub-items (Personas, Operating Surfaces, Portals,
Navigation Model, Permission Matrix, Cross-Domain Views,
Channel Behaviors), non-goals, deferred items, cross-phase
references, and carried risks. It does not enumerate concrete
surfaces, populate the permission matrix, or define portal
contents — those are deferred refinements.
Tracker files updated to reflect Phase 2 entries that previously
existed only inside Snapshot-013. No Phase 1 domain truth was
modified by this session. Repository is in a stable, confirmed state.
Pre-existing tracker drift surfaced as a separate finding
(see FIND-023); out of scope for this close-out.

---

## Document Updates

### DOC-020
`Faraz-OS-Canon/experience-architecture.md` created.
Framework-level Phase 2 canon write per DEC-019 / Snapshot-013.
Defines the seven Phase 2 sub-items, the governing boundary test,
scope, non-goals, deferred items, cross-phase references, and
carries R-023. Does not enumerate concrete surfaces or populate
the permission matrix.

### DOC-021
`open-questions.md` updated.
Q-011 added as RESOLVED (cites DEC-019 / Snapshot-013).
Q-013 added as deferred / repo-only
(AI / agent-surface home: Phase 7 vs Phase 8).

### DOC-022
`decisions.md` updated.
DEC-019 added (Phase 2 scope and Q-011 resolution),
citing Snapshot-013 and `Faraz-OS-Canon/experience-architecture.md`.

### DOC-023
`findings.md` updated.
FIND-022 added (Phase 1 Governance source-of-truth basis
for the three-altitude permission separation;
`domains.md` lines ~2170-2173).

### DOC-024
`Current-State.md` updated.
Reflects the new canon file, the resolved scoping state, and
the shifted next-focus toward Phase 2 framework population.

---

## Decisions
No new decisions authored in this session.
DEC-019 is backfilled into `decisions.md` from Snapshot-013;
it was not created here.

---

## Findings

### FIND-023
Several snapshot-authored entries
(Q-011, Q-012, Q-013, DEC-012 through DEC-019,
FIND-014 through FIND-022)
were not backfilled into the tracker files at the time
of their originating sessions.
This created a consistent drift between `snapshots/`
and `open-questions.md` / `decisions.md` / `findings.md`.

Meaning:
- Snapshots remained canonical.
- Tracker files became incomplete indexes of canonical state.
- The current close-out discipline in CLAUDE.md does not yet
  explicitly require tracker backfill at close.

Impact:
- The next valuable hygiene task is a one-pass tracker
  reconciliation against Snapshots 011, 012, and 013.
- The session close-out discipline may benefit from an explicit
  tracker-backfill step
  (consider extending `workflows/sync-protocol.md`).

---

## Open Questions

### Q-011 — RESOLVED
Closed by DEC-019. Now also recorded in `open-questions.md`
with the resolution citation.

### Q-012 (deferred)
Phase 7 ↔ Phase 8 boundary. Unchanged.
Tracker backfill into `open-questions.md` is queued
under FIND-023; this snapshot does not author it
to avoid invention beyond evidence.

### Q-013 (deferred, repo-only)
AI / agent-surface home: Phase 7 vs Phase 8.
Now recorded in `open-questions.md`.
Not blocking Phase 2.

---

## Assumptions
- Assumption: framework-level Phase 2 content is the correct
  altitude for the first canon write of
  `experience-architecture.md`. Concrete surfaces, portal
  contents, and permission matrix population are later
  refinements requiring further explicit decisions.
- Assumption: backfilling Q-011, Q-013, DEC-019, and FIND-022
  into the tracker files is a hygiene action,
  not an architecture change. No new architecture was introduced.
- Assumption: pre-existing tracker drift (Q-012, DEC-012 through
  DEC-018, FIND-014 through FIND-021) does not need
  same-session resolution and can be handled as a dedicated
  reconciliation pass.

---

## Risks

### R-023 (carried forward, active)
Phase 2 may drift into Phase 3 Capability Map or Phase 6
Workflow Design territory as the framework matures into
populated detail. Mitigation in this session:
every sub-item in `experience-architecture.md` names what it
is not and references the governing boundary test.
Keep active through Phase 2 refinement work.

### R-025 (carried forward, active)
Session close-out is applied by discipline, not enforced by
tooling. This session also surfaced tracker-backfill drift
as a related symptom (see FIND-023).
Mitigation: `workflows/sync-protocol.md` codifies the procedure
and may be extended to include tracker backfill.

### R-026 (carried forward, active)
`workflows/sync-protocol.md` references Linear MCP tools by
logical name; if those tool names change, its Tooling section
must be updated.

---

## Next Focus
1. Refine `Faraz-OS-Canon/experience-architecture.md` from
   framework to populated detail under plan → build → review,
   in a separate session:
   concrete Operating Surfaces by name,
   portal contents per persona,
   populated permission matrix rows and columns,
   concrete Cross-Domain Views.
2. Reconcile remaining tracker drift surfaced in FIND-023:
   backfill Q-012 into `open-questions.md`;
   backfill DEC-012 through DEC-018 into `decisions.md`;
   backfill FIND-014 through FIND-021 into `findings.md`
   from their originating snapshots.
3. After repo approval of this close-out, reconcile Linear
   per `workflows/sync-protocol.md`:
   mark the Phase 2 first-canon-write issue Done citing this
   snapshot; open a follow-up issue for Phase 2 framework
   population; open a follow-up issue for tracker drift
   reconciliation.
4. Carry the Future Personas placeholder and the deferred
   navigation sub-detail (notification routing, deep-linking)
   forward as marked future items.
5. Keep Phase 2 scope distinct from Phase 3 Capability Map
   and Phase 6 Workflow Design,
   per the governing boundary test
   in `experience-architecture.md`.
6. Keep Claude Project input limited to high-signal current
   files; prepare later controlled handoff to Claude Code.
