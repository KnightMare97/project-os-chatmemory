# Snapshot-028 - Phase 4 Extensibility Batch A Written

## Current Phase
Phase 11 Claude Code Operating System — operational
Phase 4 Extensibility Model — Batch A of `extensibility.md` written this session;
Batches B and C pending
Phase 3 Capability Map — written (Snapshot-025), unchanged
Phase 2 Experience Architecture — 5-of-7 populated (Snapshot-026), unchanged;
Channel Behaviors (KNI-18) now unblockable

## Current Topic
Execution of Batch A of the DEC-025-approved batched-write plan for
`Faraz-OS-Canon/extensibility.md` (KNI-23): the file skeleton plus the Provider
Model and Channel Model entries, the deferred-sub-item stubs, the non-goals, and
the open/inherited flags. This snapshot records the write at reference altitude;
it re-decides nothing — DEC-025 is the decision of record.

## Status
`Faraz-OS-Canon/extensibility.md` is created and committed (commit `8e921a8`, on
top of `e04a9cc`). Working tree clean.

Batch A content:
- File skeleton — Purpose; Status; Governing rules (referenced, not restated —
  cites DEC-025, the Governing Boundary Test, Phase-0 Philosophy, and the
  permission triad via DEC-019/FIND-022 stating only Phase 4's altitude per the
  hybrid rule); How to read an entry (the six-field skeleton).
- **Provider Model** — on the six-field skeleton; the contract for any swappable
  external provider; Contract surface kept at altitude (references Philosophy #4 /
  Extension Contracts without specifying it — the contract-altitude rule held, the
  Provider entry was not deepened to compensate for Extension Contracts being a
  Batch B item).
- **Channel Model** (the Batch A binding deliverable) — on the six-field skeleton
  plus the DEC-025 four-item minimum: an evidence-grounded typed taxonomy (one
  category, "outbound content channel", grounded in Publishing
  `capabilities.md:82-83`; platforms illustrative only per `non-goals.md:9`;
  further categories explicitly not invented, R-028); the three experience
  attributes mapped 1:1 to `experience-architecture.md:696-698` (format/media
  constraints · preview affordance · notification capability); the
  Provider-Model-specialization statement marked a DEC-025 inference; and the
  explicit deferral boundary (integration mechanics → External Integrations). The
  entry meets the DEC-025 acceptance test, quoted verbatim in the entry.
- Deferred-sub-item stubs (Versioning & Compatibility, External Integrations,
  Feature Modules, Future Domains — flagged, no deep content); Non-goals; Open and
  inherited flags.

One content-read fix was applied before landing: the Governing-rules permission
line was corrected to state only Phase 4's altitude and reference the triad
(DEC-019/FIND-022), per DEC-025's hybrid rule, rather than restating all three
altitudes. An independent verifier passed the batch (DEC-025 grounding; six-field
skeleton; the four operational rules checkable per entry; the acceptance test;
R-027/R-028; byte-accurate citations).

Batch A resolves no Phase 1 open question and writes no content beyond its scope.

---

## Document Updates

### DOC-063
`Faraz-OS-Canon/extensibility.md` created (commit `8e921a8`) — Batch A: file
skeleton, Provider Model, Channel Model, deferred stubs, non-goals, open flags.
First canon content of Phase 4.

### DOC-064
`Current-State.md` refreshed in this close-out: the Phase 4 block now records
Batch A written (skeleton + Provider Model + Channel Model; Channel Model meets
the acceptance test; KNI-18 unblockable) and Next Focus points at Batch B.
Additive/minimal edits.

---

## Decisions
No new decision. Batch A executes the already-committed DEC-025 (Active); it is
referenced here, not re-decided. No DEC changed or superseded.

---

## Findings
No new finding. (The single-category channel taxonomy is the evidence-grounded
floor anticipated by DEC-025's Channel-Model scope and the OQ-C caveat, accepted
at the content read; it is not a new finding.)

---

## Open Questions
No open question is resolved or newly opened. Carried, referenced not resolved:
- Registered Phase 4 open flags: agent/subagent identity (likely Phase 7);
  safety-controls vocabulary (`extensibility-philosophy.md:30` vs
  `domains.md:2189/2226/2262`); the optional philosophy-#7 annotation; the
  repo-wide inherited-question citation drift (FIND-028).
- Inherited Phase 1 questions: `domains.md:1915-1916`, `:1917`, `:1918-1919`, and
  Q-014 (Permission Matrix ↔ Governance).
- Q-001 / Q-004 (Client Brain) — open, untouched. Q-015 (KNI-21) — open.

---

## Assumptions
- Assumption: Batch A is faithful execution of DEC-025; no Phase 1 truth,
  ownership, or boundary is changed, and no open question is resolved.
- Assumption: the Channel-Model single-category taxonomy is the correct
  evidence-grounded floor; it grows only as domains/capabilities reference new
  channel types (no taxonomy invented).
- Assumption: the Channel-Model entry meets the DEC-025 acceptance test as read
  this session.

---

## Risks

### R-028 (carried forward, active — held)
Reference-altitude overcommitment. Held in Batch A: the permission triad is
referenced (DEC-019/FIND-022), not restated (the content-read fix enforced this);
the Channel-Model specialization is marked a DEC-025 inference, not asserted
canon; Governance touchpoints name only the six Philosophy-#8 categories at
altitude and enumerate no concrete policy. Keep active for Batches B and C —
especially the Batch B Permission entry, where the hybrid grant rule bites
hardest.

### R-027 (carried forward, active — held)
No inherited Phase 1 question was resolved or narrowed; each is referenced as
open. Keep active for Batches B and C.

### R-023 (carried forward, active)
Phase 4 ↔ Phase 6 altitude drift (routing vs orchestration). Batch A applied the
selection-vs-sequence test in the Provider/Channel boundary notes; the sharpest
exercise is Batch C (AI Model Routing). Keep active.

### R-026 (carried forward, active)
`workflows/sync-protocol.md` references Linear MCP tools by logical name; its
Fixed Coordinates were refreshed (Phase 3/4 added) and the phase-label growth
rule codified this session. Update the Tooling section if tool names change.

### R-025 (carried forward, active)
Close-out applied by discipline under the standing reduced-check-in mode: Batch A
had one content read before landing; record close-out (this snapshot +
Current-State) runs after an independent verifier pass.

---

## Next Focus
1. **Batch B** — Extension Contracts, Permission, Plugin Model. The Permission
   entry applies the hybrid grant rule hardest: state only Phase 4's grant
   altitude and reference DEC-019/FIND-022 for the triad (do not restate it).
   Extension Contracts formalizes the contract surface that Provider/Channel
   referenced at altitude in Batch A.
2. **Batch C** — Model, AI Model Routing, Runtime-vs-Config-Time framing section.
   Apply the selection-vs-sequence test hardest on AI Model Routing
   (order-free selection = Phase 4; orchestration = Phase 6).
3. **KNI-18 readiness:** the Channel Model now exists and meets its acceptance
   test, so Phase 2 Channel Behaviors is unblockable. Reopening KNI-18 is a
   structural Linear change (gated) — readiness registered, reopen deferred to an
   explicit decision.
4. Carry the registered open flags and inherited Phase 1 questions forward
   unresolved through Batches B and C.
5. KNI-23 stays In Progress until all three batches are landed.
