# Snapshot-012 - Linear-GitHub Sync Protocol Codified

## Current Phase
Phase 11 Claude Code Operating System — operational
Phase 2 Experience Architecture — active, not yet started

## Current Topic
Authoring the single canonical executable runbook for
Linear ↔ GitHub session close-out and reconciliation,
and pointing existing operating files at it.

## Status
`workflows/sync-protocol.md` has been created as the
canonical sync runbook. `Claude-Project-Workflows.md` and
`Current-State.md` now point to it without duplicating it.
This is operating-method (Phase 11) work only;
no architecture content was changed.
Repository is in a stable, confirmed state.

---

## Document Updates

### DOC-015
`workflows/sync-protocol.md` created.
It is the executable runbook implementing the
Session Close-Out and Sync Discipline (DEC-016)
and the draft-plus-review gate (DEC-011).
It defines: the authority model (GitHub source of truth,
Linear execution-only, GitHub wins), the fixed Linear
coordinates (team, project, milestones, statuses, locked
label taxonomy), the canonical repo-concept → Linear-object
mapping, the close-out procedure, a reconciliation algorithm,
conflict resolution, hard stops, and a worked example.

### DOC-016
`Claude-Project-Workflows.md` updated with a one-line
pointer to `workflows/sync-protocol.md`.
No workflow content was duplicated; the runbook remains
the single canonical place for the sync procedure.

### DOC-017
`Current-State.md` Phase 11 section updated to reference
`workflows/sync-protocol.md` as the reconciliation runbook.

---

## Decisions

### DEC-018
`workflows/sync-protocol.md` is the single canonical
procedure for Linear ↔ GitHub reconciliation.
Operating rules it fixes:
- Repository writes precede Linear writes; the human review
  gate sits between the repo draft and any commit; Linear is
  reconciled only after repo changes are approved.
- Decisions (`DEC`) and Findings (`FIND`) stay repo-only.
  Only Open Questions, actionable Risks, and work-tasks
  become Linear issues.
- Deferral is expressed as a `Canceled` issue with a
  re-open-trigger note, not a separate status.
- The Linear label taxonomy is locked to the two parent
  groups `Type` and `Phase`; new labels require an explicit
  decision.

---

## Findings

### FIND-021
The live Linear board was confirmed to mirror repository
truth as of Snapshot-010/011. Current state (Knightmare team
`KNI`, project "Faraz OS Architecture Progression"):
- `KNI-5`, `KNI-6`, `KNI-7` — Done (Phase 1 close-out).
- `KNI-8` — Phase 2 scoping, Todo, High.
- `KNI-10` — Q-011 (Phase 2 ↔ Phase 3 boundary), Todo, High,
  blocks `KNI-8`.
- `KNI-9` — R-022 (Phase 1 draft boundaries), Todo, Medium.
- `KNI-11` — Q-012 (Phase 7 ↔ Phase 8), Canceled, deferred
  until Phase 6, lives in `open-questions.md`.
- `KNI-1..4` — onboarding templates, Canceled (noise).
The board already matches the protocol's expected shape;
this snapshot did not require Linear changes beyond adding
one tracking issue for the protocol itself (see Next Focus).

---

## Assumptions

- Assumption: all changes this session are operating-method
  (Phase 11) and documentation only. No Phase 1 domain truth,
  ownership, or boundary was changed.
- Assumption: the Linear issue IDs, statuses, milestones, and
  label taxonomy recorded here are stable as of this session;
  the protocol re-verifies them by reading the board at the
  start of every run.

---

## Risks

### R-025 (carried forward, active)
The close-out rule is applied by discipline, not enforced by
tooling. A future session that changes repository content
without running the procedure can let `Current-State.md`,
the snapshot archive, and Linear drift out of sync.
Mitigation: the procedure is now codified and executable in
`workflows/sync-protocol.md`.

### R-026 (new)
`workflows/sync-protocol.md` references the Linear MCP tools
by logical name because the concrete tool ids carry a
session-specific prefix. If the Linear MCP tool names change,
the runbook's Tooling section must be updated.

### R-023 (carried forward, active)
Phase 2 Experience Architecture has canon sub-items but no
working content. If Phase 2 work begins without an explicit
scoping session, it may drift into Phase 3 Capability Map or
Phase 6 Workflow Design territory.

---

## Open Questions
No new open questions.
- Q-011 (Phase 2 ↔ Phase 3 boundary) remains open and tracked
  (`KNI-10`, High, blocking Phase 2 scope).
- Q-012 (Phase 7 ↔ Phase 8 boundary) remains deferred until
  Phase 6, in `open-questions.md`.

---

## Next Focus

1. Commit the sync-protocol changes after human approval,
   then reconcile Linear: create one tracking issue for the
   protocol (labeled `documentation`), set Done, citing this
   snapshot — per the protocol's own procedure.
2. Begin Phase 2 Experience Architecture:
   run the question-gate and scoping session (`KNI-8`)
   before producing any content for `experience-architecture.md`,
   resolving Q-011 (`KNI-10`) first as it blocks Phase 2 scope.

Use the established discipline:
- question gate first
- plan mode with scope, out-of-scope, risks
- build only after explicit approval
- preserve canonical distinctions throughout
