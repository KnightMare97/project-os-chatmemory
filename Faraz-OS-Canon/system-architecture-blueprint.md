# System Architecture Blueprint — Phase 7

## Purpose
`system-architecture-blueprint.md` defines the **logical system architecture** of
Faraz OS as **seven cross-cutting concern-views** (Logical, Application, Data, AI,
Integration, Security, Runtime Architecture) over the platform: it names **how** the
system runs, stores, secures, integrates, and executes AI.

It **references — never re-decides** — what things are and who owns them: domain
truth and authorization (Phase 1), surfaces and the Permission Matrix (Phase 2),
capabilities (Phase 3), provider / channel / model selection and the Feature-Module
contract (Phase 4), and workflow sequences / runtime semantics (Phase 6). It is a
**concern-view** blueprint, not the layered assembly (that is Phase 8, DEC-030).

It records each concern-view on a fixed six-field skeleton.

---

## Altitude
Phase 7 sits at **system-architecture altitude** (DEC-031 G-1): it architects the
*how* — execution, storage, security, integration, AI — at logical altitude, naming
no implementation technology. This is the **R-028 inversion** from the earlier
phases: through Phase 6 the risk was engine/mechanism talk bleeding *into* logical
phases; here it flips — the risk is Phase 7 **re-deciding** domain / capability /
workflow / experience truth instead of **referencing** it. The governing
inversion-guard litmus is applied to every view (referenced below, not restated).

Faraz OS is **single-tenant**: no multi-tenant isolation layer is architected
(DEC-031 G-5).

---

## Status
Phase 7 scope is defined and human-confirmed (**DEC-031 / Snapshot-042**). The
Phase 7 ↔ Phase 8 boundary is drawn (**DEC-030**); Q-013 is resolved
(architecture-home → Phase 7 AI Architecture; surface rendering → Phase 2). The
Application / Logical view prerequisite — a firm Phase-4 Feature-Module contract — is
satisfied (**DEC-032**; `Faraz-OS-Canon/extensibility.md:426`).

This file is written in batches, dependencies-first (FIND-033), so no view's
references ever point at unwritten content. **This is Batch A — the file skeleton and
framing only; no concern-view content yet.** The seven views land in subsequent gated
batches (Logical + AI Architecture; Application + Data; Integration + Security;
Runtime + closing).

No Phase 1 domain truth, ownership, or boundary is changed by this file. Phase 7
references Phase 1; it does not reinterpret it. It resolves no inherited Phase-1
question (R-027).

---

## Governing rules (referenced, not restated here)
This file **applies** the rules fixed by **DEC-031 / DEC-030 / DEC-028**; it does not
restate them. Three governing rules bind every concern-view; each is recorded verbatim
at its cited home and applied here:

- **Inversion-guard litmus** — DEC-031 G-1 (`decisions.md:1578-1582`): the per-view
  test separating the *how* (Phase 7 architects it) from the *what* (Phases 1/2/3/6
  own it, referenced). Recorded verbatim there; applied to every view. If a view
  cannot be written without re-defining owned truth, the litmus has fired — escalate,
  do not write around it.
- **P7 ↔ P8 boundary** — DEC-030: Phase 7 is the **concern-views**; Phase 8 Puzzle
  Board is the **layered assembly**. This file authors no Phase-8 layer content.
- **P6 ↔ P7 runtime litmus** — `Faraz-OS-Canon/workflows.md:167-171` (DEC-028
  `decisions.md:1348-1353`): the engine-vs-semantics test (workflow semantics are
  Phase 6; the executing engine is Phase 7 Runtime Architecture). Recorded verbatim at
  its home; carried verbatim into the Runtime Architecture view when that batch lands.

The closed boundary set (G-2), the non-goals (G-5), and the carried set (G-7) are
fixed in DEC-031; the non-goals and carried flags are written into this file in the
closing batch.

---

## AI-native, not AI-only
**AI Architecture is the spine** of the seven views (Faraz OS is AI-native), but
AI-native is **never AI-only** (DEC-031 G-3). Every view honors **Core Principle #1**
(`Faraz-OS-Canon/principles.md:3`, "AI-first, but not AI-only") and the
human-in-the-loop mode vocabulary
(`Faraz-OS-Canon/human-in-the-loop-philosophy.md:18-22`): AI is the default executor,
with human and hybrid paths first-class, not an afterthought.

---

## How to read this file — the six-field per-view skeleton
Each of the seven concern-views is recorded on a fixed six-field skeleton
(DEC-031 G-4):

1. **Definition / concern** — what the view covers.
2. **What it architects (the *how*)** — the architectural answer to the concern.
3. **Referenced owned-truth (the *what*, by phase)** — an explicit reference list of
   the domain / surface / capability / workflow truth the view depends on, by owning
   phase; referenced, never re-decided.
4. **Key decisions / mechanisms at logical altitude** — the architectural decisions,
   stated at altitude with no named technology.
5. **Cross-phase boundary notes** — how the G-1 inversion litmus holds at each seam.
6. **Open / deferred items** — anything flagged, carried, or left to a later pass.

---

## The seven concern-views
The views below are written across the gated batches (`Faraz-OS-Canon.md:132-138`);
each follows the six-field skeleton above and is bound by the three governing rules:

- Logical Architecture
- Application Architecture
- Data Architecture
- AI Architecture *(the spine; agent / subagent identity is defined here, DEC-031 G-6(a))*
- Integration Architecture
- Security Architecture
- Runtime Architecture

---

## Logical Architecture
- **Definition / concern.** The overall logical shape of the Faraz OS platform: the
  configurable core, the mountable Feature-Modules that compose onto it, and the domains
  rendered as logical components with their relationships. It answers, at architecture
  altitude, *what the system's logical building blocks are and how they relate.*
- **What it architects (the *how*).** A **base-plus-modules** shape: a configurable core
  onto which Feature-Modules mount (the module-mounting thesis — base and modules both
  extensible and updatable). Domains appear as logical components bounded by their Phase-1
  meaning, wired by their relationships; capabilities and plugins attach through the
  Phase-4 contract surface. Described at altitude — no named framework, runtime, or
  topology.
- **Referenced owned-truth (the *what*, by phase).**
  - Phase 1 — the domain set (`Faraz-OS-Canon/domains.md`): each domain is a logical
    component here, referenced by its owned meaning, never re-defined.
  - Phase 3 — capabilities (`Faraz-OS-Canon/capabilities.md`): the reusable abilities the
    components expose; invoked, not defined.
  - Phase 4 — the Feature-Module contract (`Faraz-OS-Canon/extensibility.md:426`), the
    Plugin Model (`:273`), and Extension Contracts (`:196`): the mount / attachment
    contracts the shape composes; referenced, never re-defined.
- **Key decisions / mechanisms at logical altitude.**
  - Base + mountable modules is the platform's organizing shape; modules mount through the
    Phase-4 Feature-Module contract, and the core depends on no specific module.
  - Domains-as-components: each Phase-1 domain is one logical component; cross-domain
    relationships are wiring at altitude, not new domain truth.
  - Single-tenant: a single platform instance; no multi-tenant isolation layer
    (DEC-031 G-5). No named technology.
- **Cross-phase boundary notes (G-1 litmus).**
  - ↔ Phase 1: components *reference* domain meaning; this view re-owns no entity,
    ownership, or boundary.
  - ↔ Phase 4: the shape *mounts* the Feature-Module / plugin contract; it does not
    re-define what a module or plugin is (`Faraz-OS-Canon/extensibility.md:426`, `:273`).
  - ↔ Phase 8: the *assembled* layered board — which components / modules are assembled
    where — is Phase 8 (DEC-030); this view is the concern-view shape, not the assembly.
- **Open / deferred items.** None new. Resolves no inherited Phase-1 question (R-027).

---

## AI Architecture
- **Definition / concern.** The **spine** of the blueprint (Faraz OS is AI-native): how
  the system *executes AI* — the model-invocation / routing execution, agent and subagent
  execution and **identity**, and the human / hybrid execution paths. AI-native, **never
  AI-only**.
- **What it architects (the *how*).** A **chain-modelling / routing** execution
  architecture: the system invokes models and composes agent / subagent execution into
  chains, selecting per part by policy. **Agent / subagent identity is defined here**
  (Q-013; DEC-031 G-6(a)): what an agent / subagent *is* architecturally — a defined
  executing entity with a lifecycle-as-architecture (instantiated, executes, hands off,
  retires) — distinct from the *role* it plays in a Phase-6 sequence. AI is the default
  executor; human and hybrid paths are first-class. The engine is described at altitude —
  no named runtime, framework, model, or vendor.
- **Referenced owned-truth (the *what*, by phase).**
  - Phase 3 — capabilities (`Faraz-OS-Canon/capabilities.md:85-88`): the abilities AI and
    agents execute; invoked, not defined.
  - Phase 4 — the Model abstraction (`Faraz-OS-Canon/extensibility.md:308`) and AI Model
    Routing (`:351`): the swappable-model unit and the policy-driven selection layer. This
    view *executes* the routing engine but authors no selection policy — Phase 4 owns it
    (`:390-391`). The agent / subagent-identity flag is scoped here (`:345-347`).
  - Phase 2 — agent-facing **surface rendering** stays Phase 2 (the Q-013 split,
    DEC-031 G-6(b)).
  - Core Principle #1 (`Faraz-OS-Canon/principles.md:3`) and the HITL mode vocabulary
    (`Faraz-OS-Canon/human-in-the-loop-philosophy.md:18-22`).
- **Key decisions / mechanisms at logical altitude.**
  - Chain-modelling execution: agent / subagent steps compose into chains; per-part
    model / agent selection is enforced by *invoking* the Phase-4 routing policy, not
    re-deciding it.
  - Agent / subagent identity model: a defined executing entity (identity,
    lifecycle-as-architecture, and the AI architecture that executes it) — the Phase-7
    side of the role-vs-identity litmus.
  - Human / hybrid execution paths are first-class alternatives to AI-default execution
    (HITL), never an afterthought. No named model, runtime, or vendor; selection *policy*
    is referenced (Phase 4), not authored.
- **Cross-phase boundary notes (G-1 litmus).**
  - ↔ Phase 3: executes capabilities; defines none (`Faraz-OS-Canon/capabilities.md:85-88`).
  - ↔ Phase 4: executes the routing / selection *engine*; Phase 4 owns the routing /
    selection *policy* and the Model / Provider contracts
    (`Faraz-OS-Canon/extensibility.md:351`, `:390-391`).
  - ↔ Phase 2: defines agent / subagent *identity and executing architecture*; agent-facing
    *surface rendering* is Phase 2 (the Q-013 split, DEC-031 G-6(b)).
  - ↔ Phase 6: **role vs identity.** Phase 6 names where an agent-performed step sits in a
    sequence (its *role*); Phase 7 defines what the agent *is*. Role-vs-identity litmus
    (`Faraz-OS-Canon/workflows.md:129-133`; DEC-028 `decisions.md:1325-1332`), Phase-7
    clause verbatim: *"Defines what the agent is (identity, surface, executing AI
    architecture) → Phase 7."*
- **Open / deferred items.** Q-017 (system-administrator visual workflow management) notes
  a candidate Phase-7 home but is its own gated, multi-phase decision — carried, not
  resolved here. Resolves no inherited Phase-1 question (R-027).
