# Faraz OS — Knowledge & Memory Architecture (Phase 5)

## Purpose
`memory.md` defines the logical architecture of Faraz OS memory and knowledge:
for each memory/knowledge structure — what it is, the Phase-1 domain that owns it,
what it holds (at category level), how it becomes and stays durable, and the
contract under which it is retrieved and updated. It realizes Core Principle #7
(memory-centric architecture, `principles.md:21-22`) and #9 (continuous learning
loops, `principles.md:27-28`) at the structural level.

Scope, altitude, the closed seven-boundary set, and non-goals are fixed by
**DEC-027** (the Phase 5 question-gate). This file references them rather than
restating them, and references Phase-1 domain truth, DEC-026 authorization, and
Phase-7 implementation rather than re-owning them.

## Altitude
Phase 5 architects memory and knowledge as a *logical contract*: structure,
ownership-mapping (by reference), lifecycle, and retrieval/update contract. It does
**not** specify physical storage, indexing, data schema, or AI-retrieval
implementation (Phase 7); it authors no authorization rule (DEC-026) and no domain
ownership (Phase 1).

## Governing ownership
Five of the six firm structures are already owned by the **Knowledge** domain per
Phase 1 (`domains.md:1254-1265`, "Knowledge — What it owns"); **Client Brain**
ownership was resolved to Knowledge by DEC-027 (`domains.md:374`, `:1265`,
`:2791-2795`). Phase 5 gives these Knowledge-owned structures architectural form; it
does not re-own them.

Each entry uses the DEC-027 six-field skeleton: Definition · Owner (Phase-1
reference) · Contents · Lifecycle / durability · Retrieval & update contract ·
Boundary notes.

---

## Client Brain
- **Definition.** Persistent durable memory holding the cross-workflow, cross-service
  context a client requires — strategic, brand, relationship, and learning context,
  reusable by humans and AI (`domains.md:342-343`, `:2770-2776`). Its partitioning
  unit is **per Brand** (DEC-045), with a per-Client aggregation view for cross-brand
  context.
- **Owner (Phase-1).** **Knowledge** (DEC-027; `domains.md:374`, Knowledge "What it
  owns" `:1265`). Client Success **contributes** relationship-relevant content but
  does not own it; CRM **references** it but does not own it (`:376-377`,
  `:2793-2794`). Primary consumers: Strategy, Service Delivery, Intelligence,
  Approval workflows, CRM (partial) (`:379-384`).
- **Contents.** Identity; Brand context; Market context; Commercial & offer context;
  Rules & constraints; Strategic context; Relationship memory; Performance learnings;
  Learnings & decisions; References (the Client Brain field groups,
  `domains.md:399-461`). Holds durable client memory, strategic context, relationship
  memory, durable learnings, approved long-lived context, and reusable client
  knowledge for humans and AI (`:2770-2776`). Does **not** hold the legal/commercial
  account, operational delivery state, approval-queue state, workforce identity, or
  secret values (`:2784-2789`; secrets boundary `:605-615`).
- **Lifecycle / durability.** Versioned: draft → active → approved → superseded
  (`domains.md:630-634`). Approved strategic context is long-lived and must not be
  silently overwritten (`:556-557`, `:594`).
- **Retrieval & update contract.** Update authority is tiered at altitude
  (`domains.md:529-557`): Human-only for identity / positioning / compliance /
  approval-preference / stakeholder changes; AI-propose / human-approve for audience,
  competitor, strategic-learning, pattern, tone, and pillar refinements; workflow
  auto-append for approved learnings, recurring-feedback summaries, decision
  references, and engagement-outcome summaries; restricted: no secret storage, no
  silent overwrite of strategic fields, no unreviewed replacement of approved
  context. AI may propose / enrich / summarize / classify / recommend, never silently
  overwrite approved context (`:594-603`). *Access* authorization defers to **DEC-026**
  (`domains.md:2487`, Client Brain "access only"); *physical* retrieval and storage
  defer to **Phase 7**.
- **Boundary notes.** **Partitioning: per-Brand (DEC-045):** Client Brain is
  partitioned per Brand, with a per-Client aggregation view for cross-brand context;
  Q-003 resolved (DEC-036). Aggregate-vs-Memory-Object status stays draft
  (`domains.md:1325-1336`). Client Brain may hold durable Brand-related memory without
  owning Brand identity (`:3698-3700`).

## Agency Brain
- **Definition.** The organization-wide reusable memory layer — agency-level
  knowledge, distinct from client-specific memory (`domains.md:1396-1398`).
- **Owner (Phase-1).** Knowledge (`domains.md:1254`, Knowledge "What it owns").
  Entity: Agency Brain Entry (`:1290`).
- **Contents.** Agency-wide reusable knowledge: methods, templates, standards, and
  reusable guidance (Organizational Knowledge bounded context, `domains.md:1342-1348`).
- **Lifecycle / durability.** Updated and surfaced via the "agency brain updated"
  event (`domains.md:1429`); durable agency knowledge follows the Knowledge durability
  path (artifact created → approved → superseded, `:1423-1425`).
- **Retrieval & update contract.** Reusable across workflows (cross-workflow memory
  reuse, `domains.md:1242`). Access authorization defers to DEC-026; physical
  retrieval / indexing defers to Phase 7.
- **Boundary notes.** Distinct from Client Brain — organization-wide vs
  client-specific (`domains.md:1364-1370` vs `:1396-1398`). Not interpretive analytics
  (Intelligence; risk of overlap `:1441-1442`).

## Knowledge Base
- **Definition.** The store of reusable organizational knowledge artifacts —
  structured reusable memory objects, not mere document files (`domains.md:1257`,
  `:1378-1379`).
- **Owner (Phase-1).** Knowledge (`domains.md:1257`). Entities: Knowledge Artifact,
  Knowledge Entry, Playbook, Knowledge Version (`:1281-1293`).
- **Contents.** Knowledge artifacts with content body / structured payload, tags,
  version state, retrieval metadata, and approval state (Knowledge Artifact Aggregate,
  `domains.md:1299-1306`); reusable playbooks and knowledge artifacts (`:1259`).
- **Lifecycle / durability.** Knowledge artifact created → approved → superseded
  (`domains.md:1423-1425`), with version visibility maintained (Knowledge Version,
  `:1241`, `:1292`). Which artifact types require explicit approval before becoming
  durable reusable knowledge is **open** (`:1451-1452`).
- **Retrieval & update contract.** Retrieval-ready structuring and cross-workflow
  reuse (`domains.md:1240-1242`). Access authorization defers to DEC-026; physical
  indexing / storage defers to Phase 7.
- **Boundary notes.** Risk: an unbounded dumping ground if artifact types are not kept
  explicit (`domains.md:1436-1438`). Whether Decision Log and Learning Record are
  separate aggregates or specialized Knowledge Artifact types is open (`:1453-1455`).

## Decision Logs
- **Definition.** The durable record of decisions and their rationale — preserving
  *why* a decision was made, not only the final state, because Faraz OS is
  human-governed (`domains.md:1350-1355`, `:1381-1383`).
- **Owner (Phase-1).** Knowledge (`domains.md:1258`). Entity: Decision Log (`:1283`).
- **Contents.** Decision summary, rationale, decision-maker references, effective
  date, and linked domain references (Decision Log Aggregate, `domains.md:1308-1315`);
  audit-friendly knowledge trails and decision visibility over time (Decision Memory
  bounded context, `:1350-1355`).
- **Lifecycle / durability.** Inbound: decision made / decision revised
  (`domains.md:1404-1405`); surfaced via "decision logged" (`:1423`). Retained for
  decision visibility and audit over time (`:1351-1352`).
- **Retrieval & update contract.** Retained as an audit-friendly trail (`domains.md:1354`).
  Access authorization defers to DEC-026; physical retrieval defers to Phase 7.
- **Boundary notes.** Aggregate granularity — own aggregate vs specialized Knowledge
  Artifact type — is open (`domains.md:1453-1455`).

## Learnings
- **Definition.** Durable reusable learnings — reusable insight produced by execution,
  review, correction, and outcome analysis (`domains.md:1259`, `:1385-1386`).
- **Owner (Phase-1).** Knowledge (`domains.md:1259`). Entity: Learning Record (`:1284`).
- **Contents.** Learning record with source context, confidence / validation state,
  reusable recommendation, and linked workflow / domain references (Learning
  Aggregate, `domains.md:1317-1323`); post-execution learnings, recurring patterns,
  validated improvements, and reusable lessons (Learning Memory bounded context,
  `:1354-1359`).
- **Lifecycle / durability.** Inbound: learning generated → learning approved
  (`domains.md:1406-1407`); surfaced via "learning published" (`:1424`). **The
  threshold at which an insight becomes durable knowledge is Phase-1 Intelligence
  truth, pending (`domains.md:1946`) — this entry references it at altitude and defines
  no threshold and no mechanism (G-7 / R-027).** Which artifact types require explicit
  approval before becoming durable is likewise open (`:1451-1452`).
- **Retrieval & update contract.** Reusable across workflows — the continuous learning
  loop (Principle #9, `principles.md:27-28`; cross-workflow reuse `domains.md:1242`).
  Access authorization defers to DEC-026; physical retrieval defers to Phase 7.
- **Boundary notes.** Not interpretive analytics: Intelligence computes insight;
  Knowledge holds the durable learning once it qualifies (`domains.md:1441-1442`). The
  insight→durable threshold stays with Phase-1 Intelligence (G-7).

## Context Retrieval
- **Definition.** The retrieval layer — indexing, memory references, retrieval slices,
  and context packaging that make memory available to workflows and AI execution
  (`domains.md:1371-1376`).
- **Owner (Phase-1).** Knowledge (`domains.md:1262`). Entities: Retrieval
  Context, Memory Reference (`:1288-1289`).
- **Contents.** Indexes, memory references, retrieval slices, and context packages for
  workflows and AI execution (Retrieval Context Management bounded context,
  `domains.md:1371-1376`); memory references and knowledge indexing (`:1261`).
- **Lifecycle / durability.** Inbound: retrieval context requested
  (`domains.md:1417`); outbound: retrieval context prepared (`:1427`). Retrieval
  contexts are prepared on request to package existing durable memory for consumers;
  they are derived from the durable structures above, not a separate source of truth.
- **Retrieval & update contract.** Packages context for consumers (workflows, AI
  execution) at altitude. **The physical retrieval mechanism — indexing, search
  implementation, data paths — is Phase 7** and is not specified here. Access
  authorization defers to DEC-026.
- **Boundary notes.** Risk: retrieval structures over-designed too early, before core
  artifact types stabilize (`domains.md:1443-1444`). Canon notes the depth of
  retrieval modeling as a deferral (`:1453-1454`); Phase 5 names the contract and
  defers implementation to Phase 7.

---

## Deferred sub-item (flagged stub)

### Asset Intelligence  *(deferred)*
Listed among the Phase 5 sub-items as `[ADDED]` (`Faraz-OS-Canon.md:113`) with thin
domain evidence — only asset *references* appear in canon (`relevant_assets_refs`,
`domains.md:517`). Per DEC-027 / G-3 it is a **deferred-and-flagged stub**: no
contents, lifecycle, or contract are authored here. It is un-deferred only by its own
gated decision, at which point it takes the six-field skeleton.

---

## Non-goals
Per DEC-027, `memory.md` does **not** contain: physical storage, indexing, data
schema, or AI-retrieval implementation (Phase 7); domain-entity ownership or
authoritative meaning beyond the DEC-027 Client Brain resolution (Phase 1); surfaces
/ views / portals (Phase 2 — Client Brain Surface / Knowledge Workspace render
memory, name-only); ordered sequences or the Learn → Memory Update orchestration
(Phase 6); capability *definitions* (Phase 3 — capabilities *produce* outputs that
may become durable knowledge); authorization / access / policy rules (Phase 1
Governance / DEC-026); resolution of inherited Phase-1 questions (incl. the
insight→durable-knowledge threshold, `domains.md:1946`); the deep content of the
deferred Asset Intelligence sub-item; and implementation technology.

## Cross-phase boundaries (closed seven-boundary set, DEC-027)
- **↔ Phase 1 domain truth.** Knowledge owns these structures (`domains.md:1254-1265`);
  Client Brain owned by Knowledge (DEC-027). Phase 5 architects, never re-owns.
- **↔ Phase 1 Governance.** Access authorization is DEC-026's (`domains.md:2487`);
  `memory.md` authors none.
- **↔ Phase 2.** Surfaces / views render memory (Client Brain Surface, Knowledge
  Workspace) — name-only.
- **↔ Phase 3.** Capabilities produce outputs that *may become* durable knowledge
  (`capabilities.md:61, 104, 148, 164`); `memory.md` owns what persists, not the
  producing ability.
- **↔ Phase 4.** Extensibility is a consumer of memory contracts; it deferred
  storage / retention / memory-structure here (`extensibility.md:493`).
- **↔ Phase 6.** Learn → Memory Update is the sequence (`Faraz-OS-Canon.md:125`);
  `memory.md` owns the target and the update contract, not the orchestration.
- **↔ Phase 7.** Physical storage, indexing, data architecture, and AI-retrieval
  implementation are out — Phase 7.

## Open and inherited flags
- **Client Brain Aggregate vs Memory Object** — draft (`domains.md:1325-1336`).
- **Insight → durable-knowledge threshold** — `domains.md:1946`; Phase-1 Intelligence
  truth, pending (G-7 / R-027); referenced at altitude by the Learnings entry.
- **Approval-before-durable** and **Decision Log / Learning Record aggregate
  granularity** — open in canon (`domains.md:1451-1455`).
