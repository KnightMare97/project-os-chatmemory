# Phase 3 Capability Map: Brainstorm / Discovery Notes
Date: 2026-06-07 · Goal: Define Phase 3 scope, the canonical meaning of a Capability, and its boundaries with Phase 1 (Domain truth), Phase 2 (Experience/surfaces), and Phase 6 (Workflow sequence) — before any content is written to `capabilities.md`. Scoping only.

## Status
Interview in progress. Repository is source of truth; this is a Phase 11
operating-method capture feeding Phase 3 content decisions. Nothing here is
canon until promoted via an explicit decision + snapshot. Per CLAUDE.md, this
session must not silently finalize boundaries — decisions are flagged for
explicit human confirmation. Same discipline as Phase 2 scoping
(Snapshot-013 / DEC-019).

## Grounding already read (no need to re-ask)
- Canon phase map (`Faraz-OS-Canon.md`): Phase 3 = Capability Map =>
  `capabilities.md`, sub-items: Research, Strategy, Content Creation, Video
  Creation, Publishing, Analytics, Reporting, Lead Scoring.
- Capability definition (`domains.md:177-180`): "A Capability is a reusable
  business function that may serve multiple workflows, domains, or channels.
  A Capability is not a Domain." Canon examples listed there: Research,
  Strategy, Content Creation, Publishing, Analytics, Reporting, Lead Scoring.
- Classification rules (`domains.md:239-265`): "If the concept is a reusable
  function across Domains, classify it as a Capability"; Workflow = "an
  execution path"; Domain = "owns a major business responsibility".
- Workflow definition (`domains.md:195-200`): "A Workflow is an executable
  path of work across one or more Domains and Capabilities... not a Domain."
- Phase 2 Governing Boundary Test (`experience-architecture.md:88-105`):
  Presentation/surface/navigation → Phase 2; Reusable functional ability
  (UI-independent) → Phase 3; Ordered cross-step flow + approval gates →
  Phase 6.
- Phase 2 KPI altitude split (`experience-architecture.md:564-571`): KPI
  computation = Phase 3; the dashboard surface that displays it = Phase 2;
  rule is presents / computes / owns (Phase 2 / Phase 3 / Phase 1).
- `domains.md` is accepted Phase 1 truth and must NOT be re-normalized.
- No `capabilities.md` file exists yet — only the canon map defines Phase 3.

## Summary / key decisions
(running synthesis — items become CONFIRMED only when the user confirms in
the interview; pending promotion to canon via explicit decision + snapshot)

**Capability definition (Q1, CONFIRMED).** A Capability is a reusable,
UI-independent functional ability — a unit of "what the system can *do*" —
invokable by multiple workflows, serving multiple domains, runnable across
multiple channels, that owns no domain truth, prescribes no ordered sequence,
and is tied to no surface. It is the *ability*, not the *owner* (Domain), the
*sequence* (Workflow), or the *presentation* (Surface). Faithful to the
`domains.md:177-180` anchor. Right altitude.

**Execution mode is NOT part of the definition (Q1, CONFIRMED).** Do NOT
narrow Capability to AI/agent-executable. That would contradict Core
Principle #1 "AI-first, but not AI-only" (`principles.md:3`) and the
human/hybrid production reality. Instead, **execution mode (AI / human /
hybrid) is a per-capability ATTRIBUTE** to capture during enumeration, not a
gate on what counts as a capability.

**CLOSED BOUNDARY SET (six) — the single checklist for the entry-writing
pass** (supersedes the earlier "five boundaries" framing from Q1, which
double-counted Phase 1):
1. **Capability definition** (Q1): reusable, UI-independent ability; invokable
   by workflows; serves domains, owns no truth; not a sequence, not a surface.
2. **↔ Phase 2 presentation** (Q2): UI-independent ability vs where a human
   sees/does it; KPI computation = P3, display = P2 (presents/computes/owns).
   Verb-test.
3. **↔ Phase 6 sequence** (Q3): reusable order-free, gate-free ability vs
   ordered gated sequence; workflow-agnostic. Sequence-test. (Watch Publishing,
   Reporting, Research, Strategy, Content Creation.)
4. **↔ Phase 1 domain truth** (Q4): serve domains, never own entity/meaning/
   store-of-record; inherits the unresolved P1↔P3 line, does not resolve it.
5. **↔ Phase 4 provider/plugin** (Q1, Video Creation flag): capability = the
   ability; Provider = swappable execution option (AI model, media tool,
   external integration); Plugin = extension mechanism (`domains.md:212-235`).
   Per Extensibility Philosophy #5 "Domains, capabilities, and plugins must
   remain distinct" (`extensibility-philosophy.md:17`). Ability = Phase 3;
   the swappable tool that executes it = Phase 4.
6. **↔ Phase 5 memory/knowledge** (Q6): capability produces an output;
   persistence as durable knowledge (Client Brain, Knowledge Base, Learnings)
   = Phase 5; ownership = Phase 1. Names that an output *may become* durable
   knowledge; never defines storage/retention/memory structure.

## Q&A log

### Q1 — What a Capability IS (governing definition) + execution mode + 5th boundary
- Asked: Accept the proposed Capability definition (reusable, UI-independent
  ability; invokable by workflows; serves domains, owns no truth; not a
  sequence, not a surface)? Right altitude, or narrow to AI/agent-executable?
- Captured (CONFIRMED):
  - Definition ACCEPTED as proposed. Faithful to `domains.md:177-180`.
  - Do NOT narrow to AI/agent-executable — contradicts "AI-first, but not
    AI-only" (`principles.md:3`) and human/hybrid production paths. Execution
    mode (AI / human / hybrid) = per-capability ATTRIBUTE, captured at
    enumeration, NOT part of the definition.
  - ADD a FIFTH boundary: Capability ↔ Provider/Plugin (Phase 3 ↔ Phase 4),
    per Extensibility Philosophy #5 (`extensibility-philosophy.md:17`) and
    the Plugin/Provider definitions (`domains.md:212-235`).
  - Flag **Video Creation** as an Open Question NOW (before enumeration) — it
    is the sub-item most likely to blur capability vs provider/tool
    integration.
- Citation correction: the user cited FIND-022 for the human/hybrid /
  "AI-first not AI-only" point. FIND-022 (`findings.md:331`) is actually
  about Governance owning permission rules ("not a UI permission table"), a
  different topic. The intended substance is correctly grounded in
  Core Principle #1 (`principles.md:3`); recorded with that anchor instead.
  Do NOT carry a FIND-022 citation for this point into canon.
- Flags: Video Creation classification (capability vs provider/tool) → resolve
  in this session before enumeration.

### Q2 — Phase 3 ↔ Phase 2 boundary (UI-independence + KPI altitude split)
- Asked: Accept the P3↔P2 boundary mirroring Phase 2 canon (presents /
  computes / owns)? Keep Analytics and Reporting distinct?
- Captured (CONFIRMED):
  - Boundary ADOPTED as written, **mirroring existing Phase 2 canon, not
    re-deciding it**. Phase 3 owns the UI-independent ability (the verb:
    compute / generate / assemble / score); Phase 2 owns presentation of the
    result (surface / view / navigation).
  - KPI rule: **computation = Phase 3; the dashboard surface that displays it
    = Phase 2** (presents / computes / owns). `capabilities.md` REFERENCES
    the rule at `experience-architecture.md:564-571`; it does NOT restate or
    re-decide it.
  - **Analytics and Reporting stay DISTINCT capabilities:** Analytics =
    compute metrics/aggregations; Reporting = assemble/generate the report
    artifact. Honors the canon map and `domains.md`, which list them
    separately.
- **Verb-test (reusable operational rule, CONFIRMED):**
  > If removing all UI leaves the ability intact, it is Phase 3.
  (Use this as the standing P3↔P2 discriminator.)
- Flags: **Reporting** is the sub-item most at risk of drifting into Phase 6
  during the later entry-writing pass — "assemble and generate a report" can
  quietly become an ordered, gated reporting *sequence* (gather → compose →
  format → deliver). Watch it the same way as Publishing. (For the
  entry-writing pass, not now.)

### Q3 — Phase 3 ↔ Phase 6 boundary (ability vs ordered sequence; watch Publishing)
- Asked: Accept the P3↔P6 boundary + sequence-test? Publishing = atomic
  "push approved content to channel"? Other hidden-sequence sub-items?
- Captured (CONFIRMED):
  - Boundary ADOPTED as written. **Workflow-agnostic formulation (verbatim):**
    a capability does NOT know its predecessor or successor; if it does,
    Phase 6 ordering has leaked in. A Workflow (Phase 6) is the ordered,
    gated sequence *across* capabilities and *invokes* them.
  - **Altitude clarification (CONFIRMED):** "capabilities.md never describes
    what precedes or follows a capability" is a **writing constraint on the
    file**, NOT a claim that capabilities have no real-world sequence. Phase 3
    simply does not RECORD ordering. Keep this distinction crisp.
  - **Publishing scheduling/queueing — Open Question (do NOT default):**
    atomic "push approved content to channel" is clean; a when-parameter
    (scheduled publish) is probably still within the capability; cross-item
    queueing starts to resemble orchestration and needs a deliberate
    decision. Flag for the Publishing entry-writing pass; do not silently
    resolve toward "part of the ability."
  - **Content Creation note (for entry pass):** the "draft → review → revise"
    loop is a WORKFLOW that invokes the capability, not the capability itself.
    The repo already models this as Service Delivery's **Revision Cycle /
    Revision Aggregate / Revision Handling** (`domains.md:3217`, `:3250`,
    `:3287`). Reference at reference altitude; do NOT reinterpret.
- **Sequence-test (reusable operational rule, CONFIRMED):**
  > If defining the thing requires naming a predecessor, successor, or
  > approval gate, it belongs to Phase 6, not Phase 3.
- **Hidden-sequence watch-list (for the entry-writing pass):** Publishing,
  Content Creation, **Research** ("gather → synthesize → produce brief"),
  **Strategy** ("research → analyze → recommend"). General rule (record):
  any sub-item whose NAME implies a *process* rather than a single act is a
  sequence-leak candidate — which is why the **sequence-test matters more than
  the list**.

### Q4 — Phase 3 ↔ Phase 1 boundary (serve domains, never own domain truth)
- Asked: Accept the P3↔P1 boundary? Lead Scoring = compute-and-hand-off with
  authoritative home deferred to Phase 1? Per-capability "Domains served"
  field, or prose only?
- Captured (CONFIRMED):
  - Boundary ADOPTED as written. A Capability **serves** domains: reads
    domain-owned inputs, produces an output (score/brief/analysis/report),
    owns NO domain truth — not the entity, not its authoritative meaning, not
    where the result is stored-of-record. Phase 1 owns *what things are and
    who owns them*; Phase 3 owns *the ability to act on them*.
  - **"Inherits the flag, does not resolve it" (keep prominent):** Phase 3
    owns the computation altitude and must NOT be where the Phase 1 ↔ Phase 3
    source-of-truth-vs-computation line finally gets settled. That stays a
    Phase 1 Governance/Intelligence question, flagged unresolved
    (`experience-architecture.md:637-639` already flags it).
  - **Lead Scoring:** capability computes a score and hands it to the owning
    domain; the score's authoritative home is deferred to Phase 1.
    Specifically reference the EXISTING open Phase 1 question
    (`domains.md:1917-1918`): "Should lead scoring live fully inside
    Intelligence, or partly inside CRM as domain-local logic?" Phase 3 does
    NOT answer it. The capability computes; where the scoring logic
    authoritatively lives stays that open Phase 1 question. Reference
    altitude; do not step on it.
  - **Structural decision (CONFIRMED): adopt an explicit per-capability
    "Domains served" reference field.** Mirrors the Phase 2 precedent (the
    Cross-Domain Views "Domains composed" column and surface "anchors on"
    references). **Bounded strictly:** it NAMES the owning domain(s) only. It
    must NOT describe how the capability reads/writes domain data — that
    data-path/integration altitude is **Phase 7**, and letting it in here is
    drift. Naming altitude only.
  - **"Stored-of-record" caveat:** Phase 3 NAMES that a result's authoritative
    home is a domain concern; it does not specify which domain or how. Naming
    altitude only.

### Q5 — Sub-item list firmness + Video Creation resolution
- Asked: Keep all eight? Video Creation = capability (medium=video) with tool
  integration pushed to Phase 4? Or fold Video into Content Creation (→ seven)?
- Captured (CONFIRMED):
  - **Keep all eight as the firm working set.** Phase map
    (`Faraz-OS-Canon.md:82-90`) is authoritative over the `domains.md`
    examples list — the examples list (`domains.md:184-191`) is illustrative,
    not exhaustive (tier-2 canon wins).
  - **Video Creation stays a genuine capability:** "the reusable ability to
    produce a video asset." Tool/provider integration (Runway/Sora/Pika/etc.)
    is explicitly **Phase 4**, recorded as a deferred provider reference,
    never part of the capability definition. Holds regardless of the fold
    question.
  - **Content Creation vs Video Creation kept separate** — deciding rationale
    (record, not just "the map says so"): text/image and video are different
    production abilities (distinct operator skills, distinct providers,
    distinct deliverable handling), NOT one capability with a medium
    parameter.
  - **Seam discriminator (define now, not at entry time):**
    Content Creation = non-video content assets; Video Creation = video
    assets. So the two entries don't overlap when written.
  - The sibling open question `domains.md:1914-1915` ("What belongs in
    Intelligence vs Analytics / Reporting capability?") is LOGGED for Q6 —
    not acted on yet.
- **Finding candidate (FIND-026):** phase-map-vs-`domains.md`-examples
  asymmetry — Video Creation appears in the Phase 3 map but is absent from the
  `domains.md:184-191` Capability examples list. The entry-writing pass should
  reconcile the `domains.md` examples list (it is the incomplete one; Video
  Creation should appear there). **Examples-touch-up altitude only** — NOT a
  Phase 1 domain-truth change; do not reinterpret Phase 1.

### Q6 — Capability ↔ Intelligence overlap + Phase 3 ↔ Phase 5 (sixth boundary)
- Asked: (a) Intelligence-vs-Analytics/Reporting framing as flag-inheriting,
  non-resolving? (b) Add sixth boundary Capability ↔ Memory/Knowledge with
  naming-altitude discipline?
- Captured (CONFIRMED):
  - **(a) Intelligence overlap.** Adopt the framing: "Intelligence-domain owns
    insight/scoring truth; Analytics/Reporting capabilities own computation/
    assembly." Record explicitly as **Phase 3's working interpretation pending
    the Phase 1 resolution**, inheriting the open flag at `domains.md:1914-1915`
    — NOT as a resolution dressed as a reference. A later reader must NOT think
    Q6 answered that open question; it did not. Also reference `domains.md:1904`
    (noted Intelligence/Reporting overlap) at reference altitude.
  - **(b) Sixth boundary ADDED: Capability ↔ Memory/Knowledge (Phase 3 ↔
    Phase 5).** A capability produces an output; persistence as durable
    knowledge (Client Brain, Knowledge Base, Learnings) = Phase 5; ownership =
    Phase 1. `capabilities.md` **names** that an output *may become* durable
    knowledge but **never defines** storage, retention, or memory structure.
    "Names, does not define" — same naming-altitude discipline as Q4.
  - **This boundary inherits TWO flags (record both, orphan neither):**
    (i) the persistence-mechanics seam → Phase 5; (ii) the open Phase 1
    question `domains.md:1916` "When does an insight become durable
    knowledge?". Phase 3 references both; resolves neither.
  - **Rationale (record):** every capability produces an output (brief,
    recommendation, metric, report, score, asset), so output-persistence is a
    **universal seam**, not Research/Strategy-specific. One named boundary
    settles it once instead of re-litigating per entry.

### Q7 — File shape (`capabilities.md`) + non-goals + granularity (completeness backstop)
- Asked: Accept the six-field skeleton, non-goals, reference-don't-restate
  framing as the scope target? (1) skeleton right / "Consumed by workflows"?
  (2) backstop: MVP-vs-full set; granularity/naming rule?
- Captured (CONFIRMED):
  - Accept (a) six-field per-capability skeleton, (b) non-goals list, (c)
    reference-don't-restate document framing — all as the **scope target for
    the entry-writing session, NOT written now**. Mirrors how Phase 2 scoping
    closed (DEC-019: explicit non-goals + per-item structure).
  - **(1) No "Consumed by workflows" field.** It would pull Phase 6 ordering
    in — a capability naming its consuming workflows knows its successors (the
    Q3 violation). Leave out. The six fields are non-decorative: each maps to
    a closed boundary (Domains served → Q4; Execution mode → Q1; Produces →
    Q6; Provider dependency → Q4/Q5; Boundary notes → inherited flags).
  - **Execution-mode guard (naming-altitude):** record as "which mode this
    capability CAN run in" (AI/human/hybrid attribute, per Principle #1),
    NOT "the policy for when a human must intervene." The intervention/
    checkpoint policy is **Phase 1 Governance** (risk-tiered checkpoint
    rules). Name the attribute, do not author the rule.
  - **(2a) Scope all eight — no MVP subset.** This is scoping; the deliverable
    is the scope target, not the entries. Build-order is **Phase 10 Build
    Roadmap**, not Phase 3 — do not pre-empt. Any build-priority signal is a
    Phase 10 input, not a Phase 3 decision.
  - **(2b) Add a granularity rule + light naming convention to the scope
    decision** (the one genuine Q7 gap; Phase 2 needed both and they settled
    disputes fast). The Content↔Video seam (Q5) is a granularity question in
    disguise and will recur. Anchor on calls already made.

## Granularity rule + naming convention (proposed, anchored on session calls)
- **Granularity rule (proposed):** one capability per **distinct reusable
  ability (verb)** — NOT per output variant and NOT per domain served. This is
  exactly what already justified keeping Video Creation separate from Content
  Creation (Q5: distinct production ability, not a medium parameter) and
  keeping Analytics distinct from Reporting (Q2: compute vs assemble — two
  verbs). State it now so the eighth entry does not re-open the first entry's
  altitude debate.
- **Naming convention (proposed, light):** capability named by its ability as
  a noun-phrase verb-of-record (Research, Strategy, Content Creation, Video
  Creation, Publishing, Analytics, Reporting, Lead Scoring) — i.e. the canon
  sub-item names already satisfy it; the convention just fixes that new
  capabilities are named for the ability, not the output, tool, or domain.
- NOTE: Claude Code proposes these as part of the scope decision (DEC-024);
  they are not invented later at entry-writing time.

## Per-capability entry skeleton (six fields — scope target, not written now)
1. **Definition** — the reusable ability, one sentence (the verb).
2. **Domains served** — owning domain(s) NAMED only (Q4; no data-path → P7).
3. **Execution mode** — AI / human / hybrid attribute (Q1; "can run in", not
   intervention policy → P1 Governance).
4. **Produces** — the output artifact (brief, score, metric, report, asset…);
   may NAME it can become durable knowledge (Q6); no storage detail → P5.
5. **Provider dependency** — NAMED, deferred to Phase 4 where relevant (Q1/Q5).
6. **Boundary notes / inherited flags** — per-entry watch-items (sequence-test
   flags; inherited Phase 1 open questions).

## Reusable operational rules (canonical set — for the entry-writing pass)
- **Verb-test (P3↔P2):** if removing all UI leaves the ability intact, it is
  Phase 3. Phase 3 owns the verb (compute/generate/assemble/score); Phase 2
  owns viewing the result.
- **Sequence-test (P3↔P6):** if defining the thing requires naming a
  predecessor, successor, or approval gate, it belongs to Phase 6.
- **Workflow-agnostic (P3↔P6):** a capability does not know its predecessor or
  successor; if it does, Phase 6 ordering has leaked in. `capabilities.md`
  does not record ordering — a writing constraint on the file, NOT a claim
  that no real-world sequence exists.
- **Naming-altitude (P3↔P1 / P3↔P7 / P3↔P5):** per-capability fields NAME the
  owning domain / store-of-record / durable-knowledge possibility only; they
  never author the rule, describe data-path/integration (Phase 7), or define
  storage/retention/memory structure (Phase 5). Covers the serve-don't-own
  (boundary 4) and output-persistence (boundary 6) statements.
- **Granularity (P3 internal):** one capability per distinct reusable ability
  (verb), not per output variant or per domain served.

## Non-goals (explicit, CONFIRMED) — `capabilities.md` will NOT contain
- UI / surfaces / views / navigation → Phase 2
- ordered sequences or approval gates → Phase 6
- domain-entity definitions, ownership, or authoritative meaning → Phase 1
- provider/tool implementations or channel integration → Phase 4
- data-paths / read-write mechanics / system wiring → Phase 7
- storage / retention / memory structure → Phase 5
- permission / authorization / human-intervention-checkpoint rules
  → Phase 1 Governance
- build order / MVP-vs-later sequencing → Phase 10 Build Roadmap
- resolution of ANY inherited Phase 1 open question (it references, never
  resolves: `domains.md:1914-1915`, `:1916`, `:1917-1918`)

## Document-level framing (scope target)
`capabilities.md` opens by REFERENCING (not restating) the Governing Boundary
Test (`experience-architecture.md:88-105`) and the closed six-boundary
checklist, then carries the eight capability entries (six-field skeleton each).
The `domains.md` examples-list reconciliation (FIND-026) is an examples-touch-up
tracked for the entry-writing pass, not done this session.

## Build-priority note (Phase 10 input, NOT a Phase 3 decision)
All eight capabilities are in scope to be written. Any build-order/MVP signal
is recorded as a Phase 10 Build Roadmap input; Phase 3 does not pre-empt it.

## Open flags (pending input)
- **Video Creation** — [RESOLVED Q5] genuine capability ("produce a video
  asset"); tool/provider integration deferred to Phase 4. No longer open.
- **Reporting ↔ Phase 6 drift risk** — "assemble/generate a report" must not
  become an ordered gated sequence (gather → compose → format → deliver).
  Watch like Publishing. → carry into the entry-writing pass (not this
  session).
- **Publishing scheduling/queueing** — Open Question for the Publishing
  entry-writing pass: atomic push = clean; scheduled (when-parameter) = likely
  still in-capability; cross-item queueing = possible orchestration, needs a
  deliberate decision. Flag, do not default.
- **Hidden-sequence watch-list** (entry-writing pass): Publishing, Content
  Creation, Research, Strategy. Apply the sequence-test per entry.
- **Lead Scoring authoritative home** — deferred to the existing open Phase 1
  question (`domains.md:1917-1918`, Intelligence vs CRM domain-local). Phase 3
  computes only; does not answer. Reference altitude.
- **Intelligence ↔ Analytics/Reporting line** — inherits open Phase 1 question
  `domains.md:1914-1915` (+ noted overlap `domains.md:1904`). Phase 3 working
  interpretation only; does NOT resolve. Reference altitude.
- **Insight → durable-knowledge threshold** — inherits open Phase 1 question
  `domains.md:1916` ("When does an insight become durable knowledge?") + the
  Phase 5 persistence-mechanics seam. Phase 3 references both; resolves
  neither.
