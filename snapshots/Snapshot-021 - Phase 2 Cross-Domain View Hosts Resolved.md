# Snapshot-021 - Phase 2 Cross-Domain View Hosts Resolved

## Current Phase
Phase 11 Claude Code Operating System — operational
Phase 2 Experience Architecture — active; the DEC-020 host follow-up
(two deferred Cross-Domain View hosts + operator-finance gap) resolved
this session

## Current Topic
DEC-020 follow-up: assign host surfaces to the two Cross-Domain Views whose
hosts DEC-022 deferred (Engagement Health View, Client Engagement Summary
View) and resolve the operator-finance gap. A DEC-020 amendment session by
authority; resolved by scoped reuse with no new firm surface, so the
inventory is unchanged. Plan-then-write with a question gate; the canon was
written this session.

## Status
Both deferred host surfaces are assigned to the Reports & Analytics Surface
(Engagement Health View — operator/manager scope; Client Engagement Summary
View — client-scoped), by scoped reuse; no new Operating Surface was added.
The Reports & Analytics Surface now hosts four distinct, separately named
views. The operator-finance gap is resolved for the per-engagement
financial-context need (the operator reaches engagement financial context
via the Engagement Health View on a surface it already holds) and is removed
from the flagged-surface list; a later cross-engagement rollup need would be
a new item, not a reopening. Recorded as DEC-023, which does not amend the
firm inventory (still sixteen surfaces). Three Operating-Surface flags
remain (Client Profile, System Configuration / Settings, Onboarding). The
Permission Matrix stays unpopulated and entitlement deferred. Repository is
in a stable, confirmed state.

---

## Document Updates

### DOC-044
Faraz-OS-Canon/experience-architecture.md updated (single-file,
minimal-diff; +40 / −25):
- Cross-Domain Views inventory rows 5 and 6: host cells changed from
  "deferred (DEC-020 follow-up)" to the Reports & Analytics Surface
  (operator/manager scope; client-scoped, respectively).
- The "hosts two distinct views" note → "hosts four distinct views",
  propagated consistently to the Operating Surfaces inventory row 7 and the
  Operator / Manager / Client portal table notes (each persona-accurate).
- The Cross-Domain Views "Deferred and flagged" subsection renamed to
  "Host assignments" and rewritten to record the resolution (scoped reuse;
  no new surface; operator-finance gap resolved for the per-engagement need;
  cross-engagement rollup would be a new item).
- Open and Deferred Items "Flagged — Operating Surfaces carried forward"
  reduced Four → Three (operator-finance gap removed, with a resolution
  note). Client Profile, System Configuration / Settings, and Onboarding
  unchanged.
- Provenance: added the DEC-023 / Snapshot-021 reference.

### DOC-045
Current-State.md updated to record the DEC-020 follow-up as resolved (host
assignments + operator-finance gap), with KNI-14 unchanged (In Progress;
Permission Matrix the only open item).

---

## Decisions

### DEC-023
The two deferred Cross-Domain View host surfaces and the operator-finance
gap (the DEC-020 follow-up) are resolved. Engagement Health View and Client
Engagement Summary View are hosted on the Reports & Analytics Surface by
scoped reuse; no new firm surface (inventory unchanged at sixteen). The
operator-finance gap is resolved for the per-engagement financial-context
need via the Engagement Health View on the Reports & Analytics Surface; a
later cross-engagement rollup need is a new item, not a reopening. Recorded
in full in decisions.md; builds on DEC-020 and DEC-022.

---

## Findings
No new findings promoted to findings.md this session.
- Noted (recorded here only): the Reports & Analytics Surface now hosts four
  Cross-Domain Views — a mild host-concentration observation. Defensible
  (it is the analytics / composition surface), informational only, no
  action. Revisit only if the count keeps growing.

---

## Open Questions
No new open questions this session.
- Q-011 resolved; Q-012 deferred; Q-013 deferred (all unchanged).

---

## Assumptions
- Assumption: both resolutions are scoped reuse; no new firm Operating
  Surface was added, so DEC-020's inventory is unchanged.
- Assumption: the operator-finance gap is resolved only for the
  per-engagement financial-context need; a cross-engagement financial
  rollup, if it surfaces, is a new item.
- Assumption: no Phase 1 domain truth, ownership, or boundary was modified;
  the host assignments reference Phase 1 / 3 / 5 concepts at reference
  altitude only.
- Assumption: entitlement remains deferred to the Permission Matrix /
  Phase 1 Governance; this session decided where the views live, not who
  sees them.

---

## Risks

### R-023 (carried forward, active, reduced)
Phase 2 may drift into Phase 3 / Phase 6 territory. Mitigation held: the
host assignments are presentation placement only; views remain consume-only;
entitlement stays deferred. Keep active.

### R-025 (carried forward, active)
Session close-out is applied by discipline; the propose-then-review gate
was followed this session.

### R-026 (carried forward, active)
workflows/sync-protocol.md references Linear MCP tools by logical name;
update its Tooling section if those names change.

---

## Next Focus
1. KNI-14's only remaining item is the Permission Matrix population, which
   stays deferred until Phase 1 Governance rules in domains.md are concrete.
   KNI-14 stays In Progress.
2. With this follow-up resolved, the Phase 2 Cross-Domain Views work
   (inventory, hosts, operator-finance gap) is complete; the three remaining
   Operating-Surface flags (Client Profile, System Configuration / Settings,
   Onboarding) stay flagged for their own future sessions.
3. Carry the Future Personas placeholder and the deferred navigation
   sub-detail forward as marked future items.
4. Keep Claude Project input limited to high-signal current files; prepare
   later controlled handoff to Claude Code.
