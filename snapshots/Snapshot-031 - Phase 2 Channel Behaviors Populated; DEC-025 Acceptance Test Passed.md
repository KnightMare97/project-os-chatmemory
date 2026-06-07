# Snapshot-031 - Phase 2 Channel Behaviors Populated; DEC-025 Acceptance Test Passed

## Current Phase
Phase 11 Claude Code Operating System — operational
Phase 2 Experience Architecture — Channel Behaviors populated this session;
**Phase 2 is now 6-of-7 populated** (only the Permission Matrix remains, blocked)
Phase 4 Extensibility Model — first write complete (Snapshot-030), unchanged
this session; its Channel Model was the input consumed here
Phase 3 Capability Map — written (Snapshot-025), unchanged

## Current Topic
Reopening KNI-18 and populating the Phase 2 Channel Behaviors sub-item per channel
type, using only the landed Phase 4 Channel Model — its taxonomy and three
experience attributes. This was the first real trial of the DEC-025 Channel Model
acceptance test. This snapshot records the write and the trial result at reference
altitude; it re-decides nothing.

## Status
Channel Behaviors content is committed (commit `9cf4b63`, on top of `c2901b7`).
Working tree clean.

The `## Channel Behaviors` section of `experience-architecture.md` now carries a
"Behaviors by channel type" subsection populating, for the one channel type in the
Phase 4 Channel Model taxonomy (outbound content channel), the three Phase 2
dimensions on the human-experience side:
- Rendering differences ← the Channel Model's *format / media constraints*
  attribute;
- Preview behavior ← the *preview affordance* attribute;
- Notification UX ← the *notification capability* attribute.
Each is keyed 1:1 to its attribute. The structure grows with the taxonomy (a new
channel type adds a behavior set). No channel type was invented; platforms remain
illustrative only. Concrete per-platform constraint values (Phase 4 / External
Integrations) and notification *events* (Phase 6) are referenced at altitude, not
defined here.

**DEC-025 acceptance test — first trial result: PASS.** The write was producible
using only the Channel Model taxonomy plus the three experience attributes, with
no further Phase 4 content required. An independent verifier ran the trial as an
explicit adversarial check and found no hidden dependency on un-provided Phase 4
content (no fourth attribute, no second type, no integration detail, no event
definition silently required). The OQ-C unblock-altitude decision held under real
load; no escalation was needed.

Phase 2 is now **6-of-7 populated**. Only the Permission Matrix remains, blocked
on concrete Phase 1 Governance rules (Q-014 / KNI-16).

---

## Document Updates

### DOC-069
`Faraz-OS-Canon/experience-architecture.md` — Channel Behaviors populated (commit
`9cf4b63`): a "Behaviors by channel type" subsection added to the Channel
Behaviors section (outbound content channel: rendering / preview / notification
UX). The Definition and "What Channel Behaviors are not" subsections are unchanged.

### DOC-070
`Current-State.md` amended **in place** (not append-only) to the new reality:
(1) the Phase 2 sub-item status list — Channel Behaviors moved from
"framework only, soft-blocked" into Populated, and the count changed 5-of-7 →
6-of-7; (2) the Snapshot-026 audit paragraph's trailing count note scoped to its
session (then 5-of-7; now 6-of-7); (3) Next Focus item 2 — Channel Behaviors
recorded as written, with the Permission Matrix named the one remaining (blocked)
sub-item.

---

## Decisions
No new decision. This executes the already-committed DEC-025 (Active) and the
existing Phase 2 framework; it is referenced here, not re-decided.

---

## Findings

### FIND-029
The DEC-025 Channel Model acceptance test held under its first real load. Writing
the Phase 2 Channel Behaviors for the one taxonomy channel type needed only the
Channel Model's taxonomy and its three experience attributes
(format/media constraints · preview affordance · notification capability) — the
three Phase 2 dimensions key 1:1 to the three attributes — with no further Phase 4
content required. This validates the OQ-C unblock-altitude decision (write the
Channel Model only to the altitude that unblocks Phase 2) and the broader pattern
of recording a verbatim cross-phase acceptance test as the contract between a
producing phase and a consuming phase. Citable precedent for future unblock-
altitude scoping.

---

## Open Questions
No open question is resolved or newly opened. Carried, referenced not resolved:
- Inherited Phase 1 questions: `domains.md:1915-1916`, `:1917`, `:1918-1919`, and
  Q-014 (Permission Matrix ↔ Governance — the one remaining Phase 2 blocker).
- Registered Phase 4 open flags (carried from Snapshot-030): agent/subagent
  identity (likely Phase 7); safety-controls vocabulary; the optional
  philosophy-#7 annotation; the repo-wide inherited-question citation drift
  (FIND-028).
- Q-001 / Q-004 (Client Brain) — open, untouched. Q-015 (KNI-21) — open.

---

## Assumptions
- Assumption: the Channel Behaviors write is faithful Phase 2 content (rendering /
  preview / notification UX on the human-experience side); it authors no channel
  integration (Phase 4), workflow/events (Phase 6), capability (Phase 3),
  permission rule (Phase 1 Governance), or identity (Phase 1).
- Assumption: the one-channel-type population is complete for the current taxonomy
  and grows with it; this is the correct evidence-grounded floor, not a gap.
- Assumption: no Phase 1 truth, ownership, or boundary is changed; no inherited
  question resolved.

---

## Risks

### R-028 (carried forward, active — held)
Reference-altitude overcommitment. Held: the write references Phase 4 attributes
and Phase 6 events at altitude and defines neither; no platform is hardcoded
(illustrative only); no owner/placement asserted for a draft concept.

### R-027 (carried forward, active — held)
No inherited Phase 1 question was resolved or narrowed. Q-014 stays the one open
Phase 2 blocker; the inherited domains.md questions stay referenced.

### R-023 (carried forward, active)
Phase 2 ↔ Phase 4 ↔ Phase 6 altitude drift. Held here: notification *events* kept
on the Phase 6 side (referenced, not defined); channel integration kept on the
Phase 4 side. Keep active.

### R-026 (carried forward, active)
`workflows/sync-protocol.md` references Linear MCP tools by logical name; update
the Tooling section if names change.

### R-025 (carried forward, active)
Close-out applied by discipline under the standing reduced-check-in mode: the
write had one content read before landing; this record close-out follows an
independent verifier pass; the Current-State in-place amendments were shown as
exact hunks for review.

---

## Next Focus
1. **Phase 2 is 6-of-7 populated.** The one remaining sub-item is the Permission
   Matrix, blocked on concrete Phase 1 Governance rules (Q-014 / KNI-16); it stays
   KNI-14's open item. No other unblocked Phase 2 content remains.
2. **KNI-18 → Done** (gated structural Linear change, covered by the current
   authorization): applied after this close-out push is verified on origin/main.
3. The four Phase 4 deferred sub-items (Versioning & Compatibility, External
   Integrations, Feature Modules, Future Domains) remain flagged stubs; each a
   fresh gated topic if/when un-deferred.
4. Carry the registered open flags and inherited Phase 1 questions forward,
   unresolved.
5. Methodological note (FIND-029): the verbatim cross-phase acceptance-test
   pattern is a reusable tool for future producer→consumer phase boundaries.
