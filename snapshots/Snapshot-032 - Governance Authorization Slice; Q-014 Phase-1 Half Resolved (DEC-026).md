# Snapshot-032 - Governance Authorization Slice; Q-014 Phase-1 Half Resolved (DEC-026)

## Current Phase
Phase 11 Claude Code Operating System — operational
Phase 1 Domain Discovery — the Governance **authorization slice** is now accepted
and concrete (DEC-026); the rest of `Governance Draft v1` stays draft, untouched
Phase 2 Experience Architecture — 6-of-7 populated; the Permission Matrix is now
**unblocked** (its population is landing (ii), KNI-14)
Phase 4 Extensibility Model — first write complete (Snapshot-030), unchanged
Phase 3 Capability Map — written (Snapshot-025), unchanged

## Current Topic
Step A (Phase 1, landing (i)) of the Q-014 thread: a grill-me gate (G-1 through
G-7) defined the Governance authorization slice, promoted to DEC-026 and landed
together with an isolated `domains.md` edit. This snapshot records the close-out
at reference altitude; the decisions of record are in DEC-026.

## Status
DEC-026 and the `domains.md` Governance authorization slice are committed in one
isolated commit (`10822d0`, on top of `35a167e`), verified on origin/main; working
tree clean. The `domains.md` edit was **additive only** (118 insertions, 0
deletions): the new "Authorization (accepted slice — DEC-026)" subsection plus two
one-line status pointers (on the Authorization Aggregate sketch and the Access and
Authorization Control bounded context); the rest of `Governance Draft v1` is
byte-untouched and its `Draft v1` status preserved.

What landed (per DEC-026 / G-1→G-7):
- **Slice (G-1):** only the authorization rules sufficient for persona↔surface
  exposure; the rest of Governance stays draft. Slice-bleed risk **R-029** (new).
- **Rule shape (G-2):** `subject × verb × resource × condition → allow` at
  data/action altitude by reference (Phase 2 owns the surface↔resource mapping;
  the matrix derives exposure); closed evidence-derived verb set
  view/edit/approve/configure; approve-verb (Phase 1) vs approval-gate (Phase 6)
  boundary.
- **Baseline (G-3):** the human-confirmed DEC-020 reuse/portal tables ratified as
  the expected *derived projection*; the Step-B matrix population must reproduce
  them (acceptance criterion). No decided DEC-020 cell value amended; the three
  previously ambiguous/under-specified cells resolved here.
- **Conditions (G-4):** closed set of three — own-engagement (defined at altitude),
  assigned-client, engagement-relevant; Manager · Agent & Workflow Monitor resolved
  to Full-at-`view` (SysAdmin distinguished by `configure`); `managed-scope` left a
  future-evidence door.
- **Overlap (G-5):** union of allows with explicit-deny-override (existing
  allow/deny field; no new construct; zero deny rules authored).
- **Cell shape (G-6):** {Full / Scoped / —}; verb+condition detail in the rules.

An independent verifier passed twice, including **derivation spot-checks**: the
landed authorization rules + the mapping reproduce the ratified DEC-020 exposure
(the acceptance criterion applied early).

This step resolves the **Phase-1 half of Q-014**; the Phase-2 Permission Matrix
population (Q-014's consuming half) is landing (ii), a separate gated step.

---

## Document Updates

### DOC-071
`decisions.md` — DEC-026 appended (commit `10822d0`): the Governance
authorization-slice scope/decisions (G-1→G-7), resolving Q-014's Phase-1 half.

### DOC-072
`Faraz-OS-Canon/domains.md` — additive Governance authorization slice (commit
`10822d0`): the "Authorization (accepted slice — DEC-026)" subsection (enumerated
`subject × verb × resource × condition` rules projecting the ratified DEC-020
baseline, the subject-binding own-engagement conditions on external personas, and
the union+deny-override meta-rule) + two one-line status pointers. Rest of
`Governance Draft v1` byte-untouched.

### DOC-073
`Current-State.md` — Permission Matrix sub-item moved from "blocked on Q-014 /
KNI-16" to "unblocked (DEC-026; population is landing (ii), KNI-14)"; Next Focus
updated so the Permission Matrix population is the unblocked next Phase 2 step to
7-of-7.

### DOC-074
`brainstorms/2026-06-08-governance-authorization-slice.md` — created: the
question-gate capture (G-1→G-7, riders, the subject-binding refinement, the
verifier/derivation passes).

---

## Decisions
DEC-026 (Active) is the decision of record (landed in `decisions.md`, commit
`10822d0`). No other decision is made or changed by this snapshot.

**Decided-here refinement recorded (at the content read):** *subject-binding on
external personas.* The inherently subject-bound external-persona resources — a
Client's own deliverables, approval items, notifications, and billing; a
Contractor's own assignment records — carry the `own-engagement` condition at the
rule level, so the authoritative layer never authorizes cross-client or
cross-contractor access. Their Phase-2 table exposure stays *Full (primary
persona)* per the recorded acceptance-criterion precision (the table's Full = surface
exposure; cross-subject data scope lives in the rules; not divergence). Captured in
DEC-026 (G-3/G-4/G-6).

---

## Findings
No new finding. (FIND-029, the DEC-025 acceptance-test PASS, is unrelated and
already recorded; this thread's subject-binding refinement is captured in DEC-026,
not as a separate finding.)

---

## Open Questions
- **Q-014 — Phase-1 half resolved** by DEC-026 (the Governance authorization rules
  the matrix requires are concrete). The Phase-2 consuming half (matrix populated)
  completes at landing (ii). The open-questions.md entry should be updated /
  closed at the landing-(ii) close-out, when the matrix is populated and Phase 2
  reaches 7-of-7.
- Carried, untouched: Q-001 / Q-004 (Client Brain ownership); Q-015 (KNI-21);
  the inherited Intelligence-Draft-v1 Open Questions (`domains.md:1915-1919`).

---

## Assumptions
- Assumption: DEC-026 makes concrete only the authorization slice; the rest of
  `Governance Draft v1` is byte-untouched and stays draft.
- Assumption: the landed rules + the Phase-2 surface↔resource mapping reproduce
  the ratified DEC-020 exposure (verified early via derivation spot-checks; to be
  re-verified at landing (ii) against the acceptance criterion).
- Assumption: no Phase 1 draft area other than the authorization slice is changed;
  Q-001/Q-004 and the inherited questions are untouched.

---

## Risks

### R-029 (new, active)
Authorization-slice bleed. An in-slice authorization rule may reference a draft
neighbor (a condition, policy ref, or risk tier) at altitude but must not
concretize it. If a later exposure or matrix-population need cannot be stated
without finalizing a draft Governance neighbor, that is slice-bleed → escalate,
never silently absorb (the G-1 escalation rule). Watch at landing (ii) and any
later Governance work.

### R-028 (carried forward, active — held)
Reference-altitude overcommitment. Held: domain resources referenced not
redefined; verb/condition sets evidence-derived and closed; Client Brain access
authorized without touching ownership.

### R-027 (carried forward, active — held)
No inherited Phase 1 open question resolved (the Intelligence-Draft-v1 questions
`domains.md:1915-1919` untouched); Q-014 is a cross-phase dependency, not one of
them.

### R-026 (carried forward, active)
`workflows/sync-protocol.md` references Linear MCP tools by logical name; update
the Tooling section if names change.

### R-025 (carried forward, active)
Close-out applied by discipline under the standing reduced-check-in mode: DEC-026
+ the domains.md slice had two content reads (DEC, then the enumerated rules) and
two independent verifier passes before landing; this record close-out follows.

---

## Next Focus
1. **Landing (ii) — Phase 2 Permission Matrix population** (the unblocked next
   step). A separate gated content read → populate the Permission Matrix in
   `experience-architecture.md` as a read-only projection of the DEC-026
   authorization rules through the surface↔resource mapping (authors no rules,
   DEC-019/FIND-022) → verifier against the G-3 acceptance criterion (reproduces
   the ratified DEC-020 exposure) → close-out (Snapshot-033 + Current-State
   **Phase 2 → 7-of-7**) → Linear close **KNI-14**.
2. **Linear (this close-out):** **KNI-16** (the Q-014 unblock dependency) is
   closeable now — Q-014's Phase-1 half is resolved and the matrix is unblocked;
   **KNI-14** stays In Progress for landing (ii).
3. The rest of `Governance Draft v1` (policies, risk-tiering, checkpoints, audit,
   exceptions, override, routing) remains draft; concretizing any of it is its own
   future gated decision, not implied by this slice.
4. Carry R-029 (slice-bleed watch) and the registered open flags / inherited
   questions forward, unresolved.
