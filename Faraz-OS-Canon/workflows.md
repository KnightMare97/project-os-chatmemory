# Workflow Design — Phase 6

## Purpose
`workflows.md` defines the logical orchestration layer of Faraz OS: the ordered
business workflows, their hand-offs, their human-approval gates, and the
cross-cutting constructs (agent chains, workflow runtime, loop/exception
patterns) through which Phase-3 capabilities are sequenced into governed,
end-to-end flows.

It names **what runs, in what order, with which hand-offs and gates, at
altitude**. It does not author capabilities (Phase 3), surfaces (Phase 2),
authorization rules (Phase 1 Governance / DEC-026), memory structure (Phase 5),
provider/model selection (Phase 4), or the execution engine and data paths
(Phase 7).

It records each workflow on a fixed entry skeleton.

---

## Altitude
Phase 6 sits at **logical orchestration altitude** (DEC-028 G-1): it names ordered
flows, gates, hand-offs, and the sequencing contract over Phase-3 capabilities. It
defines no execution engine, runtime technology, data paths, or AI architecture —
those are Phase 7. Workflows *invoke* capabilities by name; they do not redefine
them.

---

## Status
Phase 6 scope is defined and human-confirmed (**DEC-028 / Snapshot-036**).

This file was written in batches (dependencies-first, FIND-033). **The first write
is complete** (Batches A–C): the file skeleton; the three framing/construct sections
(Human Approval Gates, Agent Chains, Workflow Runtime); the three cross-cutting
loop/exception patterns (Escalation Loop, Revision Loop, Failure/Exception Path);
the seven flow entries (Lead → Client, Client → Strategy, Strategy → Production,
Production → Approval, Approval → Publishing, Publishing → Reporting, Learn → Memory
Update) on the six-field skeleton; the non-goals; and the open/inherited flags. The
cross-cutting sections were written before the flow entries that reference them, so
no flow's field-3/4/5 ever pointed at unwritten content.

No Phase 1 domain truth, ownership, or boundary is changed by this file. Phase 6
references Phase 1; it does not reinterpret it. It resolves no inherited Phase-1
question (R-027).

---

## Governing rules (referenced, not restated here)
This file **applies** the Phase 6 rules fixed by **DEC-028**; it does not restate
them. Recorded there:
- the Phase 6 definition / logical altitude (G-1);
- the closed boundary set — a definition/altitude line plus seven cross-phase
  boundaries, Phase 1 split into two facets (G-2);
- the two governing altitude tests: the **selection-vs-sequence test**
  (`decisions.md:823-830`) and the **approve-verb vs approval-gate test**
  (`decisions.md:1015-1018`);
- the six-field per-workflow skeleton (G-4);
- the non-goals (G-5) and the carried set (G-7).

The two new litmus tests authored at this gate — **role-vs-identity** (Agent
Chains) and **P6↔P7** (Workflow Runtime) — are recorded verbatim in their
sections below, per DEC-028 G-6(b)/(c).

---

## Per-workflow entry skeleton (the seven flow entries below)
Each flow entry carries six fields (DEC-028 G-4):
1. **Definition** — what the workflow accomplishes; the ordered intent.
2. **Trigger / entry condition** — what starts it.
3. **Ordered steps & hand-offs** — the capabilities invoked (Phase-3 reference,
   name-only) and the sequence and hand-offs between them.
4. **Gates & human-involvement mode** — where approval gates sit and the
   involvement mode (see *Human Approval Gates*).
5. **Exception / loop behavior** — references the loop/exception patterns (see
   *Loop and Exception Patterns*) and the runtime semantics (see *Workflow
   Runtime*); it does not restate them.
6. **Cross-phase boundary notes** — what the entry references versus owns
   (reference altitude, R-028).

---

## Human Approval Gates
An **approval gate** is a point in an ordered workflow where the flow **suspends
for a human intervention** before proceeding. Phase 6 owns *where a gate sits and
in what mode*; **who may approve** is Phase 1 / DEC-026 (the `approve`
authorization verb). This is the approve-verb vs approval-gate boundary: who *may*
approve = Phase 1; *when* approval occurs in an ordered flow = Phase 6
(`decisions.md:1015-1018`).

- **Intervention forms.** A gate may take any of the human-intervention forms
  named in the human-in-the-loop philosophy: approval, review, correction,
  rejection, escalation, override (`human-in-the-loop-philosophy.md:10-16`).
- **Involvement mode (referenced owning definition).** Each gate is placed within
  a workflow whose human-involvement level follows the philosophy's mode
  vocabulary — **human-in-the-loop**, **human-on-the-loop**, or **hybrid by
  design** (`human-in-the-loop-philosophy.md:18-22`). Phase 6 references this
  vocabulary as its owning definition; it does not redefine the modes. Field-4 of
  each flow entry names its mode using these terms.
- **Default checkpoint for client-facing publishing.** Client-facing publishing
  carries a human checkpoint **by default, but this checkpoint must remain
  configurable based on workflow policy** (`human-in-the-loop-philosophy.md:31-32`,
  quoted verbatim). Phase 6 places the default gate; it does **not** author the
  policy mechanism that configures it — that is Phase 4 (extension/policy) /
  Phase 7 (runtime), referenced at altitude.
- **Placement guidance (cited principle, not a rule table).** Gate placement is
  guided by the philosophy's intensify-when principle — review intensifies when
  risk is high, confidence is low, ambiguity is high, policy may be violated, or
  external publication / irreversible execution is involved
  (`human-in-the-loop-philosophy.md:24-29`). A flow's field-4 **may** name which
  of these motivated a gate; Phase 6 does **not** enumerate these conditions as a
  rule table, and authors no risk classification (that is policy / Phase 1
  Governance territory).
- **Boundary guard.** Gate placement and mode = Phase 6. Who may approve =
  Phase 1 / DEC-026. Auditability of what AI proposed / what the human changed /
  what was approved / what was executed (`human-in-the-loop-philosophy.md:44-49`) is
  a system property realized in
  Phase 7; Phase 6 only marks where the gate sits.

---

## Agent Chains
An **agent chain** is an ordered sequence of **agent-performed steps** with
hand-offs, sequenced inside a governed workflow. Faraz OS supports agents,
subagents, and orchestrated execution patterns collaborating **inside governed
workflows** (`ai-philosophy.md:24-25`); the *orchestration* of those chains is
Phase 6 (DEC-025, `extensibility.md:378-385`). This section owns the orchestration
contract **only**.

**Role-vs-identity litmus (recorded verbatim, DEC-028 G-6(b)):**
> *Names where an agent-performed step sits in a sequence and what it hands off →
> Phase 6. Defines what the agent is (identity, surface, executing AI
> architecture) → Phase 7. Defines how the agent is chosen among interchangeable
> agents by policy → Phase 4.*

- **Role placeholders only.** An agent chain names agent steps at **capability
  altitude** — by role (e.g. "content-drafting agent role"), never a concrete
  agent, product, or architecture. If a step cannot be expressed without identity
  vocabulary, the litmus has fired: **escalate, do not write around it.**
- **Per-step execution mode.** Each step's execution mode — AI, human, or hybrid —
  **references** the Phase-3 capability execution-mode attribute
  (`capabilities.md:79-80`) and the *Human Approval Gates* mode vocabulary. Phase 6
  does not redefine execution mode, and never narrows a step to AI-only (Core
  Principle #1, "AI-first, but not AI-only," `principles.md:3`).
- **Identity stays deferred.** Agent / subagent **identity** — what an agent *is*,
  its surface, the AI architecture that executes it — remains the registered
  Phase-7 open flag (`extensibility.md:345-347`, `:457-459`), cited here as
  deferred, not partially resolved.

---

## Workflow Runtime
This is a **framing section** (modeled on the Runtime vs Config-Time Extensions
framing precedent, `extensibility.md:396-415`); it is not a per-workflow skeleton
entry. It defines the **logical runtime semantics** the ordered flows presuppose.

**Three senses of "runtime" — disambiguated:**
1. **Phase 4 — Runtime vs Config-Time:** a *binding attribute* — *when* an
   extension binding may change (runtime versus configuration/deployment-time)
   (`extensibility.md:396-415`). Not this section.
2. **Phase 6 — Workflow Runtime (this section):** what a workflow *means while
   running* — its logical lifecycle, gate suspend/resume semantics, and how
   loops/exceptions behave semantically.
3. **Phase 7 — Runtime Architecture:** the *engine* that executes workflows
   (`Faraz-OS-Canon.md:138`). Out of scope here.

**P6↔P7 litmus (recorded verbatim, DEC-028 G-6(c)):**
> *Defines what a workflow means while running — its logical lifecycle states,
> what suspends/resumes at a gate, how a loop/exception behaves semantically →
> Phase 6 Workflow Runtime. Defines the engine that executes workflows —
> schedulers, queues, process model, state persistence, deployment runtime →
> Phase 7 Runtime Architecture.*

- **Logical lifecycle states (semantic, not mechanism).** A workflow instance is,
  at any time, in one of a small set of *semantic* states: not yet started; in
  progress; awaiting a human decision at a gate; in a revision loop; in an
  exception path; completed; or ended without completing (exception handled). These
  are described by meaning, never by mechanism.
- **Gate semantics.** At an approval gate the workflow **suspends** (awaits a human
  decision) and **resumes** along the branch the decision selects — proceed on
  approval; enter a revision loop on correction/rejection; enter an escalation loop
  on escalation. "Suspend" and "resume" are semantic states, not a scheduler or a
  persisted process.
- **Firewall.** This section uses **no** engine vocabulary — no scheduler, queue,
  process model, state persistence, or deployment-runtime terms. Each lifecycle
  state is stated in semantic terms ("awaiting a human decision at a gate"), never
  mechanism terms. If a state cannot be written without engine vocabulary, the
  litmus has fired: **escalate, do not write around it.**
- **Standing policing note.** Any future edit to this section re-applies the P6↔P7
  litmus in review. This is the highest reference-altitude-overcommitment surface
  in Phase 6 (R-028).

---

## Loop and Exception Patterns
Three cross-cutting patterns, **defined once here and referenced by each flow's
field-5** (DEC-028 G-3 form B / G-4) — they are not restated per flow. Each
describes *semantic* behavior and defers runtime mechanism to *Workflow Runtime*
(and ultimately Phase 7).

### Escalation Loop
- **What it is.** A pattern in which a decision or step is routed to a
  higher-authority human when it exceeds the current actor's scope — the
  *escalation* intervention form (`human-in-the-loop-philosophy.md:15`).
- **When it triggers.** Typically where review should intensify — high risk, low
  confidence, high ambiguity, possible policy violation, or irreversible /
  external execution (`:24-29`, cited as guiding principle, not a rule table).
- **Semantic behavior.** The workflow enters the *escalation* lifecycle state
  (awaiting a higher-authority human decision); on resolution it resumes along the
  selected branch. Who may act on the escalation is Phase 1 / DEC-026; this pattern
  only names that the escalation occurs and where control goes.

### Revision Loop
- **What it is.** A pattern in which a produced artifact is returned to a prior
  step for rework after a **correction** or **rejection** at a gate
  (`human-in-the-loop-philosophy.md:13-14`).
- **When it triggers.** At an approval gate whose human decision is correction or
  rejection rather than approval.
- **Semantic behavior.** The workflow enters the *revision* lifecycle state and
  re-enters the named predecessor step (the hand-off back is part of the flow's
  ordered steps, field-3); on the next gate it re-evaluates. The pattern names the
  return path semantically; it does not bound the number of iterations (that is
  policy / runtime, referenced not authored).

### Failure/Exception Path
- **What it is.** A pattern for when a step **cannot complete** — e.g. an invoked
  capability or its provider/channel binding (Phase 4, named only) does not
  succeed.
- **When it triggers.** On a non-completing step outcome that is not a human
  correction/rejection (those are the Revision Loop).
- **Semantic behavior.** The workflow diverts to a defined exception path: it
  enters the *exception* lifecycle state, a human is notified per the flow's gate
  and notification context, and the workflow either resumes (if the exception is
  resolved) or ends without completing (exception handled). This pattern authors
  **no** retry mechanism, scheduler, or queue — retry/backoff and execution
  recovery are Phase 7 Runtime Architecture, referenced at altitude per the P6↔P7
  litmus.

---

## Workflows
Each entry uses the six-field skeleton above. Capabilities are referenced **by
name only** (Phase 3); gates and modes follow *Human Approval Gates*;
exception/loop behavior references the patterns above. No capability, surface,
authorization rule, agent identity, or visual workflow-management capability
(Q-017, registered open) is authored here.

### Lead → Client
- **Definition.** Converts a qualified inbound lead into an established client
  relationship.
- **Trigger / entry condition.** A new lead enters the pipeline (lead-intake
  event).
- **Ordered steps & hand-offs.** Lead intake → **Lead Scoring**
  (`capabilities.md:215`) produces a score/qualification → hand-off to a human
  conversion decision → on conversion, the client relationship is established and
  hands off to *Client → Strategy*.
- **Gates & human-involvement mode.** A conversion **approval** gate; typically
  **human-in-the-loop** (a person owns the convert/decline decision). Who may
  approve = Phase 1 / DEC-026.
- **Exception / loop behavior.** Decline or "needs more info" routes via the
  **Revision Loop** (back to qualification) or ends without completing; a
  scoring/provider failure follows the **Failure/Exception Path**.
- **Cross-phase boundary notes.** Invokes Lead Scoring (P3, name-only); lead and
  client entity meaning is Phase 1; presenting surfaces are Phase 2; who may
  convert is DEC-026. Authors none of these.

### Client → Strategy
- **Definition.** Turns an established client's context into an approved strategy.
- **Trigger / entry condition.** A client is established (hand-off from *Lead →
  Client*) or a new strategy cycle begins.
- **Ordered steps & hand-offs.** **Research** (`capabilities.md:140`) gathers
  inputs → **Strategy** (`capabilities.md:156`) synthesizes a strategy artifact →
  hand-off to a client approval gate → approved strategy hands off to *Strategy →
  Production*.
- **Gates & human-involvement mode.** A client-facing strategy **approval** gate;
  **hybrid by design** (AI drafts, human and client review).
- **Exception / loop behavior.** Client correction/rejection routes via the
  **Revision Loop** to Strategy (or Research); scope beyond the team's authority
  follows the **Escalation Loop**; capability failure follows the
  **Failure/Exception Path**.
- **Cross-phase boundary notes.** Invokes Research and Strategy (P3, name-only);
  strategy-artifact ownership/meaning is Phase 1; client-approval surfaces are
  Phase 2; authorization is DEC-026.

### Strategy → Production
- **Definition.** Produces the content assets an approved strategy calls for.
- **Trigger / entry condition.** A strategy is approved (hand-off from *Client →
  Strategy*).
- **Ordered steps & hand-offs.** **Content Creation** (`capabilities.md:121`) and,
  where the asset is video, **Video Creation** (`capabilities.md:172`) produce
  draft assets → hand-off to *Production → Approval*. Where a step is
  agent-performed it is named at **role altitude** (e.g. a content-drafting agent
  role); naming a concrete agent identity fires the role-vs-identity litmus →
  escalate.
- **Gates & human-involvement mode.** Production may run **human-on-the-loop** (AI
  produces, human monitors) or **hybrid by design**; humans may also be the
  primary producer (`human-in-the-loop-philosophy.md:34-36`). Per-step execution
  mode references the capability execution-mode attribute (`capabilities.md:79-80`).
- **Exception / loop behavior.** An asset later corrected/rejected at approval
  returns here via the **Revision Loop**; a production/provider failure follows the
  **Failure/Exception Path**.
- **Cross-phase boundary notes.** Invokes Content Creation / Video Creation (P3,
  name-only); tooling/providers are Phase 4; agent identity is the deferred
  Phase-7 flag; asset domain meaning is Phase 1.

### Production → Approval
- **Definition.** Moves produced assets through internal review and client
  approval.
- **Trigger / entry condition.** Assets are produced (hand-off from *Strategy →
  Production*).
- **Ordered steps & hand-offs.** Produced asset → internal **review** gate →
  client **approval** gate → approved asset hands off to *Approval → Publishing*.
- **Gates & human-involvement mode.** Two gates — an internal **review** and a
  client-facing **approval**; **human-in-the-loop** by default. Review intensity
  is guided by the intensify-when principle (`human-in-the-loop-philosophy.md:24-29`),
  named per gate, not enumerated as a rule.
- **Exception / loop behavior.** Correction/rejection at either gate routes via the
  **Revision Loop** to *Strategy → Production*; an authority-exceeding decision
  follows the **Escalation Loop**.
- **Cross-phase boundary notes.** Authors no capability (this flow is gates +
  hand-offs); who may review/approve = Phase 1 / DEC-026; the review/approval
  surfaces (e.g. Review Queue, Client Approval Queue) are Phase 2.

### Approval → Publishing
- **Definition.** Dispatches an approved asset to its channel.
- **Trigger / entry condition.** An asset is approved (hand-off from *Production →
  Approval*).
- **Ordered steps & hand-offs.** Approved asset → **Publishing**
  (`capabilities.md:73`, the atomic push) → dispatched item; a publish-completing
  event hands off to *Publishing → Reporting*. **Cross-item queueing/sequencing is
  orchestration here, not the capability** (Q-015 resolved → Phase 6, DEC-028).
- **Gates & human-involvement mode.** Client-facing publishing carries a human
  checkpoint **by default, but this checkpoint must remain configurable based on
  workflow policy** (`human-in-the-loop-philosophy.md:31-32`); Phase 6 places the
  default gate, the policy mechanism is Phase 4 / Phase 7. Mode:
  **human-in-the-loop** for client-facing publishing by default.
- **Exception / loop behavior.** A dispatch failure follows the
  **Failure/Exception Path** (retry/recovery is Phase 7); a late rejection routes
  via the **Revision Loop**.
- **Cross-phase boundary notes.** Invokes Publishing (P3, name-only); the channel
  integration is Phase 4; cross-item queueing altitude is Phase 6 (Q-015 /
  DEC-028) — this flow owns the sequencing, not a capability.

### Publishing → Reporting
- **Definition.** Turns dispatched content and its outcomes into reporting.
- **Trigger / entry condition.** A **publish step completing** — a workflow event
  (Phase 6) that Phase 2 references for notification UX
  (`experience-architecture.md:844-846`).
- **Ordered steps & hand-offs.** Dispatched item → **Analytics**
  (`capabilities.md:189`) computes metrics → **Reporting** (`capabilities.md:95`)
  composes the report → report delivered; outcomes hand off to *Learn → Memory
  Update*.
- **Gates & human-involvement mode.** Often **human-on-the-loop** (AI
  computes/composes, human reviews before client delivery); a client-facing report
  delivery may carry an approval gate per policy.
- **Exception / loop behavior.** A metrics/data failure follows the
  **Failure/Exception Path**; a report correction routes via the **Revision Loop**
  to Reporting.
- **Cross-phase boundary notes.** Invokes Analytics and Reporting (P3, name-only);
  the triggering events are Phase 6 (referenced by Phase 2 for notifications);
  KPI/metric meaning is Phase 1 / Phase 3.

### Learn → Memory Update
- **Definition.** Captures outcomes, corrections, and decisions from across the
  workflows into durable memory and knowledge.
- **Trigger / entry condition.** A learning event — any approval, rejection, edit,
  escalation, override, or outcome (`human-in-the-loop-philosophy.md:41-42`);
  realizes Core Principle #9 (continuous learning loops, `principles.md:27-28`).
- **Ordered steps & hand-offs.** Outcome/feedback captured → routed into the
  Phase-5 memory/knowledge **update contract** (the Learnings structure and related
  memory; `memory.md:210-211` — Phase 6 owns this orchestration, Phase 5 owns the
  target and the update contract).
- **Gates & human-involvement mode.** Typically **human-on-the-loop**; a human may
  confirm before an insight becomes durable, where policy requires.
- **Exception / loop behavior.** A capture/update failure follows the
  **Failure/Exception Path**.
- **Cross-phase boundary notes.** Updates Phase-5 memory (target + contract are
  Phase 5, `memory.md`); the **insight→durable-knowledge threshold** is inherited
  Phase-1 Intelligence truth, referenced at altitude and **not resolved here**
  (R-027, `domains.md:1918`). Authors no memory structure and no threshold.

---

## Non-goals
Per DEC-028 (G-5), `workflows.md` does **not** contain:
- capabilities — reusable functional abilities are Phase 3 (`capabilities.md`),
  referenced by name only;
- surfaces, views, portals, or the Permission Matrix — Phase 2
  (`experience-architecture.md`);
- authorization / permission / policy rules, or who may approve — Phase 1
  Governance / DEC-026 (workflows place gates, they do not authorize actors);
- memory / knowledge structure, or the insight→durable-knowledge threshold —
  Phase 5 (`memory.md`) and inherited Phase-1 truth;
- provider / channel / model selection or routing — Phase 4 (`extensibility.md`);
- domain-entity ownership or authoritative meaning — Phase 1 (`domains.md`);
- the execution engine, scheduler, queue, state persistence, data paths,
  deployment runtime, or AI architecture — Phase 7;
- agent / subagent identity, surface, or executing architecture — the registered
  Phase-7 flag.

It resolves no inherited Phase-1 question (R-027) and holds reference altitude
throughout (R-028).

---

## Open and inherited flags
Carried, referenced, not resolved here:
- **Q-017 (new this gate, registered).** The system administrator's **visual
  viewing and management** (update / add / remove) of workflows. Viewing is
  partially covered by the Phase-2 Agent & Workflow Monitor surface (System
  Administrator Full, `experience-architecture.md:239`); the new part — visual
  workflow **editing / management** — has candidate homes across Phase 2 (surface),
  Phase 6 (workflow definitions as configurable artifacts), Phase 4 (config-time
  binding), and Phase 7 (engine support). **Multi-phase placement is its own gated
  decision later**; this file authors no visual workflow-management capability. See
  `open-questions.md` (Q-017).
- **Agent / subagent identity** — what an agent *is*, its surface, and the AI
  architecture that executes it: the registered Phase-7 flag
  (`extensibility.md:345-347`, `:457-459`). Agent Chains name roles, never
  identities (role-vs-identity litmus).
- **Q-012 (Phase 7 ↔ Phase 8 boundary)** — deferred until Phase 6 is complete
  (`open-questions.md:268`); Phase-6 completion is its downstream unblock trigger.
  Not resolved here.
- **Inherited Phase-1 questions (R-027)** — Q-003 (Brand placement), Q-004 (Client
  Brain partitioning), and the insight→durable-knowledge threshold
  (`domains.md:1918`): referenced at altitude, resolved by their owning Phase-1
  work, not here.
- **R-028 reference-altitude guards** — the role-vs-identity and P6↔P7 litmuses are
  the active guards; Workflow Runtime is the highest-overcommitment surface and
  carries a standing policing note.
