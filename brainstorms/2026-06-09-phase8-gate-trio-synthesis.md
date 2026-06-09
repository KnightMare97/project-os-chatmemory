# Phase 8 Gate — THREE-LENS TRIO Synthesis
**2026-06-09 | Non-canon brainstorm | Feeds DEC-040**

## Purpose
Records the PM / Workflow / System THREE-LENS TRIO analysis run against the Phase 8
question-gate (G-1…G-8), specifically G-6 (Core Layer content + Core↔Infrastructure
cut) and G-8 (AI Layer blocks + Experience↔AI seam). Not canon. Governs nothing on its
own. All rulings are in DEC-040.

---

## G-1 through G-5 (Structural-Autonomous)

All five gates were ruled structural-autonomous (no trio required):
- **G-1 altitude/definition:** Phase 8 = layered assembly; boundary test from DEC-030
  verbatim in DEC-040.
- **G-2 closed boundary set:** assembled-from map across P1/P2/P3/P4/P7; P8↔P9
  abstract-vs-physical cut; P7↔P8 boundary test.
- **G-3 all 7 layers first-write firm:** no stub; all seven receive full entries.
- **G-4 per-layer skeleton:** 5-field analog (Definition · Source phases · Assembled
  blocks · Boundary notes · Carried/deferred).
- **G-5 non-goals:** explicit list of what `architecture.md` must not author.

---

## G-6 — Core Layer Content

### PM Lens

**Orphan/extend test:**
- Does Core need a new domain? No — Core is the platform shell, not a business domain.
- Extend test (from P7 Application + Security Architecture): Core blocks are already
  named in Phase 7 as the application hosting + enforcement mechanisms; Phase 8 places
  them on the board.

**Business logic perspective:**
- A paying client would immediately understand: "Core is what makes Faraz OS a platform
  rather than a bespoke app." The Configurable Core Host is the product thesis made
  runnable. The Feature-Module Mounting Engine is what makes the base-plus-modules
  promise real at runtime.
- The Extension Contract Surface is the stability guarantee: "extensions change, the
  core doesn't break." This is a PM-level promise, not just an engineering detail.
- Authorization Enforcement + Per-Client Isolation = the trust and multi-tenancy floor.
  Even single-tenant, per-client isolation is a fundamental product guarantee.
- Credential / Secret Handling = the operational safety guarantee.
- Platform Context Services = the invisible glue; without it, no component knows which
  client's context it's operating in.

**Phase-6 boundary catch (PM perspective):**
- Approval gates and lifecycle state machines are Phase 6 workflow runtime concerns.
  From a PM viewpoint, these are "what flows do" not "what the platform is." Phase 8
  must not claim them.

### Workflow Lens

**Does any workflow invoke "mount a module"?**
- No workflow explicitly calls "mount a module." Workflows invoke capabilities; the
  mounting machinery is invisible to the workflow layer.
- Evidence: the Feature-Module Mounting Engine is Core, not invoked by Phase 6 flows —
  this confirms it belongs in Core, not Capabilities or Plugins.

**What workflows depend on that IS Core?**
- All workflows assume: a valid client context exists (Platform Context Services).
- All workflows that touch external systems assume: credentials are available and
  scoped (Credential / Secret Handling Block).
- All approval flows assume: authorization enforcement is working (Authorization
  Enforcement Block).

**Phase-6-not-Core flag (critical):**
- The Workflow lens found: approval gate mechanism, lifecycle state machine,
  loop/exception pattern router — all Phase 6-owned constructs (`workflows.md`).
  Phase 8 may note "Core Layer depends on the Phase 6 workflow runtime"; it may NOT
  name these as Core blocks. This is the most important Workflow lens contribution.

### System Lens

**Data-model implications of Core blocks:**
- Configurable Core Host: no domain data (it's the shell).
- Feature-Module Mounting Engine: mount registry (which modules are mounted, status)
  — infrastructure-adjacent but still Core (the registry IS the platform's extension
  state).
- Extension Contract Surface: contract definitions, versioning → Phase 4 owns; Core
  holds the enforcement boundary.
- Authorization / Isolation / Credential blocks: no new domain data — they enforce
  over existing Phase 1 / Phase 2 data.
- Platform Context Services: client session state → ephemeral Core context, not domain
  data.

**Core↔Infrastructure cut (System lens):**
- The system lens proposed the definitive rule: the auth backing service is a resource
  the Core blocks call into — it is Infrastructure. The enforcement LOGIC is Core.
- Same pattern: the secret store is Infrastructure (where secrets are persisted); the
  credential handling block is Core (how credentials are scoped/rotated/applied).
- This parallel exactly mirrors P4/P7: contract definition = P4; execution engine = P7.

### Reconciled Core Recommendation (all three lenses)

Seven blocks confirmed:
1. Configurable Core Host (`blueprint.md:157-159`)
2. Feature-Module Mounting Engine (`extensibility.md:458-459, :464-465`)
3. Extension Contract Surface (`extensibility.md:196`)
4. Authorization Enforcement Block (`blueprint.md:361-363`)
5. Per-Client Isolation Enforcer (`blueprint.md:364-366`)
6. Credential / Secret Handling Block (`blueprint.md:367-369`)
7. Platform Context Services (canon-endorsed by trio exclusion)

Core↔Infrastructure governing rule: enforcement logic = Core; backing substrate = Infrastructure.

Phase-6-not-Core guard: unanimous across all three lenses.

---

## G-8 — AI Layer Seam

### PM Lens

**What does a PM want from "the AI Layer"?**
- "Name the AI execution blocks so an engineer can point at them in the architecture."
- Five blocks satisfy this completely: Agent/Subagent Execution Unit (what an AI task
  runner is), Chain Orchestrator (how they compose), Routing Engine (how model
  selection executes), Model Invocation Interface (how a specific model is called),
  Human/Hybrid Execution Path (how the system handles non-AI work).
- These are legible to a PM: "AI is a set of execution primitives, not magic."

**Q-017 from PM perspective:**
- Q-017 (visual workflow management) is a product feature question, not an AI Layer
  architecture question. Its resolution may ADD a block to the AI Layer, but it cannot
  be decided here. Carry open.

### Workflow Lens

**Which AI Layer blocks does the workflow invoke?**
- Phase 6 workflows invoke: capabilities (Phase 3) → which in turn invoke AI execution.
  The AI Layer blocks are the runtime substrate that capabilities use.
- The Chain Orchestrator is the execution spine of every multi-step workflow.
- The Routing Engine executes policy (Phase 4) at every AI invocation point.
- Human/Hybrid Execution Path = every HITL step in every workflow.
- Agent/Subagent Execution Unit = the executing entity at every AI step.
- Model Invocation Interface = the call that goes to the actual model.

**Experience↔AI seam (Workflow perspective):**
- Workflows produce results. Those results surface in Phase 2 surfaces. The workflow
  never owns the rendering — that is Phase 2.
- The Agent & Workflow Monitor (`experience-architecture.md:239`) is Phase 2's surface
  for monitoring execution: it RENDERS results of AI Layer blocks, it is not an AI
  Layer block itself.

**Q-017 from Workflow perspective:**
- If Q-017 resolves to Phase 7 (an engine that can run editable workflow definitions),
  the Workflow lens predicts: Phase 6 would reference that engine at invocation points;
  Phase 2 would hold the editing/monitoring surface; Phase 8 AI Layer would name the
  engine block. But this is Q-017's own gated resolution. Carry open.

### System Lens

**Architecture implications of each AI Layer block:**
- Agent/Subagent Execution Unit: requires lifecycle management (state machine); agent
  instances must be traceable → this is the system-architecture identity model
  (DEC-031 G-6(a)).
- Chain Orchestrator: the composition layer; how steps are linked and how handoffs are
  managed between execution units.
- Routing Engine: stateless policy execution (the policy comes from Phase 4; the engine
  reads it and routes).
- Model Invocation Interface: the abstraction layer between the orchestration tier and
  the actual model API; swappable model contract from Phase 4.
- Human/Hybrid Execution Path: the HITL integration point — where execution waits for
  a human response and how that response re-enters the chain.

**Experience↔AI cut (System perspective):**
- The system boundary is clear: AI Layer blocks are execution-time components. Experience
  Layer blocks are rendering-time components. The data flow is one-way: AI Layer produces;
  Experience Layer consumes and renders.
- Agent-facing surface rendering is Phase 2 (Q-013 split; DEC-031 G-6(b)). This is a
  deliberate separation: the AI Layer must not contain rendering logic.

**Agent supervision (System flag):**
- The system lens noted that agent supervision (monitoring execution health,
  detecting stuck/failed agents) requires additional infrastructure. This is deferred
  per `blueprint.md:462-463` and carries open in Phase 8.

### Reconciled AI Layer Recommendation (all three lenses)

Five blocks confirmed:
1. Agent / Subagent Execution Unit (`blueprint.md:252-255`)
2. Chain Orchestrator (`blueprint.md:250-252`)
3. Routing Engine (`extensibility.md:391-392`; `blueprint.md:262-264`)
4. Model Invocation Interface (`extensibility.md:308`)
5. Human / Hybrid Execution Path (`blueprint.md:276-278`)

Two deferred slots:
- Q-017 Workflow Management Engine (pending Q-017 gate)
- Agent Supervision / Observability (own gated pass; `blueprint.md:462-463`)

Not in AI Layer: agent-facing rendering (→ Experience), routing POLICY (→ Plugins /
P4), UsageRecord (→ Domains / DEC-038), prompt/template versioning (→ Q-022 pending).

Experience↔AI cut: AI Layer produces; Experience Layer renders. The seam is the
produce→render handoff.

---

## PART A Cite Verification (performed before DEC-040 proposal)

All cites verified against working tree with sed. Key findings:
- `blueprint.md:361-363` (Authorization Enforcement): corrected from initially
  proposed `:360-362` — line 360 = section heading "Key decisions / mechanisms...";
  enforcement text starts at 361.
- `extensibility.md:196` (Extension Contracts heading): corrected from initially
  noted `:194` — confirmed via second sed pass.
- All other cites verified clean (19 total citations, all byte-confirmed).
- Stale-token sweep: zero living-doc cites into `decisions.md:2NNN` range;
  DEC-040 insertion creates no cascade.

---

*Non-canon. Filed for session continuity. All rulings in DEC-040.*
