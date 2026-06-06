# Capability Map — Phase 3

## Purpose
This file defines the capability layer of Faraz OS:
the reusable, UI-independent functional abilities
the system can perform.

It records each capability on a fixed entry skeleton.

It does not design surfaces or views (Phase 2),
sequence work or define approval gates (Phase 6),
own or compute domain truth (Phase 1),
or integrate providers and channels (Phase 4).

---

## Status
Phase 3 scope is defined and human-confirmed
(see Snapshot-024 and DEC-024).

This file is written in batches.
Batch A is written: Publishing, Reporting, Content Creation,
Research, Strategy.
Batch B is pending: Video Creation, Analytics, Lead Scoring.

(When Batch B lands, this Status line must be updated
to record the full eight as written and to remove the
"Batch B pending" note.)

No Phase 1 domain truth, ownership, or boundary is changed
by this file. Phase 3 references Phase 1;
it does not reinterpret it.

---

## Governing boundaries (referenced, not restated here)
Capabilities are governed by the Governing Boundary Test
in `experience-architecture.md` (§Governing Boundary Test)
and the closed six-boundary set recorded in
DEC-024 / Snapshot-024.

This file does not restate those boundaries — it applies them.

Altitude rule, by reference:
presents / computes / owns = Phase 2 / Phase 3 / Phase 1.

---

## How to read an entry
Each capability is recorded on six fields:

- **Definition** — the reusable ability, in one sentence (the verb).
- **Serves** — which domain(s) this capability serves.
  This is a **Phase 3 inference, pending confirmation**, not
  asserted domain truth: `domains.md` does not enumerate a
  capability→domain mapping. The field reads at naming altitude
  ("this capability serves [domain]") and never asserts that a
  domain owns the capability (ownership is a Phase 1 concern).
- **Execution mode** — which mode this capability *can run in*
  (AI / human / hybrid). This is an attribute, not the
  human-intervention or checkpoint policy, which belongs to
  Phase 1 Governance.
- **Produces** — the output the ability yields. Where an output
  *may become* durable knowledge, that is named only; its
  storage, retention, and memory structure belong to Phase 5.
- **Provider dependency** — any swappable execution tool the
  ability leans on, named only and deferred to Phase 4.
- **Boundary notes** — the per-entry watch-items: sequence-test
  flags, granularity seams, and any inherited Phase 1 questions
  the entry references but does not resolve.

---

## Capabilities

### Publishing
- **Definition.** The ability to push a piece of approved content
  to a channel.
- **Serves.** Serves Service Delivery (Phase 3 inference, pending).
  The channel itself — the integration that receives the content —
  is Phase 4, not part of this capability.
- **Execution mode.** AI / human / hybrid — the push can run
  autonomously, be performed by a human, or be a hybrid.
- **Produces.** A dispatched content item on a channel.
- **Provider dependency.** Channel / platform integrations
  (named only; deferred to Phase 4).
- **Boundary notes.**
  - Sequence (Phase 6): Publishing is a single, order-free, gate-free
    ability. It does not encode what precedes or follows it — the
    `Approval → Publishing → Reporting` path is a Phase 6 workflow
    that *invokes* this capability, not part of it.
  - Open question Q-015 (P3 ↔ P6), flagged not resolved: the altitude
    of scheduling/queueing. An atomic push is clearly in-capability;
    a scheduled-publish *when-parameter* is probably still
    in-capability; cross-item **queueing** may be orchestration
    (Phase 6) and needs a deliberate decision. See `open-questions.md`
    (Q-015) / KNI-21. This entry flags it and does not default it.

### Reporting
- **Definition.** The ability to assemble and generate a report
  artifact from domain-held data.
- **Serves.** Serves Intelligence and Client Success (Phase 3
  inference, pending — and the served-domain set most exposed to an
  unresolved Phase 1 question; see Boundary notes).
- **Execution mode.** AI / human / hybrid.
- **Produces.** A report artifact (a composed deliverable). The
  artifact *may become* durable knowledge (Phase 5); named only.
- **Provider dependency.** Export / formatting tools, if any
  (named only; deferred to Phase 4).
- **Boundary notes.**
  - Granularity (DEC-024): Reporting is distinct from Analytics.
    Analytics computes metrics/aggregations; Reporting assembles and
    generates the report artifact. Two abilities, two verbs.
  - Sequence (Phase 6): the assemble/generate ability only. A
    "gather → compose → format → deliver" pipeline is a workflow
    (Phase 6), not this capability; the entry records no ordering.
  - Inherited Phase 1 question, referenced not resolved: what belongs
    in the Intelligence domain versus the Analytics / Reporting
    capability is open (`domains.md:1914-1915`; noted overlap at
    `domains.md:1904`), and CRM models its own *CRM Reporting &
    Dashboarding* bounded context (`domains.md:802`). The Serves value
    above is therefore a Phase 3 inference subject to that open
    question; this entry does not settle it.

### Content Creation
- **Definition.** The ability to produce a non-video content asset.
- **Serves.** Serves Service Delivery (Phase 3 inference, pending).
- **Execution mode.** AI / human / hybrid.
- **Produces.** A non-video content asset.
- **Provider dependency.** Content-generation tools (named only;
  deferred to Phase 4).
- **Boundary notes.**
  - Granularity seam (DEC-024): Content Creation covers non-video
    content assets; video assets are the separate Video Creation
    capability. The two do not overlap — distinct production
    abilities, not one capability with a medium parameter.
  - Sequence (Phase 6): the produce-asset ability only. The
    "draft → review → revise" loop is Service Delivery's Revision
    Cycle / Revision Aggregate / Revision Handling
    (`domains.md:3217`, `:3250`, `:3287`) — a workflow that invokes
    this capability. Referenced at reference altitude; not
    reinterpreted.

### Research
- **Definition.** The ability to gather and synthesize information
  into a research output.
- **Serves.** Serves Knowledge and Intelligence (Phase 3 inference,
  pending).
- **Execution mode.** AI / human / hybrid.
- **Produces.** A research output (e.g. a brief or findings). The
  output *may become* durable knowledge (Phase 5); named only.
- **Provider dependency.** Search / data sources (named only;
  deferred to Phase 4).
- **Boundary notes.**
  - Sequence (Phase 6): "gather → synthesize → produce" reads as a
    process, but the capability is the order-free research ability;
    the entry records no ordering and names no predecessor or
    successor.

### Strategy
- **Definition.** The ability to analyze inputs and produce a
  strategic recommendation.
- **Serves.** Serves Service Delivery, Knowledge, and Intelligence
  (Phase 3 inference, pending).
- **Execution mode.** AI / human / hybrid.
- **Produces.** A strategic recommendation artifact. The artifact
  *may become* durable knowledge (Phase 5); named only.
- **Provider dependency.** AI model providers (named only; deferred
  to Phase 4).
- **Boundary notes.**
  - Sequence (Phase 6): the analyze-and-recommend ability is
    standalone. "research → analyze → recommend" names a predecessor
    (the Research capability) — that ordering is Phase 6, not part of
    this capability. The entry does not encode "after Research."

### Video Creation
- **Definition.** The ability to produce a video asset.
- **Serves.** Serves Service Delivery (Phase 3 inference, pending).
- **Execution mode.** AI / human / hybrid.
- **Produces.** A video asset.
- **Provider dependency.** Video-generation tools (e.g. Runway, Sora,
  Pika) (named only; deferred to Phase 4).
- **Boundary notes.**
  - Granularity seam (DEC-024): Video Creation covers video assets;
    non-video content assets are the separate Content Creation
    capability. Distinct production abilities, not one capability with
    a medium parameter — the same seam stated in the Content Creation
    entry, from the video side.
  - Provider line (Phase 4): the Definition names the ability, not the
    tool. The specific video tool/provider is Phase 4, not part of
    this capability — the same shape Publishing uses for the channel.

### Analytics
- **Definition.** The ability to compute metrics and aggregations
  from domain-held data.
- **Serves.** Serves Intelligence (Phase 3 inference, pending — and
  exposed to an unresolved Phase 1 question; see Boundary notes).
- **Execution mode.** AI / human / hybrid.
- **Produces.** Computed metrics and KPI values. (The display of
  these on a dashboard is Phase 2; see Boundary notes.)
- **Provider dependency.** Compute engines, if any (named only;
  deferred to Phase 4).
- **Boundary notes.**
  - Granularity (DEC-024): Analytics is distinct from Reporting.
    Analytics computes metrics/aggregations; Reporting assembles and
    generates the report artifact. Two abilities, two verbs —
    consistent with the Reporting entry.
  - KPI altitude split, referenced not restated: KPI computation is
    Phase 3; the dashboard surface that displays the computed KPI is
    Phase 2 (presents / computes / owns). See
    `experience-architecture.md:564-571`.
  - Inherited Phase 1 question, referenced not resolved: what belongs
    in the Intelligence domain versus the Analytics / Reporting
    capability is open (`domains.md:1914-1915`; noted overlap at
    `domains.md:1904`). The Serves value above is therefore a Phase 3
    inference subject to that open question; this entry does not
    settle it.

### Lead Scoring
- **Definition.** The ability to compute a score for a lead.
- **Serves.** Serves CRM and Intelligence (Phase 3 inference,
  pending — this is exactly the unresolved Phase 1 question at
  `domains.md:1917-1918`; see Boundary notes). Stated at naming
  altitude: this capability serves those domains; it does not own
  the lead or the score.
- **Execution mode.** AI / human / hybrid.
- **Produces.** A lead score. Its authoritative home — where the
  score lives of record — is a Phase 1 concern and is deferred (see
  Boundary notes); this capability computes the score and hands it to
  the owning domain.
- **Provider dependency.** Scoring / AI model providers, if any
  (named only; deferred to Phase 4).
- **Boundary notes.**
  - Phase 1 boundary (the sharp one): this capability computes a
    score only. It does not define what a lead is, what "qualified"
    means, or where the score authoritatively lives — those are
    Phase 1 truth (CRM / Intelligence). The entry names "a lead" only
    as the scored subject, at reference altitude; it defines nothing.
  - Inherited Phase 1 question, referenced not resolved: whether lead
    scoring lives fully inside Intelligence or partly inside CRM as
    domain-local logic is open (`domains.md:1917-1918`; Intelligence's
    Scoring & Prioritization context at `domains.md:1832-1837`). The
    Serves value above is the Phase 3 inference sitting directly on
    that question; this entry does not resolve it.
