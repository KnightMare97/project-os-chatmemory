# Snapshot-027 - Phase 4 Extensibility Scope Defined

## Current Phase
Phase 11 Claude Code Operating System — operational
Phase 4 Extensibility Model — scope defined this session via DEC-025; no
`extensibility.md` content written yet
Phase 3 Capability Map — written (Snapshot-025), unchanged this session
Phase 2 Experience Architecture — 5-of-7 populated (Snapshot-026), unchanged

## Current Topic
An inline grill-me question-gate (OQ-E through OQ-M) that defined the Phase 4
Extensibility scope, promoted to DEC-025 and committed. This snapshot records the
outcome at reference altitude; it re-decides nothing — DEC-025 is the decision of
record.

## Status
DEC-025 is committed and verified on origin/main (commit `26bf5d0`, on top of
`64d7888`), together with the brainstorm capture
`brainstorms/2026-06-07-phase-4-extensibility.md`. Working tree clean.

DEC-025 records (scoping only): the Phase 4 definition/altitude; the in-scope
core of eight sub-items (Permission, Extension Contracts, Plugin Model, Provider
Model, Channel Model, Model, AI Model Routing, Runtime vs Config-Time) and the
four deferred-and-flagged (Versioning & Compatibility, External Integrations,
Feature Modules, Future Domains); the locked distinction set (Model / AI Model
Routing kept separate; Channel Model first-class but typed as a Provider-Model
specialization — recorded as a DEC-025 scoping inference, not pre-existing canon);
the closed boundary set (definition/altitude + six cross-phase boundaries, with
Phase 6 and Phase 7 split and Phase 1 a single Governance boundary); the
selection-vs-sequence test; the grant-altitude rule (R-028) with the six
Philosophy-#8 touchpoint categories named verbatim; the six-field per-sub-item
skeleton; the non-goals (including human identity and implementation technology);
and the Channel-Model unblock-altitude scope with its verbatim acceptance test.

DEC-025 resolves no Phase 1 open question, writes no `extensibility.md` content,
and finalizes no Phase 1 boundary. Every citation was re-verified against raw
bytes before the commit, and an independent verifier pass was run on the draft.

---

## Document Updates

### DOC-060
`decisions.md` — DEC-025 appended after DEC-024, before the Supersession Rule
(commit `26bf5d0`). Records the Phase 4 Extensibility scope. Additive; no existing
decision changed or superseded.

### DOC-061
`brainstorms/2026-06-07-phase-4-extensibility.md` — created (commit `26bf5d0`).
The question-gate capture feeding DEC-025 (grounding read, pre-gate verification,
OQ-E→OQ-M outcomes, registered directives, independent verification, open flags).

### DOC-062
`Current-State.md` — refreshed in this close-out to record Phase 4 as scoped
(DEC-025; 8-in / 4-deferred; `extensibility.md` not yet written; batched write is
next), to point latest-snapshot reality at Snapshot-027, and to update Next Focus.
Additive/minimal edits; unrelated content left untouched.

---

## Decisions
No new decision is made in this snapshot. DEC-025 (Active) is the decision of
record for the Phase 4 scope and is referenced here, not re-decided. No DEC was
changed or superseded.

---

## Findings

### FIND-028
Repo-wide citation drift on the inherited Phase 1 open-question line refs. The
`domains.md` `### Open Questions` block (header at `:1914`) holds the three
inherited questions at byte-accurate ranges `:1915-1916` (Intelligence vs
Analytics/Reporting), `:1917` (when an insight becomes durable knowledge), and
`:1918-1919` (lead-scoring home). Prior canon files cite these off by one —
`capabilities.md:116/211` use `:1914-1915` and `:220/238` use `:1917-1918`; the
same off-by-one appears in Snapshot-025/026 and `Current-State.md`. DEC-025 uses
the byte-accurate ranges and registers the drift as a minor normalization flag.
Alignment is deferred to a later normalization pass; it resolves no question and
changes no domain truth.

Tracker note (not a new finding): the active `findings.md` tracker still lacks
FIND-027 (Client Brain placement, created in Snapshot-026) and now FIND-028.
Backfilling both into `findings.md` is a tracker-reconciliation item for the
GitHub-side reconcile / Linear step, consistent with the prior tracker-backfill
pattern (Snapshot-015). The legacy FIND scheme in `snapshot-001..004` and
`Snapshot-005..007` (reaching FIND-052) is abandoned and is not the current
sequence.

---

## Open Questions
No open question is resolved or newly opened. The registered Phase 4 open flags
(carried, not resolved) are:
- Agent / subagent identity — likely Phase 7 AI Architecture
  (`experience-architecture.md:809` Workforce owns *human* identity; `:821` AI
  Architecture likely home of agent surfaces). Open cross-phase question.
- Safety-controls vocabulary — "safety controls" (`extensibility-philosophy.md:30`,
  #8) vs Governance's "safety constraints / safety rules / Safety Constraint"
  (`domains.md:2189, :2226, :2262`). Cross-doc alignment deferred.
- Philosophy #7 annotation — optional pointer on `extensibility-philosophy.md:25`
  noting the DEC-025 orchestration refinement; a Phase 0 normalization edit, not
  done by Phase 4.

Carried forward unchanged:
- Inherited Phase 1 questions, referenced not resolved: `domains.md:1915-1916`,
  `:1917`, `:1918-1919`, and Q-014 (Permission Matrix ↔ Governance).
- Q-001 / Q-004 (Client Brain ownership) — open, untouched.
- Q-015 (Publishing scheduling/queueing P3 ↔ P6) — open (KNI-21).
- Q-011 resolved; Q-012 deferred (KNI-11); Q-013 deferred (repo-only).

---

## Assumptions
- Assumption: DEC-025 records scope only; no architecture is finalized, no Phase 1
  truth, ownership, or boundary is changed, and no open question is resolved.
- Assumption: the Channel-Model-as-Provider-specialization typing is a DEC-025
  scoping inference reasoned from Philosophy #5/#6 plus the Publishing field —
  not a pre-existing canon statement.
- Assumption: the audited citations reflect `decisions.md` / `findings.md` /
  `domains.md` / the philosophy docs as read this session against raw bytes.

---

## Risks

### R-028 (carried forward, active — applied)
Reference-altitude overcommitment. DEC-025 applies the mitigation directly via the
grant-altitude rule (reference Governance at altitude, name only the #8 touchpoint
categories verbatim, never enumerate concrete policies) and by marking the
Channel-Model specialization as an inference rather than asserted canon. Keep
active for the `extensibility.md` write.

### R-027 (carried forward, active — held)
The scoping pass could have silently resolved an inherited Phase 1 question.
Mitigation held: every inherited flag (`domains.md:1915-1916`, `:1917`,
`:1918-1919`; Q-014) is preserved as still-open and is registered as inbound
demand only; none was upgraded to a resolution.

### R-023 (carried forward, active)
Phase 2 / Phase 3 / Phase 6 altitude drift — now extended to Phase 4 ↔ Phase 6
(routing vs orchestration). Mitigation: the selection-vs-sequence test and the
split P6/P7 boundaries. Keep active; cross-check against the Phase 3 sequence-test
when Phase 6 is written.

### R-026 (carried forward, active)
`workflows/sync-protocol.md` references Linear MCP tools by logical name; update
its Tooling section if those names change. Relevant to the upcoming Linear
reconciliation.

### R-025 (carried forward, active)
Session close-out applied by discipline; the propose-then-review gate was followed
(gate answered OQ by OQ; DEC-025 reviewed before commit; this close-out proposed
before any commit).

---

## Next Focus
1. Phase 4 is scoped (DEC-025); `extensibility.md` is not yet written. The next
   Phase 4 work is the batched write of the eight in-scope sub-items (à la the
   Phase 3 A/B split), prioritising the dependency-unblocking items — the Channel
   Model (KNI-18, against its verbatim acceptance test) and the Provider Model it
   specializes — then Permission, Extension Contracts, Plugin Model, Model, AI
   Model Routing, and the Runtime-vs-Config-Time framing section. Batch sequencing
   is a separate decision at write time.
2. Carry the four registered Phase 4 open flags forward as marked items
   (agent/subagent identity; safety-controls vocabulary; philosophy-#7 annotation;
   repo-wide inherited-question citation drift, FIND-028).
3. Honour the registered inbound flags during the write without resolving any
   inherited Phase 1 question: KNI-18; the eight capability provider-dependencies
   (`capabilities.md:83,106,128,150,166,179,199,229`); Video Creation tooling.
4. Tracker reconciliation (GitHub-side + Linear): backfill `findings.md` with
   FIND-027 (Snapshot-026) and FIND-028 (this snapshot); reconcile Linear against
   this snapshot (Phase 4 scoped; KNI-18 still soft-blocked until the Channel
   Model is written). GitHub remains source of truth.
5. Keep Phase 2 (5-of-7) and Phase 3 (written) unchanged; both remaining Phase 2
   sub-items stay blocked (Permission Matrix on Q-014 / KNI-16; Channel Behaviors
   on the Phase 4 Channel Model / KNI-18 — now unblockable once the Channel Model
   is written).
6. Do not write `extensibility.md` until its batched-write plan is approved.
