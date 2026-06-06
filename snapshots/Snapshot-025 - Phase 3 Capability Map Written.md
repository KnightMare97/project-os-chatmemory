# Snapshot-025 - Phase 3 Capability Map Written

## Current Phase
Phase 11 Claude Code Operating System — operational
Phase 3 Capability Map — capabilities.md written (Batch A + Batch B, all eight
capabilities); only the open Q-015 boundary remains
Phase 2 Experience Architecture — active, 5-of-7 populated (unchanged)

## Current Topic
The Phase 3 entry-writing pass (KNI-20): writing Faraz-OS-Canon/capabilities.md
from the approved DEC-024 scope, under plan → build → review, in two batches.
This is execution of an already-approved scope; it produced no new architecture
decision and resolved no open question. The session's discipline was to apply
the closed six-boundary set per entry and to preserve every inherited Phase 1
flag as still-open.

## Status
Faraz-OS-Canon/capabilities.md now records all eight capabilities (Research,
Strategy, Content Creation, Video Creation, Publishing, Analytics, Reporting,
Lead Scoring) on the DEC-024 six-field skeleton (Definition, Serves, Execution
mode, Produces, Provider dependency, Boundary notes). The file header
references — does not restate — the Governing Boundary Test
(experience-architecture.md) and the closed six-boundary set (DEC-024 /
Snapshot-024), holding the single-source discipline. The Serves field is a
Phase-3 inference at naming altitude: domains.md has no capability→domain
mapping, so each value names which domain a capability serves and never asserts
domain ownership (a Phase 1 concern).

The write was done in two reviewed batches: Batch A (Publishing, Reporting,
Content Creation, Research, Strategy; commit 9be5cbc) and Batch B (Video
Creation, Analytics, Lead Scoring; commit 288969a). The verb-test and
sequence-test were applied per entry; Strategy's predecessor ("after Research")
and the Publishing/Reporting/Content-Creation sequence leaks were excluded as
Phase 6, not encoded. Analytics is kept distinct from Reporting (compute vs
assemble) per the granularity rule, and the KPI altitude split is referenced
(experience-architecture.md:564-571), not restated.

No open question is resolved by this write, and no Phase 1 domain truth is
changed. Repository is in a stable, confirmed state.

---

## Document Updates

### DOC-054
Faraz-OS-Canon/capabilities.md created and completed — all eight capability
entries on the six-field skeleton, plus the header (Purpose, Status, Governing
boundaries by reference, How to read an entry). Written across two commits:
Batch A 9be5cbc, Batch B 288969a.

### DOC-055
capabilities.md Status line updated: drops the "Batch B pending" note, records
all eight as written, and cites Snapshot-025.

### DOC-056
Current-State.md refreshed: Phase 3 recorded as written (not just scoped);
Next Focus updated; Q-015 and the inherited Phase 1 questions carried as open.

### DOC-057
domains.md examples list (lines 184-191) — Video Creation added to the
Capability examples list, remediating FIND-026. Applied as its own separate
commit with an explicit examples-list-touch-up message. This is a completion of
an illustrative list, NOT a Phase 1 domain-truth change; no other domains.md
content is touched.

---

## Decisions
No new decision this session. The write executed DEC-024 (the approved Phase 3
scope); no new decision was required or made.

---

## Findings
No new finding this session.
- FIND-026 (the domains.md examples-list / phase-map asymmetry) is carried from
  Snapshot-024; its remediation (adding Video Creation to domains.md:184-191) is
  applied as a separate commit in this close-out. The finding stands as the
  record of why the touch-up was made.

---

## Open Questions
No open question is resolved or newly opened by this write. All carried forward,
still pending:
- Q-015 (new in Snapshot-024) — Publishing scheduling/queueing altitude
  (P3 ↔ P6). Batch A's Publishing entry flagged it and did not default it; it
  remains open, tracked in Linear as KNI-21 (Todo).
- Inherited Phase 1 questions, referenced by the entries but NOT resolved:
  domains.md:1914-1915 (Intelligence vs Analytics/Reporting capability),
  domains.md:1916 (when an insight becomes durable knowledge),
  domains.md:1917-1918 (lead scoring home — Intelligence vs CRM-local).
- Q-011 resolved; Q-012 deferred (KNI-11); Q-013 deferred (repo-only);
  Q-014 deferred (KNI-16).

---

## Assumptions
- Assumption: capabilities.md records work against the approved DEC-024 scope
  only; no capability was added, dropped, or redefined beyond the firm eight.
- Assumption: the Serves field is a Phase-3 inference pending confirmation, not
  asserted domain truth; no Phase 1 ownership was established by this file.
- Assumption: no Phase 1 domain truth, ownership, or boundary is changed by the
  capabilities.md write. The separate domains.md commit is an examples-list
  touch-up only.
- Assumption: Phase 2 is unchanged and remains 5-of-7 populated.

---

## Risks

### R-027 (carried forward, active — held this session)
The entry-writing pass could have silently resolved an inherited Phase 1 open
question. Mitigation held: every inherited flag (domains.md:1914-1915, :1916,
:1917-1918) and Q-015 is preserved as still-open in the entries and verified in
review; none was upgraded to a resolution. Keep active for any later Phase 3
edits.

### R-023 (carried forward, active — reduced)
Phase 2 / Phase 3 / Phase 6 altitude drift. The capabilities.md write was the
main exercise of this risk; mitigation held via the closed six-boundary set and
the verb-test / sequence-test applied per entry, reviewed batch by batch. Keep
active.

### R-025 (carried forward, active)
Session close-out is applied by discipline; the propose-then-review gate was
followed (two batch reviews plus this close-out).

### R-026 (carried forward, active)
workflows/sync-protocol.md references Linear MCP tools by logical name; update
its Tooling section if those names change.

---

## Next Focus
1. Phase 3 capabilities.md is written (all eight). The remaining Phase 3 open
   item is Q-015 (Publishing scheduling/queueing altitude, P3 ↔ P6) — a
   deliberate decision when it surfaces, tracked as KNI-21. The three inherited
   Phase 1 questions stay referenced, not resolved, pending their owning Phase 1
   work.
2. Reconcile Linear: KNI-20 → Done citing Snapshot-025; KNI-21 stays Todo
   (Q-015 is still open); the Phase 3 milestone reflects the write.
3. Phase 2 remains 5-of-7 populated: Channel Behaviors soft-blocked on Phase 4
   (KNI-18); Permission Matrix blocked on Phase 1 Governance (Q-014 / KNI-16);
   the three Operating-Surface flags stay parked; Future Personas and the
   deferred navigation sub-detail carry forward.
4. The Serves-field inferences in capabilities.md are pending confirmation
   against Phase 1 if/when capability→domain mapping is made concrete; they are
   marked as inference, not domain truth.
