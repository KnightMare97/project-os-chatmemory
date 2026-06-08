> NON-CANON grounding input — directional, not a decision; see grounding/Gap-and-Enhancement-Register.md.

# Phase 7 Grounding Brief — handoff to the next Code session

**Status:** working handoff brief, NOT canon. Not committed by default.
Delete or archive once the Phase 7 scope decision lands. It records pre-gate
thinking and Ali's system brief so the next session starts from his mental
model instead of cold. It authors no architecture and resolves nothing — the
Phase 7 question-gate still runs.

---

## 0. Re-ground first (do this before anything else)
- Verify head: `git -C ~/Documents/GitHub/project-os-chatmemory log --oneline -1`
  should be **`8b87ae2`** (Snapshot-040; Phase 6 complete) or later. Confirm a
  clean tree.
- The operating contract now lives in `CLAUDE.md` (§ Execution Mode and Approval
  Gates) — four gates, AUTO/GATED split, evidence discipline, the FIND-032/034
  citation rules. **Reviewer CLEAR counts as the explicit go** for record-only
  close-outs, record commits/tracker backfills, and reference-altitude knock-ons;
  Ali's explicit go is still required for new canon content, procedure changes,
  structural Linear, and posture calls.
- Citation discipline (FIND-033/034): every `domains.md` (and cross-file) cite is
  content-verified at its anchor, never token-matched; immutable history
  (snapshots, brainstorms, `decisions.md`) resolves cites against landing commits
  and is never retro-edited.

## 1. Where we are
- Phases 0–6 complete or first-write-complete. Phase 6 `workflows.md` is written
  and consistency-reviewed clean; **Phase 6 declared complete at DEC-028's scope
  (DEC-029)**, which fired **Q-012** (Phase 7 ↔ Phase 8 boundary).
- **The open thread is Q-012 — the Phase 7 ↔ Phase 8 boundary *scoping*. Scoping
  only; NO Phase-7/8 content before its own question-gate.** Linear KNI-11 is back
  to Todo with that guard.

## 2. Suggested sequence
1. **Resolve Q-012 first** (narrow: the P7↔P8 boundary) as its own gated decision.
2. **Then run the full Phase 7 scope gate** (a G-1…G-7-style question-gate, as in
   DEC-024/025/027/028), feeding it this brief.
Don't collapse the two — Q-012 is the registered immediate thread and is narrower
than full Phase 7 scoping.

## 3. Q-012 resolution hypothesis (Ali-aligned; ratify at the gate)
**Phase 7 is the substantive architecture — the seven concern-views; Phase 8
"Puzzle Board" is its layered assembly.** One-way dependency: P8 assembles to
satisfy P7; P7 is scoped/written first.

Proposed boundary test:
- *"How does the system handle [data / execution / AI / integration / security /
  runtime] as a cross-cutting concern?"* → **Phase 7** (a concern-view / lens).
- *"What concrete building blocks exist and which layer do they sit in — Core /
  Domains / Capabilities / Plugins / Infrastructure / Experience / AI?"* → **Phase 8**
  (the assembled board).
- *Re-defines what a domain / capability / plugin **is*** → neither; that is
  Phases 1/3/4, **referenced**.

Why: P7's seven sub-items are classic architectural views; P8's **seven** layers
(Core / Domains / Capabilities / Plugins / Infrastructure / Experience / AI —
`Faraz-OS-Canon.md:141-147`; this brief originally miscounted "five") are mostly
already-defined pieces (Domains P1, Capabilities P3, Plugins P4, Experience P2),
i.e. an *assembly* view, not a design layer. Rejected alternative (record it): "P8 is the
real architecture, P7 is conceptual preamble" — leaves P7 thin and wastes the
seven-view structure.

## 4. The inversion guard (the new R-028 for Phase 7)
Through Phase 6 the risk was engine-talk bleeding *into* logical phases. In
Phase 7 it flips: the risk is Phase 7 **re-deciding** domain/capability/workflow
truth instead of **referencing** it. Proposed Phase 7 litmus:
> *Architects **how** the system runs / stores / secures / integrates X → Phase 7.
> Re-defines **what** X is, who owns it, or its sequence → Phases 1/3/6,
> referenced.*

## 5. Naming-collision hazard + the fix
"Architecture" appears in both phase names, all seven P7 sub-items, and P8's title
— the three-way "runtime" trap at larger scale. **Fix = disambiguation, not
rename** (the proven "runtime" precedent; a rename is a wide-blast-radius phase-map
change). The Phase 7 scope doc opens by distinguishing
*architecture-as-concern-view (P7)* from *architecture-as-layered-assembly (P8)*,
with optional working nicknames ("the Blueprint" / "the Board"). Reserve an actual
rename only if the gate finds a name conceptually wrong, not merely colliding.

---

## 6. What Faraz OS does (Ali's system brief — informal, not final)
Synthesized and mapped to existing canon. Treat as Phase 7 grounding; flag
contradictions, route new domain truth to its owning phase — do not absorb.

**Strategic framing (decisive for altitude):** Faraz OS is **single-tenant** — one
agency (Ali's), its own operation, **no multi-tenant isolation to architect**. But
the **base** it runs on is the real product: a clean, module-mountable, **AI-native**
platform. Faraz OS is the **showcase build / reference architecture** for a business
that will build and develop AI-native business systems. So the value is the
*generalizable architecture as a demonstrable pattern*, instantiated once.

**Functional map (his brief → canon):**
- **CRM**, two halves — lead acquisition→conversion, and existing-client
  management/follow-up → **CRM** + **Client Success** domains; **Lead→Client**
  workflow; **Lead Scoring** capability.
- **Social-media services** — IG/FB/LinkedIn page management; video, story, caption,
  banner, logo, cover, motion graphics; **content calendar** → **Service Delivery**
  domain; **Content Creation** / **Video Creation** capabilities;
  **Strategy→Production→Approval→Publishing** workflow chain. Content-calendar
  scheduling sits near **Q-015** (resolved: cross-item queueing → Phase 6).
- **HR** — employees, contractors, panels; the editor sees today's schedule,
  progress, salary → **Workforce** domain + the Phase-2 personas/portals
  (Operator, Contractor, Manager, Admin) — *already designed in Phase 2*.
- **Financial section** → **Finance** domain (Draft v1 exists in `domains.md`).
- **AI doing repetitive/costly work, "chain modelling" (router-like), admin picks
  the model per part** → **Phase 4 AI Model Routing** (selection policy) +
  **Phase 6 Agent Chains** (orchestration); the **engine** that runs it is
  **Phase 7 AI Architecture**.
- **Services sold both as monthly packages and one-off units** (e.g. 3 IG reels, or
  one LinkedIn content calendar) → **Service Agreement** area — still a **draft**
  boundary (open Phase-1 question). Flag, don't absorb.

## 7. The four architectural signals for the seven views
1. **Module-mounting is the thesis, not a feature.** "A base where modules mount,
   base + modules both extensible/updatable." But **"Feature Modules" is a *deferred*
   Phase-4 sub-item.** Real cross-phase dependency for the gate to resolve: does
   Phase 7 just *reference* module-mounting, or does **Phase 4 Feature Modules need
   un-deferring first** because it's now load-bearing? (My read: flag it explicitly;
   likely Phase 7 architects the mounting mechanism while P4 owns the module
   contract — but that's a gate call.)
2. **AI-native ⇒ AI Architecture is the spine**, not one of seven equal views — but
   **AI-native is NOT AI-only.** Must honor Core Principle #1 ("AI-first, but not
   AI-only") and HITL: AI as default executor *with* human/hybrid paths first-class.
3. **Cross-domain data sync** (CRM↔HR↔Content "stay in sync") is a major **Data
   Architecture** concern — how truth stays consistent across domains without
   re-owning it.
4. **AI monitoring staff** (رصد نیروها) is a real **Security/Governance/privacy**
   concern, not just a feature — and connects to the Phase-2 "Agent & Workflow
   Monitor" surface.

## 8. Indicative mapping to the seven P7 views (a starting sketch, not the gate)
- **Logical Architecture** — the platform + mountable-modules shape; domains as
  components and their relationships.
- **Application Architecture** — the portals (client/employee/manager/admin), the
  module-mount platform, services structure.
- **Data Architecture** — persistence; the cross-domain sync model; where each
  domain's truth lives; single-tenant (no isolation layer).
- **AI Architecture** *(spine)* — the chain-modelling/router engine, admin
  model-per-part selection, agent execution, **agent/subagent identity (lands here —
  the registered deferred flag)**, human/hybrid paths.
- **Integration Architecture** — social platform APIs (IG/FB/LinkedIn), external
  services; the executed side of Phase-4 provider/channel bindings.
- **Security Architecture** — per-persona access (enforces the Phase-2 Permission
  Matrix), AI-monitoring privacy, financial-data sensitivity.
- **Runtime Architecture** — content-calendar scheduling, async/long-running content
  & AI jobs, publishing queues (Q-015), failure/recovery — everything the P6↔P7
  litmus firewalled here.

## 9. Carried open items that intersect Phase 7 (reference, don't resolve here)
- **Q-017** (admin visual workflow viewing + management) — its candidate P7 home now
  has context: AI/Runtime Architecture + module config. Marked-future; doesn't reopen
  Phase 6.
- **Agent/subagent identity** — lands in Phase 7 AI Architecture (per the registered
  flag); confirm at the gate.
- **Q-013** (AI/agent-surface home) — deferred; may surface in Phase 7.
- **Service Agreement** draft + the R-027 inherited Phase-1 questions — referenced at
  altitude, resolved by their owning phases, never here.

## 10. Candidate Phase 7 non-goals (for the gate to confirm)
- Specific technology/vendor/language/cloud selection — stays at Claude Code handoff
  (keeps the blueprint generalizable; the showcase value is the *pattern*).
- Implementation code.
- Re-deciding domain/capability/workflow truth (Phases 1/3/6).
- Phase 8 layered-assembly content (that's P8, downstream).
