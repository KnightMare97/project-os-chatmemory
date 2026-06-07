# Snapshot-030 - Phase 4 Extensibility Batch C Written; First Write Complete

## Current Phase
Phase 11 Claude Code Operating System — operational
Phase 4 Extensibility Model — Batch C written this session; **all eight in-scope
entries of `extensibility.md` are now written** (first write complete). Four
deferred sub-items remain flagged stubs.
Phase 3 Capability Map — written (Snapshot-025), unchanged
Phase 2 Experience Architecture — 5-of-7 populated (Snapshot-026), unchanged;
Channel Behaviors (KNI-18) unblockable

## Current Topic
Execution of Batch C of the DEC-025-approved batched-write plan for
`Faraz-OS-Canon/extensibility.md` (KNI-23): the Model and AI Model Routing
entries, the Runtime vs Config-Time Extensions framing section, and the
Status-section update. With Batch C, the Phase 4 first write (eight in-scope
sub-items) is complete. This snapshot records the write at reference altitude; it
re-decides nothing — DEC-025 is the decision of record.

## Status
Batch C is committed (commit `082b261`, on top of `bbf4ea2`). Working tree clean.
`extensibility.md` now carries all eight in-scope entries: Provider Model, Channel
Model, Extension Contracts, Permission, Plugin Model, Model, AI Model Routing, and
the Runtime vs Config-Time Extensions framing section.

Batch C content:
- **Model** — the AI-model abstraction as a swappable unit, kept distinct from
  Provider Model (the general provider contract) and AI Model Routing (the
  selection policy), per the locked distinction set / OQ-E. Backed by the
  multi-model principle (`ai-philosophy.md:18-19`). Six-field skeleton; contract
  surface at altitude.
- **AI Model Routing** — the order-free, policy-driven selection mechanism over
  models / providers / agents / paths. Its ↔ Phase 6 boundary note quotes the
  DEC-025 **selection-vs-sequence test verbatim** (routing = Phase 4 order-free;
  orchestration = Phase 6). The "risk" routing dimension references, not authors,
  Governance/safety policy. The Philosophy-#7 refinement (orchestration → Phase 6)
  is presented as the DEC-025 reading plus the registered annotation flag — no
  Phase 0 doc edit.
- **Runtime vs Config-Time Extensions** — a **framing section** (OQ-K) defining the
  cross-cutting attribute (Philosophy #10), explicitly not an enumeration and not
  a six-field entry; the per-entry Runtime vs Config-Time field carries the mode.

Each new entry is on the six-field skeleton (the framing section excepted by
design); the six Philosophy-#8 governance categories are named verbatim where
touched; citations were checked for wrap-around precision. An independent verifier
passed the batch (OQ-E two-entry structure; OQ-K framing section; the verbatim
selection-vs-sequence test; the four operational rules; R-027/R-028; Batch A/B
consistency). No content-read change was required (approved as written).

Batch C resolves no Phase 1 open question and writes no content beyond its scope.

The four deferred sub-items (Versioning & Compatibility, External Integrations,
Feature Modules, Future Domains) remain flagged stubs by design; each becomes its
own work item if and when un-deferred.

---

## Document Updates

### DOC-067
`Faraz-OS-Canon/extensibility.md` — Batch C written (commit `082b261`): the Model
and AI Model Routing entries and the Runtime vs Config-Time Extensions framing
section inserted after Plugin Model, and the Status section updated to "all eight
in-scope entries written (Batches A–C)."

### DOC-068
`Current-State.md` refreshed in this close-out: the Phase 4 block now records the
first write complete (all eight in-scope entries), and Next Focus records KNI-23's
done-condition met (moves to Done after this push) with the next Phase 4 decisions
(KNI-18 reopen; un-deferring sub-items) flagged as fresh gated topics.

---

## Decisions
No new decision. Batch C executes the already-committed DEC-025 (Active); it is
referenced here, not re-decided. No DEC changed or superseded.

---

## Findings
No new finding.

---

## Open Questions
No open question is resolved or newly opened. Carried, referenced not resolved:
- Registered Phase 4 open flags: agent/subagent identity (likely Phase 7);
  safety-controls vocabulary (`extensibility-philosophy.md:30` vs
  `domains.md:2189/2226/2262`); the optional philosophy-#7 annotation
  (`extensibility-philosophy.md:25`); the repo-wide inherited-question citation
  drift (FIND-028).
- Inherited Phase 1 questions: `domains.md:1915-1916`, `:1917`, `:1918-1919`, and
  Q-014 (Permission Matrix ↔ Governance).
- Q-001 / Q-004 (Client Brain) — open, untouched. Q-015 (KNI-21) — open.

---

## Assumptions
- Assumption: Batch C is faithful execution of DEC-025; no Phase 1 truth,
  ownership, or boundary is changed, and no open question is resolved.
- Assumption: the Runtime vs Config-Time framing section defines the attribute
  only (OQ-K) and assigns no modes; the per-entry fields carry the mode.
- Assumption: "first write complete" means the eight in-scope entries are written;
  the four deferred sub-items remain out of scope for this write by design.

---

## Risks

### R-028 (carried forward, active — held)
Reference-altitude overcommitment. Held in Batch C: Governance touchpoints name
only the six Philosophy-#8 categories at altitude; the Routing "risk" dimension
references rather than authors safety policy; the Philosophy-#7 refinement is the
DEC-025 reading plus a flag, not a Phase 0 doc edit. Keep active for any later
Phase 4 work (deferred sub-items).

### R-027 (carried forward, active — held)
No inherited Phase 1 question was resolved or narrowed across Batches A–C; each is
referenced as open. Keep active.

### R-023 (carried forward, active — exercised and held)
Phase 4 ↔ Phase 6 altitude drift (routing vs orchestration) — the sharpest test
for the whole phase, exercised in the AI Model Routing entry via the verbatim
selection-vs-sequence test. Held. Carry forward: when Phase 6 is written,
cross-check the selection-vs-sequence test against the Phase 3 sequence-test for
consistency.

### R-026 (carried forward, active)
`workflows/sync-protocol.md` references Linear MCP tools by logical name; update
the Tooling section if tool names change.

### R-025 (carried forward, active)
Close-out applied by discipline under the standing reduced-check-in mode: Batch C
had one content read before landing; this record close-out follows an independent
verifier pass.

---

## Next Focus
1. **Phase 4 first write is complete.** No unblocked Phase 4 in-scope content
   remains. Remaining Phase 4 work is the four deferred sub-items (Versioning &
   Compatibility, External Integrations, Feature Modules, Future Domains), each a
   fresh gated topic if/when un-deferred; Future Domains stays a marked-future
   placeholder.
2. **KNI-23 → Done** (gated structural Linear change, approved): applied only
   after this close-out push is verified on origin/main. Its done-condition (all
   eight in-scope entries written per DEC-025) is met; the deferred stubs are out
   of the issue's scope by design and become new issues if un-deferred.
3. **KNI-18 (Phase 2 Channel Behaviors)** stays Canceled-with-reopen; the Channel
   Model now exists and meets its acceptance test, but reopening to write Channel
   Behaviors is a **fresh gated work decision awaiting explicit human
   green-light** — not auto-reopened by this close-out.
4. Carry the registered open flags and inherited Phase 1 questions forward,
   unresolved.
