# Open Questions

## Purpose
This file tracks the current important unresolved questions
for Faraz OS.

It is not a historical archive of every question ever raised.

It should contain only active,
still-relevant,
cross-file questions that matter to current work.

Historical or already-resolved questions
should be moved into snapshots,
decision records,
or archive material as appropriate.

---

## Usage Rules
- Keep questions current.
- Remove or relocate resolved questions.
- Prefer one canonical entry per unresolved issue.
- Link question wording to the latest relevant canon and snapshots.
- If a question becomes a decision, move it to `decisions.md`.
- If a question is only historical, keep it out of this file.

---

## Current High-Priority Questions

### Q-001
What is the final ownership model for Client Brain?

Current direction:
- Client Brain is currently treated as a Memory Object
  and Shared Service Artifact direction.
- Knowledge appears to be the strongest long-term ownership direction.
- Client Success contributes important relationship memory.
- Final ownership remains draft.

Why it matters:
- This affects memory ownership,
  retrieval design,
  update authority,
  and cross-domain boundaries.

Resolved (DEC-027):
- Client Brain is owned by Knowledge as a Memory Object / Shared Service Artifact.
- Client Success contributes relationship-relevant content but does not own it;
  CRM references it but does not own it.
- Made concrete in `domains.md` (Knowledge "What it owns"; Client Brain section)
  in the same landing.
- Partitioning (per Client / per Brand / both) remains open — that is Q-004, not Q-001.
- Closed.

---

### Q-002
What is the final ownership model for Service Agreement?

Resolved (DEC-034):
- **Service Agreement is owned by CRM as a first-class Entity** — addressable by
  reference, not absorbed into the CRM Client Account entity.
- Classification: **Entity** (identity + revision history + lifecycle); **Aggregate
  placement pending Q-006** (not yet an Aggregate).
- Reference-vs-own: Finance / Service Delivery / Client Success / Engagement Scope
  reference it; none own. Carried fallback: a new Commercial / Agreements domain if the
  commercial spine later strains CRM.
- Narrowings: the `domains.md:690` `CRM / Client Success` ambiguity → CRM-owns /
  Client-Success-references; the Finance open note answered (owned by CRM).
- Scope: ownership + classification only — the dependents (Proposal / Package / SLA /
  Contract / Amendment) and **Q-006** are each their own later gate. The second of the
  ~10 Phase-1 entity reopenings (Q-018 was first).

Why it mattered:
- It affected agreement truth, scope control, service coordination, and future
  aggregate / bounded-context design; the commercial spine (pre-sales → proposal →
  package → agreement → SLA → contract → billing) had no firm owner to hang off.

---

### Q-003
What is the final placement of Brand?

Current direction:
- Brand should not be treated casually
  as just a field inside Client Brain.
- It may require its own Entity treatment
  or more explicit scoped modeling.
- Final placement remains draft.

Why it matters:
- This affects client structure,
  memory design,
  account structure,
  and scope modeling.

---

### Q-004
Should Client Brain exist per Client,
per Brand,
or support both levels?

Current direction:
- This remains explicitly open.
- Current material suggests Brand may need stronger modeling.
- No final structural rule is locked yet.

Why it matters:
- This affects memory partitioning,
  retrieval,
  ownership,
  and scaling of client context.

Note (DEC-027):
- Q-001 (Client Brain ownership) is resolved to Knowledge; Q-004 (partitioning)
  stays open, entangled with Q-003 (Brand placement).
- The Phase-5 Client Brain entry is written partition-agnostic — valid under
  per-Client, per-Brand, or both — so it does not silently resolve Q-004.

---

### Q-005
What is the final ownership boundary between CRM Client Account
and Client Success Relationship?

Current direction:
- CRM should own account baseline and commercial continuity.
- Client Success should own active post-conversion relationship handling.
- The distinction is draft but directionally clear.

Why it matters:
- This affects domain boundaries,
  relationship lifecycle modeling,
  and later aggregate clarity.

---

### Q-006
What is the final lifecycle relationship
between Service Agreement and Engagement Scope?

Current direction:
- Engagement Scope should be derived from,
  constrained by,
  or validated against Service Agreement.
- The exact lifecycle link is still draft.

Why it matters:
- This affects scope governance,
  execution correctness,
  and later service-delivery modeling.

---

### Q-007
Should assigned human operator references
inside Engagement Scope remain simple references,
or evolve into a stronger assignment artifact?

Current direction:
- Workforce remains the source of truth
  for Human Operator identity,
  availability,
  capacity,
  and eligibility.
- Engagement Scope may reference assignment-related information.
- Final structure remains draft.

Why it matters:
- This affects the Workforce / Service Delivery boundary
  and later aggregate design.

---

### Q-008
RESOLVED — see DEC-011.

Normalization of `domains.md` produces a proposed normalized draft
plus a review summary before any canonical file replacement.
Direct update to the canonical file is not the accepted operating model.
This question is closed.

---

### Q-009
Should normalization produce only a cleaned `domains.md`,
or also a short change log summarizing what changed and why?

Current direction:
- This remains open.
- A review-oriented summary may improve trust and traceability.

Why it matters:
- This affects handoff clarity,
  review quality,
  and future maintenance.

Partial direction established:
The review summary component of DEC-011 should serve the change log purpose.
It should cover what was consolidated, what was left unchanged,
and any newly surfaced Open Questions or Risks.
Whether the review summary should also be persisted
as a standalone file after acceptance remains open.

Further partial direction established:
The review summary requirements section of the Execution Checklist v1
now specifies the required format and content of the review summary,
including Changes Made, Items Left Unchanged,
Duplicate Definitions Consolidated,
Draft Boundaries Confirmed Preserved,
Follow-up Discovery Items,
and Residual Ambiguity.
Whether the review summary should persist as a standalone file
after acceptance remains open.
Full resolution of Q-009 is deferred until after
the first normalization pass is complete.

---

### Q-010
RESOLVED — see Execution Checklist v1 appended to
`Faraz-OS-Canon/Normalization Pass v1 Plan for domains.md`.

A dedicated normalization checklist has been produced
and appended to the Normalization Pass v1 Plan.
Claude Code must read and follow it in full
before beginning the normalization pass.
This question is closed.

Priority raised following DEC-011:
Claude Code must operate under explicit constraints
even when producing only a proposed draft.
A normalization checklist reduces the risk of constraint drift
during the pass and should be prepared before Claude Code begins.

---

### Q-011
RESOLVED — see DEC-019 in
`snapshots/Snapshot-013 - Phase 2 Experience Architecture Scope Defined.md`.

The Phase 2 ↔ Phase 3 boundary
and the Permission Matrix question
are resolved.

Direction:
- Operator-facing surfaces are in Phase 2 scope.
- Phase 2 owns where / to whom / how humans interact.
- Phase 2 does not own human identity (Workforce / Phase 1),
  capabilities (Phase 3),
  or authorization rules (Governance / Phase 1).
- The Phase 2 Permission Matrix is a read-only projection
  of Governance rules onto the experience layer
  (rows = personas; columns = surfaces / portals / views;
  not capabilities).
- Phase 2 authors no rules.

This question is closed.

---

### Q-012
What is the intended boundary between
Phase 7 System Architecture Blueprint
and Phase 8 Puzzle Board Architecture?

Resolved (DEC-030) — one boundary drawn (scoping only; no Phase-7/8 content):
- **Phase 7 = the substantive cross-cutting concern-views** (seven lenses,
  `Faraz-OS-Canon.md:132-138`): how the system handles data / execution / AI /
  integration / security / runtime as cross-cutting concerns.
- **Phase 8 = the layered assembly** (seven layers, `Faraz-OS-Canon.md:141-147`,
  incl. Experience + AI `[ADDED]` at `:146-147`): the concrete building blocks
  organized into layers, most owned across other phases — **not** a 1:1 mapping
  of the seven P7 views.
- **One-way dependency:** Phase 8 assembles to satisfy Phase 7; Phase 7 is
  scoped/written first.
- The boundary test and the disambiguation-not-rename convention are recorded
  verbatim in DEC-030, with the AI Architecture (P7) vs AI Layer (P8) worked
  example as the highest-collision seam.

Carried, not resolved by DEC-030 (deferred to the Step-2 Phase 7 question-gate
or their owning passes): Q-013 (AI / agent-surface home), the agent/subagent-
identity Phase-7 flag, the inversion guard, Feature-Modules / module-mounting;
Q-003, Q-004, Q-016, the R-027 set (incl. `domains.md:1918`), and R-028 carried
untouched.

Linear: KNI-11 → Done (DEC-030 raw-verified on origin/main, commit `fdbe0fe`).

Why it mattered:
- This affected how Phase 7
  (System Architecture Blueprint)
  and Phase 8 (Puzzle Board Architecture,
  including the Experience Layer and AI Layer)
  were scoped and what each owns.
- It prevented premature finalization of either phase's
  responsibility before Phase 6 revealed concrete needs.

---

### Q-013
What is the exact home of AI / agent-facing surfaces?

Resolved (DEC-031) — the architecture-home split:
- The **architecture / engine home** of AI & agent-facing capability is
  **Phase 7 AI Architecture**, which also owns **agent / subagent identity**
  (un-deferred into Phase 7 scope by DEC-031).
- **Surface rendering** of agent-facing surfaces stays **Phase 2 Experience**
  (which already owns surfaces). Only a genuinely pure surface-rendering nuance,
  should one surface, is a Phase-2 item; no new Phase-2 work is implied.
- The agent / subagent architecture is defined in the Phase 7 content write
  (AI Architecture view), not in the scope gate.
- Repo-only; not tracked as an active Linear issue (see Snapshot-013).

Why it mattered:
- This affected where agent-driven and AI-driven surfaces
  belonged in canon.
- It prevented Phase 2 from silently absorbing
  AI / agent-facing surfaces.

---

### Q-014
What concrete Phase 1 Governance rules are required
to populate the Phase 2 Permission Matrix,
and when do they become available?

Current direction:
- The Phase 2 Permission Matrix is structurally defined
  (rows = personas; columns = surfaces / portals / views;
  a read-only projection of Governance rules),
  but it cannot be populated until Phase 1 Governance
  authorization and permission rules in `domains.md`
  are concrete.
- This is a cross-phase dependency:
  Permission Matrix population is blocked on Phase 1 Governance.
- Trigger: reopening Phase 1 Governance
  (making its permission / authorization rules concrete)
  is what unblocks Permission Matrix population.
- Deferred; not active work.
- The Permission Matrix population work itself remains
  in `KNI-14` (In Progress, blocked).
- This dependency lives in this file as the system of record;
  tracked in Linear as a separate issue,
  Canceled with a reopen-when-Phase-1-Governance-rules-concrete
  note (deferral pattern, not a separate status).

Why it matters:
- It prevents Phase 2 from authoring permission rules
  (which belong to Phase 1 Governance)
  merely to populate the matrix.
- It makes the Phase 2 -> Phase 1 dependency explicit,
  so the Permission Matrix is populated
  only when Governance truth exists.

Resolved (DEC-026 / Snapshot-033):
- Phase-1 half — the Governance authorization slice is concrete in `domains.md`
  ("Authorization (accepted slice — DEC-026)"); DEC-026.
- Phase-2 half — the Permission Matrix is populated as a read-only projection of
  those rules through the surface↔resource mapping (`experience-architecture.md`;
  Snapshot-033), reproducing the ratified DEC-020 exposure with zero divergence.
  Phase 2 is now 7-of-7; KNI-14 → Done.
- Closed.

---

### Q-015
At what altitude does Publishing scheduling/queueing sit —
within the Publishing capability (Phase 3),
or orchestration (Phase 6)?

Resolved (DEC-028) — split three ways:
- Atomic "push approved content to a channel" = Phase 3
  Publishing capability.
- A scheduled-publish *when-parameter* = **firm Phase 3** (moved
  from "probably in-capability"); it carries no cross-item ordering.
- Cross-item **queueing / sequencing** = **Phase 6 orchestration**:
  it names an ordering across items (a sequence), so the
  selection-vs-sequence test (`decisions.md:823-830`) places it
  in Phase 6.

Venue-change note (recorded in DEC-028):
- Q-015's own text named the `capabilities.md` write as its
  resolution venue; that pass deliberately chose flag-not-resolve —
  the flag note, now refreshed at `Faraz-OS-Canon/capabilities.md:89-93`.
  The venue moved to the
  Phase 6 question-gate because the deciding instrument — the
  ratified selection-vs-sequence test (DEC-025) — now exists.
  A deliberate re-venue, applying the litmus as a recorded decision,
  not a default.

Knock-on (reference altitude, isolated commit):
- The `capabilities.md` Publishing entry flag note (`:89-93`) is
  refreshed to "resolved by DEC-028"; the capability itself stays
  atomic, order-free, unchanged.

Linear: KNI-21 → Done (after the resolving push is raw-verified on
origin/main).

Why it mattered:
- It kept the Phase 3 ↔ Phase 6 boundary clean: a capability is a
  single, order-free, gate-free ability, while ordered cross-item
  sequencing belongs to Phase 6 Workflow Design. Defaulting
  Publishing toward "the queueing is part of the ability" would
  have silently imported workflow orchestration into a capability.

---

### Q-016
Does the Client persona have scoped exposure to the Performance & Analytics View?
View Inventory (:614) says scoped; Client portal table (:370) omits it.
Pre-existing inconsistency between two ratified Phase-2 sources, surfaced by the
matrix view projection (Snapshot-033). Resolution reopens DEC-022 view membership
— its own small decision.

Current direction:
- Flagged in the Permission Matrix view projection as `‡`; not resolved there
  (the matrix authors no decision; R-027/R-028).
- The Client's surface-level Reports & Analytics exposure (Scoped, own-engagement)
  is unaffected and reproduces the ratified surface table; this question is only
  the view-membership nuance.
- Deferred; its resolution is a small DEC reopening DEC-022 view membership.
- Lives in this file as the system of record; tracked in Linear if/when scheduled.

---

### Q-017
Where do the system administrator's **visual viewing and management**
(update / add / remove) of workflows belong across phases?

Current direction:
- **Viewing** is partially covered already: the Phase-2 **Agent & Workflow
  Monitor** surface gives the System Administrator Full exposure
  (`experience-architecture.md:239`).
- The **new part is visual workflow editing / management** — updating, adding,
  and removing workflows through a visual interface. This is not yet authored
  anywhere.
- Candidate homes span multiple phases and likely need more than one:
  - Phase 2 (the surface / experience through which editing happens);
  - Phase 6 (workflow definitions treated as **configurable artifacts** rather
    than fixed canon flows);
  - Phase 4 (config-time binding / extensibility of workflow definitions);
  - Phase 7 (engine support for editable, runnable workflow definitions).
- **Registered, not resolved.** Multi-phase placement is its own gated decision
  later; do not default it. This question lives in this file as the system of
  record; tracked in Linear if/when scheduled.

Why it matters:
- It keeps a real capability (administer workflows visually) from being silently
  assumed or authored in the wrong phase. In particular, the Phase 6
  `workflows.md` first write (Batch B flow entries) must **not** assume or author
  a visual workflow editor / management capability; it carries this as a
  registered flag.
- The viewing-vs-editing split mirrors the Phase-2 vs Phase-6/4/7 altitude
  boundaries already in canon; resolving where editing lives prevents collapsing
  a surface concern, a definition-as-artifact concern, and an engine concern.

---

### Q-018
What domain owns a Client Asset (raw + produced + client-uploaded client media)
as a first-class entity, and does Asset Intelligence (P5) need un-deferring to
support the Phase-7 Data Architecture view?

Resolved (DEC-033):
- A new Phase-1 domain — **Media & Assets** — owns the **Client Asset** entity (one
  entity spanning raw uploads, client-uploaded content, AI-generated media, and
  produced deliverables; it owns the asset + rights / provenance / retention-status).
- **Asset Intelligence (P5) stays deferred** — Q-018 settles only the Phase-1 owner.
- Five-seam boundary recorded: Asset entity = Media & Assets; `relevant_assets_refs`
  (Engagement Scope) unchanged; produced-by = Phase 3; storage / scoping / ingest /
  retention = Phase 7 Data + Phase 1 Governance (referenced); asset intelligence =
  Phase 5, deferred.
- This unblocks the Phase-7 Data Architecture view; it is the **first of the ~10
  Phase-1 entity reopenings** the gap analysis surfaced
  (`grounding/Gap-Analysis-and-Roadmap.md`, non-canon).

Linear: KNI for Q-018 (after the resolving push is raw-verified on origin/main).

Why it mattered:
- Canon carried only asset *references* (`relevant_assets_refs`) and *produced
  outputs* (Content / Video Creation); no domain owned the asset entity, so the
  Phase-7 Data view had nothing to reference and the inversion guard (DEC-031 G-1)
  forbade Phase 7 inventing the owner.
- It was the keystone for asset rights / licensing, the Brand Kit / content library,
  retention, and the client-upload / footage flows.

---

### Q-019
Which domain owns post-publish audience engagement
(comments, direct messages, conversations, and the agency's replies)?

Resolved (DEC-035):
- A new Phase-1 domain — **Community** — owns post-publish audience engagement, with four
  Entities: Comment, Direct Message, Conversation / Thread (aggregate-root candidate), and
  Engagement Reply. Classification = Entity; aggregate boundaries draft.
- Named **Community** deliberately, **not "Engagement"** (which collides with the existing
  Service-Delivery "Engagement Scope" concept).
- **Sentiment Signal ownership is contested and left draft** (a raw tag may sit here; the
  derived analytical finding is Intelligence).
- Boundary set: references Lead → CRM, Escalation → Client Success, sentiment / crisis
  finding → Intelligence, Publishing capability + channel → P3 / P4, published item →
  Publishing / Service Delivery, approval-of-record / IR-sensitivity → Governance. B2C
  audience axis ≠ B2B client axis.
- The **3rd of the ~10 Phase-1 entity reopenings** the non-canon gap analysis surfaced
  (`grounding/Gap-Analysis-and-Roadmap.md`); the biggest coverage gap.

Surfaced by the three-lens gap analysis (no pre-existing open-question number; registered
here and resolved by DEC-035 in the same package). Linear: KNI for Q-019 (after the
resolving push is raw-verified on origin/main).

Why it mattered:
- The canon workflow chain stopped at Publishing → Reporting; no domain owned comments /
  DMs / conversations and no community capability existed — the entire post-publish stage
  (community management, inbound lead capture, sentiment / crisis) was unmodeled.
- Resolving the owner unblocks the Phase-6 post-publish workflow and the Phase-3 / Phase-4
  follow-ons (each its own later gate).

---

## Question Review Rule
Review this file regularly.

If a question is:
- resolved, move it to `decisions.md`
- obsolete, remove it
- historical, move it to snapshots or archive
- still active, keep it here

This file should stay short,
current,
and decision-relevant.
