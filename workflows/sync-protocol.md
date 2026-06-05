# Linear ↔ GitHub Sync Protocol

## Purpose
This file is the executable runbook for keeping the Faraz OS
GitHub repository and the Linear board in sync.

It is written for the AI executor (Claude),
not as general prose.
Follow it literally at session close-out
and whenever repository truth and Linear may have diverged.

It implements the Session Close-Out and Sync Discipline
in `CLAUDE.md` (DEC-016) and the draft-plus-review model (DEC-011).

This is a Phase 11 operating-method artifact.
It governs *how* sync happens.
It must not invent or reinterpret architecture content.

---

## Authority Model (non-negotiable)
1. **GitHub repository is the source of truth.**
   Snapshots, `Current-State.md`, `Faraz-OS-Canon.md`,
   `domains.md`, `open-questions.md`, `decisions.md`,
   and `findings.md` are the system of record.
2. **Linear is execution tracking only.**
   It mirrors repository truth. It never originates it.
3. **GitHub wins on any conflict.**
   When Linear and the repo disagree, the repo is correct
   and Linear is updated to match — never the reverse.
4. **Divergence is never silent.**
   Any deliberate gap between Linear and the repo
   must be stated out loud in the review step and,
   where it lives on, recorded in the repo (snapshot or
   `open-questions.md`), not only in Linear.

If a sync action would change architecture meaning,
ownership, classification, or a boundary,
stop. That is content-phase work, not sync work.

---

## Fixed Coordinates (verify, don't assume)
These are stable identifiers as of the last sync.
Re-confirm with a read before each run; treat the repo
phase map in `Faraz-OS-Canon.md` as authoritative if they differ.

- **Team:** `Knightmare` (key `KNI`)
- **Project:** `Faraz OS Architecture Progression`
- **Milestones (one per active architecture phase):**
  - `Phase 1 — Domain Discovery`
  - `Phase 2 — Experience Architecture`
  - Add a new milestone only when a phase becomes active in canon.
- **Statuses:** `Backlog`, `Todo`, `In Progress`,
  `In Review`, `Done`, `Canceled`, `Duplicate`
- **Label taxonomy (locked — do not invent new labels
  without an explicit decision):**
  - Parent `Type`: `documentation`, `scoping`, `boundary`,
    `architecture`, `snapshot`, `canon`
  - Parent `Phase`: `Phase 1`, `Phase 2`
  - The default `Bug` / `Feature` / `Improvement` labels
    are unused for this project; do not apply them.

---

## Canonical Mapping (repo concept → Linear object)
This is the heart of the protocol. Every Linear write
must trace back to a repository fact through this table.

| Repository concept | Linear representation |
|---|---|
| Architecture phase (canon) | Milestone, plus `Phase N` label |
| Open Question (`Q-0NN`) | Issue, labeled `boundary` (or fit type), referencing the Q-id |
| Risk (`R-0NN`) that needs action | Issue referencing the R-id; if purely informational, leave in repo only |
| Decision (`DEC-0NN`) | NOT a standalone issue. It closes/creates issues; cite it in the issue, not as its own ticket |
| Finding (`FIND-0NN`) | NOT an issue by default. Findings live in `findings.md` / snapshots |
| Snapshot creation task | Issue labeled `snapshot` |
| Canon/phase-map edit | Issue labeled `canon` |
| Memory-file upkeep | Issue labeled `documentation` |
| Scoping / question-gate work | Issue labeled `scoping` |
| Architecture content work | Issue labeled `architecture` |

Mapping rules:
- An issue title should name the work, and its description
  must cite the repo anchor it derives from
  (snapshot id, `Q-0NN`, `R-0NN`, `DEC-0NN`, or file).
- Deferral is expressed as **Canceled** with a description
  note saying when to re-open (see KNI-11 / Q-012 as the
  reference pattern). It is not a status of its own.
- Completed repo work → issue **Done** with `completedAt`,
  description annotated with the snapshot id that confirms it.
- Onboarding/sample issues (the original `KNI-1..4` template
  tickets) are not project work; leave them Canceled.

### Status semantics (repo state → Linear status)
- Work not yet started, still relevant → `Todo`
- Actively being worked this session → `In Progress`
- Draft proposed, awaiting human review → `In Review`
- Confirmed complete by a snapshot → `Done`
- Superseded / deferred / won't-do → `Canceled` (+ note)
- Backlog is for genuinely-later work with no active phase;
  prefer Canceled-with-reopen-note for deferred boundary
  questions so the deferral reason stays visible.

---

## Tooling
Use the Linear MCP tools. Logical names used here
(the concrete tool ids carry a session-specific prefix —
resolve them at runtime):

- Read: `list_teams`, `list_projects`, `list_issues`,
  `get_issue`, `list_issue_statuses`, `list_issue_labels`,
  `list_milestones`, `list_comments`
- Write: `save_issue` (create/update issues — status,
  priority, labels, milestone, relations, description),
  `save_comment` (audit note on an issue),
  `save_milestone`, `save_project`

Read before every write. Never write blind.

---

## The Close-Out Sync Procedure
Run this at the close of any session that produced a
decision, finding, structural change, or meaningful progress.
Repository steps (1–3) come first because the repo is the
source of truth; Linear (step 4) reconciles to the result.

### Step 0 — Pre-flight (read-only)
1. `git pull` (or confirm the working tree is current)
   so you are reconciling against the latest repo truth,
   not a stale local copy.
2. Read the latest snapshot, `Current-State.md`, and
   `open-questions.md`. These define the target state.
3. Read the live board: `list_issues` for team `Knightmare`
   (include the project), plus `list_issue_labels` and
   `list_issue_statuses`. Build the current picture.

### Step 1 — Create the new snapshot (repo)
1. Determine the next number: latest `Snapshot-{NNN}` + 1,
   zero-padded to three digits.
2. Write `snapshots/Snapshot-{NNN} - {title}.md` using the
   established section order: Current Phase, Current Topic,
   Status, Document Updates, Decisions, Findings,
   Open Questions, Assumptions, Risks, Next Focus.
3. Record what happened. Do not finalize unresolved
   boundaries. Preserve Assumption / Open Question / Risk
   markers exactly.

### Step 2 — Refresh `Current-State.md` (repo)
Update it to match the new snapshot's reality:
active phase, completed work, current next focus,
open questions. Prefer minimal diffs.

### Step 3 — Propose repo changes for review (gate)
Present the snapshot content and the `Current-State.md`
diff for human review. **Do not commit or push without
explicit approval.** This is the DEC-011 gate.
Linear is not touched until repo changes are approved,
so the board never mirrors an unapproved draft.

### Step 4 — Reconcile Linear to the approved snapshot
Only after repo changes are approved. For each item,
read first, then `save_issue`:

1. **Phases / milestones.** If a new phase became active in
   canon, create its milestone and `Phase N` label. Ensure
   each active-phase issue carries the right milestone + label.
2. **Completed work.** Every task the snapshot marks done →
   set issue `Done`; in the description, cite the snapshot id
   (e.g. "Done — Snapshot-{NNN}").
3. **Open Questions.** For each `Q-0NN` in `open-questions.md`:
   - active → an open issue (`Todo`/`In Progress`),
     correct priority, `boundary` label, cites the Q-id.
   - deferred → `Canceled` with a note stating the re-open
     trigger (pattern: KNI-11 / Q-012, "re-open when Phase 6
     complete").
   - resolved → `Done`, citing the deciding `DEC-0NN`.
4. **Risks.** Actionable `R-0NN` → ensure a tracking issue
   exists (pattern: R-022 → KNI-9). Informational risks stay
   in the repo only.
5. **Priorities.** Reflect the snapshot's emphasis. A question
   that blocks the active phase is `High` (e.g. Q-011/KNI-10).
6. **Blocking relations.** If the snapshot says X blocks Y,
   set the blocks/blocked-by relation (e.g. Q-011 blocks the
   Phase 2 scoping issue).
7. **Stale/noise issues.** Leave template onboarding issues
   Canceled. Do not resurrect them.
8. **Audit note.** On each materially changed issue, add a
   short `save_comment` citing the snapshot id as the reason
   for the change.

### Step 5 — Verify and report
1. Re-read the board (`list_issues`) and diff against the
   snapshot. Every open issue should map to a live repo
   concern; every repo open question should map to an issue
   (or a stated, recorded exception).
2. Report to the human: what changed in Linear, what was
   intentionally left divergent and why, and confirm the
   board now mirrors the snapshot.

---

## Reconciliation Algorithm (the diff)
Think of sync as a three-way comparison each run:

1. **Repo open concerns** = active `Q-0NN` + actionable
   `R-0NN` + the snapshot's Next Focus items.
2. **Linear open issues** = non-Done, non-Canceled issues
   in the project.
3. Compute:
   - In repo, not in Linear → create issue.
   - In Linear, not in repo → the repo resolved/dropped it;
     set `Done` (if completed) or `Canceled` (if dropped),
     citing the snapshot. Never delete history.
   - In both → reconcile status, priority, labels,
     milestone, relations to the repo's version.

GitHub wins every cell of this diff.

---

## Conflict Resolution
- Linear says done, repo says open → repo wins; reopen the
  issue or record the gap. Investigate why Linear drifted.
- Linear has an issue with no repo anchor → either it predates
  a repo entry (add the anchor / create the repo item via the
  proper content-phase workflow) or it is noise (Cancel it).
- Two issues cover the same concern → keep one, mark the other
  `Duplicate`, point it at the survivor.
- Priority/label disagreement → the snapshot's framing wins.

---

## Hard Stops (do NOT do these)
- Do not commit or push repo changes without explicit approval.
- Do not edit `domains.md`, `Faraz-OS-Canon.md`, or any phase
  content file as part of "sync." Sync touches snapshots,
  `Current-State.md`, and Linear only. Content changes go
  through the owning content phase.
- Do not finalize an unresolved boundary in a snapshot or by
  closing its Linear issue. Closing the *question* requires a
  recorded `DEC-0NN`.
- Do not invent Linear labels, statuses, or milestones outside
  the locked taxonomy without an explicit decision.
- Do not delete issues or snapshots. Use Canceled / Duplicate /
  archive to preserve history.
- Do not treat Linear as the source for any architecture fact.

---

## Worked Example (last completed cycle)
Reference pattern from the Snapshot-010 → board reconciliation:
- Phase 1 tasks confirmed done in the snapshot → `KNI-5`,
  `KNI-6`, `KNI-7` set `Done`, descriptions cite Snapshot-010.
- `Q-011` active and blocking Phase 2 → `KNI-10`, `Todo`,
  `High`, labels `boundary` + `Phase 2`, milestone Phase 2,
  set to block `KNI-8` (Phase 2 scoping).
- `R-022` (draft boundaries must stay open) → `KNI-9`, `Todo`,
  `Medium`, labels `boundary` + `Phase 1`.
- `Q-012` deferred → `KNI-11` `Canceled` with a re-open-after-
  Phase-6 note; it lives in `open-questions.md` meanwhile.
- Onboarding templates `KNI-1..4` → left `Canceled`.
- A redundant workflow-stage label was removed, leaving the
  clean two-group (`Type` / `Phase`) taxonomy above.

The new entry this cycle is Snapshot-011 itself, which codified
this discipline; the next cycle's snapshot should cite this
file as the procedure it followed.

---

## Maintenance
Keep this file procedural and current.
When the label taxonomy, status set, milestone list, or the
mapping table changes, update the Fixed Coordinates and the
Canonical Mapping here in the same session, and note the change
in that session's snapshot. This file is the one canonical place
for the sync procedure — do not duplicate it into `CLAUDE.md`
or the snapshot archive.
