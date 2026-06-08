# Workflow Design — Phase 6

## Purpose
`workflows.md` defines the logical orchestration layer of Faraz OS: the ordered
business workflows, their hand-offs, their human-approval gates, and the
cross-cutting constructs (agent chains, runtime semantics, loop/exception
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

This file is written in batches. **Batch A is written**: the file skeleton; the
three framing/construct sections (Human Approval Gates, Agent Chains, Workflow
Runtime); and the three cross-cutting loop/exception patterns (Escalation Loop,
Revision Loop, Failure/Exception Path). Batch A lands first because every flow
entry's field-3/4/5 references these cross-cutting sections — they exist before
any flow leans on them (FIND-033).

**Pending:** Batch B — the seven flow entries (Lead → Client, Client → Strategy,
Strategy → Production, Production → Approval, Approval → Publishing, Publishing →
Reporting, Learn → Memory Update) on the six-field skeleton. Batch C — non-goals,
open/inherited flags, and header cross-reference tidy.

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

## Per-workflow entry skeleton (for the Batch-B flows)
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
  what was approved / what was executed (`:44-49`) is a system property realized in
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
