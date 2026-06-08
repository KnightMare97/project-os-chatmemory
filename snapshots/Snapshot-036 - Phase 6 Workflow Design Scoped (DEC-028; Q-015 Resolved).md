# Snapshot-036 - Phase 6 Workflow Design Scoped (DEC-028; Q-015 Resolved)

## Current Phase
Phase 11 Claude Code Operating System — operational; operating contract now
persisted in `CLAUDE.md` (commit `7f1cda3`)
Phase 6 Workflow Design — **scoped** (DEC-028); `workflows.md` not yet written
Phase 5 Knowledge & Memory Architecture — first write complete (Snapshot-035), unchanged
Phase 4 Extensibility Model — first write complete (Snapshot-030), unchanged
Phase 3 Capability Map — written (Snapshot-025); Q-015 now resolved (DEC-028)
Phase 2 Experience Architecture — complete (7-of-7, Snapshot-033), unchanged
Phase 1 Domain Discovery — Q-001 resolved (DEC-027), unchanged

## Current Topic
The Phase 6 Workflow Design question-gate (G-1 → G-7), closed by DEC-028, plus
the single boundary resolution it carried (Q-015) and the supporting
operating-contract landing in `CLAUDE.md`. This snapshot **records** what
happened; it re-decides nothing and authors no `workflows.md` content.

## Status
DEC-028 is written and verified on origin/main (commit `e9c9296`, on top of
`7f1cda3`), with the isolated `capabilities.md` flag-note refresh on top (commit
`623960e`); working tree clean. `workflows.md` is **not yet written** — the first
write is the next step and is gated.

**The Phase 6 question-gate is closed (DEC-028):**
- **Structural frame (autonomous, recorded reasoning):** G-1 logical
  orchestration altitude; G-2 a closed boundary set = a definition/altitude line
  (the selection-vs-sequence and approve-verb-vs-approval-gate tests) + seven
  cross-phase boundaries (Phase 1 split into two facets, per the DEC-027
  precedent `memory.md:198-202`); G-3 thirteen firm sub-items in three structural
  forms — seven workflow entries on the G-4 skeleton, three referenced loop/path
  patterns, three framing/construct sections — **zero deferred stubs**; G-4 the
  six-field per-workflow skeleton; G-5 non-goals; G-7 the carried set.
- **Four G-6 posture decisions (human-decided):**
  - (a) **HITL default model — bounded adoption:** field-4 uses the
    human-in-the-loop philosophy #5 mode vocabulary as the referenced owning
    definition ("hybrid by design" carried verbatim); the client-facing-publishing
    default-on checkpoint (#7) carries the verbatim override phrase "configurable
    based on workflow policy"; #6 is a cited guiding principle, never an enumerated
    rule table. Gate placement+mode = Phase 6; who-may-approve = Phase 1 / DEC-026.
  - (b) **Agent Chains — bounded orchestration construct:** owns the orchestration
    contract only; the **role-vs-identity litmus** is recorded verbatim; role
    placeholders at capability altitude only (identity-vocabulary need → escalate);
    per-step execution mode references the Phase-3 attribute + field-4 vocabulary;
    the Phase-7 agent/subagent-identity flag stays registered and untouched.
  - (c) **Workflow Runtime — bounded framing section** (not a skeleton entry,
    modeled on the Runtime-vs-Config-Time precedent): three-way "runtime"
    disambiguation; the **P6↔P7 litmus** recorded verbatim; explicit firewall list;
    semantic-only vocabulary test (engine-vocabulary need → escalate); standing
    policing note. Highest-R-028 surface.
  - (d) **Q-015 — resolved** (see Decisions / Open Questions).

## Current Topic Notes — record-only
This close-out records three landed commits from this session and the two tracker
touches of the close-out itself. No architecture was created by the snapshot.

---

## Document Updates

### DOC-089
`decisions.md` — **DEC-028 added** (commit `e9c9296`): Phase 6 Workflow Design
scope + question-gate closure; the structural frame, the four G-6 posture
decisions with their recorded conditions and the two verbatim litmuses, the G-3
sub-item classification, the G-5 non-goals, the G-7 carried set, and the Q-015
three-part resolution with venue-change note. Authored no `workflows.md` content.

### DOC-090
`open-questions.md` — **Q-015 → Resolved (DEC-028)** (same commit `e9c9296`,
same-commit tracker backfill): the three-part split, the venue-change note, the
reference-altitude knock-on note, and the KNI-21 line.

### DOC-091
`Faraz-OS-Canon/capabilities.md` — **Q-015 flag note refreshed** (`:89-93`;
isolated commit `623960e`, reference altitude): "resolved by DEC-028" (cross-item
queueing → Phase 6; atomic push + when-parameter firm Phase 3). The Publishing
capability entry itself stays atomic / order-free / unchanged.

### DOC-092
`CLAUDE.md` — **"Execution Mode and Approval Gates" section added** + Session
Close-Out reconciling line + Client Brain draft-area example refreshed (commit
`7f1cda3`): persists the direct-execution contract, the four GATED approval gates,
the AUTO/GATED split, evidence discipline, the independent-verifier + FIND-032
citation rule + same-commit tracker backfill. Procedure-file change; no
architecture introduced.

### DOC-093
`findings.md` — **FIND-033 backfilled** (this close-out): citation verification
must validate anchor *content*, not only token freshness.

### DOC-094
`Current-State.md` — Phase 6 added as scoped (DEC-028; `workflows.md` not yet
written); Q-015 marked resolved; latest snapshot = 036; Next Focus updated.

---

## Decisions

### DEC-028 (recorded; landed this session)
Phase 6 Workflow Design — scope and question-gate closure. Resolves Q-015 (only).
Records the structural frame (G-1…G-5, G-7), the four G-6 posture decisions with
their conditions and the role-vs-identity and P6↔P7 litmuses verbatim, the
thirteen-firm-sub-item classification, and the Q-015 three-part resolution
(atomic push + scheduled-publish when-parameter = firm Phase 3; cross-item
queueing/sequencing = Phase 6 orchestration) with its venue-change note. Status:
Active. No prior decision changed or superseded.

---

## Findings

### FIND-033 (new)
Citation verification must validate **anchor content**, not only token freshness.
During the DEC-028 landing, a draft citation `memory.md:196-199` was mis-anchored
(line 196 is unrelated trailing text; the range stopped before the second Phase-1
facet it claimed) — the content actually sat at `:198-202`. A stale-token sweep
does not catch this (no token shifted; the citation was wrong at authoring) and
the independent LLM verifier false-passed it. Separately, the deterministic
`89-94` sweep surfaced a **third** stale occurrence beyond the human reviewer's
two-item enumeration. Sibling to FIND-032 (same-session shift) and FIND-031
(grep-completeness). **Corrective (standing rule, extends FIND-032):** the
pre-commit verifier must byte-read each cited range and confirm it contains the
claimed content (anchor-content check), **and** must always run the deterministic
sweep rather than trusting any manual enumeration — both, not either. See
`findings.md`.

---

## Open Questions
- **Q-015 — resolved (DEC-028):** Publishing scheduling/queueing altitude.
  Atomic push and the scheduled-publish *when-parameter* are firm Phase 3;
  cross-item queueing/sequencing is Phase 6 orchestration. Venue moved from the
  `capabilities.md` write (which chose flag-not-resolve) to this gate because the
  ratified selection-vs-sequence test (DEC-025) now exists.
- **Carried, untouched (verbatim):**
  - **Q-003** — final Brand placement (open).
  - **Q-004** — Client Brain partitioning (per Client / per Brand / both),
    entangled with Q-003 (open).
  - **Q-012** — Phase 7 ↔ Phase 8 boundary; deferred until Phase 6 is complete
    (`open-questions.md:268`). Phase-6 completion is its downstream unblock
    trigger; DEC-028 does not resolve it.
  - **Q-016** — Client × Performance & Analytics View membership nuance
    (tracked separately).
  - The inherited Intelligence-Draft-v1 questions, incl. the
    insight→durable-knowledge threshold (`domains.md:1918`) — R-027.

---

## Assumptions
- Assumption: DEC-028 records but does not author `workflows.md` content; every
  sub-item is described structurally, not populated.
- Assumption: the two new litmus tests (role-vs-identity, P6↔P7) are
  boundary-drawing operationalizations of existing canon (the DEC-025
  agent-identity flag + the "engine that executes = Phase 7" principle + the
  explicit Phase-7 Runtime Architecture sub-item), not new architecture.
- Assumption: all citations in this trio are byte-accurate against post-landing
  ground truth (deterministic sweep + anchor-content check per FIND-033).

---

## Risks

### R-027 (carried forward, active — held)
No inherited Phase-1 question resolved: DEC-028 references Q-003, Q-004, and the
insight→durable-knowledge threshold (`domains.md:1918`) at altitude; resolves none.

### R-028 (carried forward, active — held, now with two active guards)
Reference altitude / overcommitment. DEC-028 holds the line on the three `[ADDED]`
sub-items via the two new verbatim litmuses (role-vs-identity for Agent Chains;
P6↔P7 for Workflow Runtime) and the escalate-don't-write-around-it rule. Workflow
Runtime is the highest-R-028 surface and carries a standing policing note.

### R-029 (carried forward, active)
Authorization-slice bleed (from DEC-026). Untouched by this scope; access
authorization is referenced, never authored (gate placement = Phase 6; who-may-
approve = Phase 1 / DEC-026). Keep active.

### R-025 / R-026 (carried forward, active)
R-025 close-out discipline applied (content read + independent verifier +
deterministic stale-token sweep **and** anchor-content check before landing;
same-commit tracker backfill for the trackers, isolated reference-altitude commit
for the Phase-3 content file). R-026 sync-protocol tooling-name watch unchanged.

---

## Next Focus
1. **Phase 6 `workflows.md` first write** (gated) — the seven firm flow entries on
   the G-4 six-field skeleton, the three referenced loop/path patterns, and the
   three framing/construct sections (Human Approval Gates, Agent Chains, Workflow
   Runtime), each honoring its recorded G-6 conditions and the two verbatim
   litmuses. Would create its own Linear work issue.
2. **Carried, none blocking:** Q-003 / Q-004 (resolve together; their own gated
   decision); Q-012 (unblocks on Phase-6 completion); Q-016; the inherited
   Phase-1 questions (R-027).
3. Other fresh, gated threads: the four Phase-4 deferred sub-items (Versioning &
   Compatibility, External Integrations, Feature Modules, Future Domains); Phase 5
   Asset Intelligence un-defer.
4. Normalization backlog (`[[normalization-pass-backlog]]`): the new item 7
   (scope the unqualified `CLAUDE.md` close-out push/commit bullet to GATED), plus
   the standing items.
5. Linear: KNI-21 → Done (landed this session, after raw-verified push).
