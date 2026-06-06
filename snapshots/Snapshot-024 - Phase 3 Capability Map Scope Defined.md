# Snapshot-024 - Phase 3 Capability Map Scope Defined

## Current Phase
Phase 11 Claude Code Operating System — operational
Phase 3 Capability Map — newly active; scope defined, no content written
Phase 2 Experience Architecture — active, 5-of-7 populated (unchanged)

## Current Topic
Scoping session (grill-me) for Phase 3 Capability Map. Establishing the
canonical meaning of a Capability and its boundaries with Phase 1 (domain
truth), Phase 2 (presentation), Phase 4 (provider/plugin), Phase 5
(memory/knowledge), and Phase 6 (sequence) before any content is written to
`capabilities.md`. Same discipline as Phase 2 scoping (Snapshot-013 / DEC-019).

## Status
A structured scoping interview (Q1-Q7) was completed and human-confirmed. The
Capability definition, a closed six-boundary set, five reusable operational
rules (verb-test, sequence-test, workflow-agnostic, naming-altitude,
granularity), the per-capability six-field skeleton, the granularity rule and
naming convention, the explicit non-goals, and all inherited flags are
captured. The eight canon sub-items are firm; Video Creation is resolved as a
genuine capability. No architecture content file was written: `capabilities.md`
is deferred to a separate plan -> build -> review session. This snapshot
records scope; it does not write canon content or finalize any Phase 1
boundary. Repository is in a stable, confirmed state.

---

## Document Updates

### DOC-052
`brainstorms/2026-06-07-phase-3-capability-map.md` created. Full Phase 3
scoping capture: capability definition, closed six-boundary set, five
operational rules, six-field skeleton, granularity rule + naming convention,
non-goals, and carried flags. It is a working capture, not canon.

### DOC-053
`capabilities.md` has NOT been created or modified. Writing Phase 3 canon
content from the approved scope is deferred to a separate session
(plan -> build -> review).

---

## Decisions

### DEC-024
The Phase 3 Capability Map scope is defined and human-confirmed (scoping only):

- **Capability definition:** a reusable, UI-independent functional ability —
  a unit of "what the system can *do*" — invokable by multiple workflows,
  serving multiple domains, runnable across channels; owns no domain truth,
  prescribes no ordered sequence, tied to no surface. Faithful to
  `domains.md:177-180`. Execution mode (AI / human / hybrid) is a
  per-capability **attribute**, not part of the definition (Core Principle #1
  "AI-first, but not AI-only", `principles.md:3`) — never narrowed to AI-only.
- **Closed six-boundary set** (the entry-writing checklist):
  1. Capability definition.
  2. ↔ Phase 2 presentation: KPI computation = Phase 3, display = Phase 2;
     `capabilities.md` references `experience-architecture.md:564-571`, does
     not restate it.
  3. ↔ Phase 6 sequence: order-free, gate-free, workflow-agnostic.
  4. ↔ Phase 1 domain truth: serve, never own; inherits the unresolved
     P1 ↔ P3 source-of-truth-vs-computation line, does not resolve it.
  5. ↔ Phase 4 provider/plugin: per Extensibility Philosophy #5
     (`extensibility-philosophy.md:17`) and `domains.md:212-235`.
  6. ↔ Phase 5 memory/knowledge: names that an output *may become* durable
     knowledge; never defines storage / retention / memory structure.
- **Five reusable operational rules:** verb-test (if removing all UI leaves
  the ability intact, it is Phase 3); sequence-test (if defining it needs a
  predecessor/successor/gate, it is Phase 6); workflow-agnostic (a capability
  does not know its predecessor/successor; `capabilities.md` does not record
  ordering — a writing constraint, not a claim that no real-world sequence
  exists); naming-altitude (per-capability fields name the owning domain /
  store-of-record / durable-knowledge possibility only; never author the rule,
  describe data-paths (Phase 7), or define memory structure (Phase 5));
  granularity (one capability per distinct reusable ability).
- **Granularity rule:** one capability per distinct reusable ability (verb),
  not per output variant or per domain served (justifies Video Creation ≠
  Content Creation and Analytics ≠ Reporting). **Naming convention (light):**
  a capability is named for the ability, not the output, tool, or domain.
- **Sub-item set:** all **eight** are firm (Research, Strategy, Content
  Creation, Video Creation, Publishing, Analytics, Reporting, Lead Scoring);
  the phase map is authoritative over the illustrative `domains.md:184-191`
  examples list. **Video Creation** is resolved as a genuine capability
  ("produce a video asset"); its tool integration is Phase 4. No MVP subset —
  build-order is Phase 10 Build Roadmap.
- **Per-capability skeleton (six fields):** Definition; Domains served (name
  only); Execution mode (which mode it *can run in*, not the
  human-intervention/checkpoint policy, which is Phase 1 Governance);
  Produces; Provider dependency (deferred to Phase 4); Boundary notes /
  inherited flags. **No "Consumed by workflows" field** (it would import
  Phase 6 ordering — a capability that names its consuming workflows knows its
  successors).
- **Non-goals — `capabilities.md` will NOT contain:** UI / surfaces / views
  (Phase 2); ordered sequences or approval gates (Phase 6); domain-entity
  definitions, ownership, or authoritative meaning (Phase 1); provider/tool
  implementations or channel integration (Phase 4); data-paths / read-write
  mechanics / wiring (Phase 7); storage / retention / memory structure
  (Phase 5); permission / authorization / human-intervention-checkpoint rules
  (Phase 1 Governance); build order / MVP sequencing (Phase 10); and the
  resolution of ANY inherited Phase 1 open question.

This decision records scope only. It finalizes no Phase 1 boundary and writes
no Phase 2 or Phase 3 canon content.

---

## Findings

### FIND-026
Video Creation appears in the Phase 3 map (`Faraz-OS-Canon.md:82-90`) but is
absent from the `domains.md:184-191` Capability examples list. That examples
list is illustrative, not exhaustive (the phase map is authoritative); the
entry-writing pass should add Video Creation to it. Examples-touch-up altitude
only — this is NOT a Phase 1 domain-truth change and must not reinterpret
Phase 1.

---

## Open Questions

### Q-015 (new, deferred to the Phase 3 entry-writing pass)
Publishing scheduling/queueing altitude (Phase 3 ↔ Phase 6): atomic "push
approved content to a channel" is clearly the capability; a scheduled-publish
*when-parameter* is probably still within the capability; but cross-item
**queueing** may be orchestration (Phase 6). Resolve deliberately during the
Publishing entry-writing pass — flag, do not default. To be tracked in Linear
(`boundary` + `Phase 3`), related to the write-`capabilities.md` issue.

Inherited Phase 1 questions (pre-existing; they stay in `domains.md` as system
of record; Phase 3 references but does not resolve them):
- `domains.md:1914-1915` — what belongs in Intelligence vs the Analytics /
  Reporting capability (noted overlap at `domains.md:1904`).
- `domains.md:1916` — when does an insight become durable knowledge.
- `domains.md:1917-1918` — should lead scoring live fully inside Intelligence
  or partly inside CRM as domain-local logic.

Other open questions unchanged: Q-011 resolved; Q-012 deferred (KNI-11);
Q-013 deferred (repo-only); Q-014 deferred (KNI-16).

---

## Assumptions
- Assumption: the scope captured in DEC-024 reflects human-confirmed decisions
  made this session; the `capabilities.md` write is pending and will be done
  under plan -> build -> review in a separate session.
- Assumption: no Phase 1 domain truth, ownership, or boundary was changed this
  session. Phase 3 references Phase 1; it does not reinterpret it.
- Assumption: no Phase 2 content was changed; Phase 2 remains 5-of-7
  populated.
- Assumption: the eight-capability set is firm for the entry-writing pass;
  Video Creation is a capability and its tooling is deferred to Phase 4.

---

## Risks

### R-027 (new, informational, repo-only)
The entry-writing pass may silently resolve an inherited Phase 1 open question
(lead scoring home, Intelligence ↔ Analytics/Reporting line, insight ->
durable-knowledge threshold) while writing entries. This is a distinct failure
mode from altitude drift. Mitigation: the non-goals explicitly forbid it; the
inherited flags are recorded in the brainstorm and this snapshot; and
"references, never resolves" is a stated rule. Keep active through the
entry-writing pass.

### R-023 (carried forward, active)
Phase 2 / Phase 3 / Phase 6 altitude drift; now also covers the Phase 3
entry-writing pass. The closed six-boundary set and the five operational rules
are the mitigation. Keep active until `capabilities.md` is written in a way
that respects these boundaries.

### R-025 (carried forward, active)
Session close-out is applied by discipline; the propose-then-review gate was
followed this session.

### R-026 (carried forward, active)
`workflows/sync-protocol.md` references Linear MCP tools by logical name;
update its Tooling section if those names change.

---

## Next Focus
1. Write `Faraz-OS-Canon/capabilities.md` from the approved scope (DEC-024 /
   the brainstorm capture), under plan -> build -> review, in a separate
   session: eight entries on the six-field skeleton, opening by referencing
   (not restating) the Governing Boundary Test (`experience-architecture.md:88-105`)
   and the closed six-boundary checklist.
2. During that write, honor every carried flag: Publishing scheduling/queueing
   (Q-015); Reporting sequence-risk; the hidden-sequence watch-list
   (Publishing, Content Creation, Research, Strategy — apply the sequence-test
   per entry); the three inherited Phase 1 questions (reference, never
   resolve); reconcile the `domains.md` examples list (FIND-026,
   examples-touch-up only).
3. Phase 2 remains 5-of-7 populated: Channel Behaviors soft-blocked on the
   Phase 4 Channel Model (KNI-18), Permission Matrix blocked on concrete
   Phase 1 Governance rules (Q-014 / KNI-16); the three Operating-Surface
   flags (Client Profile, System Configuration / Settings, Onboarding) stay
   parked; the Future Personas placeholder and the deferred navigation
   sub-detail (landing surface, notification routing, deep-linking) carry
   forward as marked future items.
4. After repo approval, reconcile Linear (sync-protocol Step 4): create the
   Phase 3 milestone + `Phase 3` label; Phase 3 scoping issue -> Done citing
   this snapshot; write-`capabilities.md` issue -> Todo; Q-015 -> a `boundary`
   issue. Re-read the board first to confirm the next free issue numbers.
