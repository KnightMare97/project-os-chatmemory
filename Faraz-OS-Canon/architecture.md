# Faraz OS — Puzzle Board Architecture (Phase 8)

## Purpose

`architecture.md` defines the **layered assembly** (the Puzzle Board) of Faraz OS: what
named building blocks exist and which of the seven layers each sits in. It is the Phase 8
target (`Faraz-OS-Canon.md:140`, DEC-040) — the one-way downstream from Phase 7.

This file answers boundary test item #2 (DEC-030, `decisions.md:1491-1499`): *"What
concrete building blocks exist, and which layer do they sit in — Core / Domains /
Capabilities / Plugins / Infrastructure / Experience / AI?"* → **Phase 8** (the assembled
board). It is governed by DEC-040 (scope gate G-1…G-8, commit `abcc84a`).

---

## Altitude

Phase 8 architects the layered assembly as a *logical assembly view*: block names,
source-phase provenance, and cross-layer boundary rules. It does **not** specify physical
infrastructure (Phase 9), implementation technology (Phase 10), or concern-view mechanics
(Phase 7). Block names are at layer altitude — no named framework, runtime, vendor, or
physical technology.

---

## Disambiguation

**Blueprint ≠ Board (DEC-040 G-1).**
- `system-architecture-blueprint.md` = the **Blueprint** — Phase 7's cross-cutting
  concern-view document (lenses; `Faraz-OS-Canon.md:131`).
- `architecture.md` (this file) = the **Puzzle Board** — Phase 8's layered-assembly
  document (blocks; `Faraz-OS-Canon.md:140`).
- These are not synonyms. No concern-view content from the Blueprint is reproduced
  here; no assembled-layer content from the Board belongs in the Blueprint.
- The seven Phase 7 concern-views and the seven Phase 8 layers are **not a 1:1 map**
  (DEC-030, `decisions.md:1483-1489`): P7 views are lenses; P8 layers are assembled
  groupings. No P7 view "becomes" a P8 layer.

**AI Architecture ≠ AI Layer (DEC-040 G-1, highest-collision callout).**
- Phase 7 AI Architecture (`system-architecture-blueprint.md`) answers *how the system
  executes AI* — a cross-cutting concern-view (a lens).
- Phase 8 AI Layer (this file) *assembles the named execution blocks into the board* —
  it places and names; it never re-defines or re-executes.
- This principle applies to every layer pair: the concern-view is Phase 7; the
  assembled grouping is Phase 8.

---

## Governing boundary test

DEC-030 (`decisions.md:1491-1499`), governing every Phase 8 boundary call — verbatim:

> 1. *"How does the system handle [data / execution / AI / integration / security /
>    runtime] as a cross-cutting concern?"* → **Phase 7** (a concern-view / lens).
> 2. *"What concrete building blocks exist, and which layer do they sit in — Core /
>    Domains / Capabilities / Plugins / Infrastructure / Experience / AI?"* →
>    **Phase 8** (the assembled board).
> 3. *Re-defines what a domain / capability / plugin / experience-surface **is**, who
>    owns it, or its sequence* → **neither**; that is Phases 1 / 2 / 3 / 4 / 6,
>    **referenced**.

Phase 8 NAMES and PLACES. Any re-definition refers back to the owning phase.

---

## How to read this file

Each layer entry uses the **five-field skeleton**:

1. **Definition** — what the layer IS in one sentence (an assembled grouping, not a
   concern-view).
2. **Source phases** — which phases' blocks are assembled here (referenced, never
   re-authored).
3. **Assembled blocks** — the named building blocks in this layer at layer altitude,
   each with source-phase provenance.
4. **Boundary notes** — explicit cross-phase cuts and what this layer does NOT own.
5. **Carried / deferred** — open questions and deferred items affecting this layer,
   not resolved by Phase 8.

---

## Non-goals

Per DEC-040 G-5, `architecture.md` authors **no**:
- Re-definition of what a domain, capability, plugin, or experience surface *is* —
  those are Phases 1 / 2 / 3 / 4; referenced only.
- New entity or domain — Phase 1 exclusively.
- Concern-view content — Phase 7 (`system-architecture-blueprint.md`).
- Implementation technology or physical infrastructure specifics — Phase 9 / 10.
- Workflow sequences or ordered execution patterns — Phase 6 (`workflows.md`).
- Resolution of any carried-open question (Q-004, Q-006, Q-016, Q-017, Q-020, Q-022,
  Q-024, R-027 set) — all referenced where they affect a layer, none resolved here.
- Re-authoring of Phase 6 constructs (approval gate mechanism, lifecycle state machine,
  loop / exception pattern router) as Core Layer blocks — Phase 8 references the Phase 6
  workflow runtime as a dependency; those constructs are Phase 6-owned (`workflows.md`).

---

## Core Layer

- **Definition.** The product-level building blocks that constitute what Faraz OS IS as
  a platform — the platform shell: base application, mounting and enforcement machinery,
  and cross-cutting context services. Removing any Core block changes what the platform
  fundamentally is.

- **Source phases.** Phase 7 Application Architecture + Phase 7 Security Architecture
  (`system-architecture-blueprint.md:157-159, :361-369`) + Phase 4 Extension Contracts
  (`extensibility.md:196`); assembled from multiple sources (DEC-040 G-6).

- **Assembled blocks.**

  | # | Block | Source and note |
  |---|---|---|
  | 1 | **Configurable Core Host** | P7 Application Architecture (`system-architecture-blueprint.md:157-159`): "a configurable core hosts the persona portals... and mounts Feature-Modules through the Phase-4 contract." The base application that hosts Phase-2 persona portals and mounts Feature-Modules. IS the platform product. |
  | 2 | **Feature-Module Mounting Engine** | P7 (`extensibility.md:458-459, :464-465`): "the mounting / running / composing mechanism itself is Phase 7." Runtime mechanism that mounts, runs, and composes Feature-Modules. Distinct from: the Phase-4 module contract (→ Plugins Layer) and the assembled mounted modules (→ Plugins Layer, `extensibility.md:466`). |
  | 3 | **Extension Contract Surface** | P4 Extension Contracts (`extensibility.md:196`): "the explicit, versioned boundary through which every extension — plugin, provider, channel, model — interacts with the core." Core holds the stable boundary face; Phase 4 authors the contract definition (→ Plugins Layer). |
  | 4 | **Authorization Enforcement Block** | P7 Security Architecture (`system-architecture-blueprint.md:361-363`): "the Phase-2 Permission Matrix and the Phase-1 Governance rules (DEC-026) are enforced at the application and data boundaries; Security adds no rule." Enforcement engine only — rules are Phase 1 (DEC-026) / Phase 2. |
  | 5 | **Per-Client Isolation Enforcer** | P7 Security Architecture (`system-architecture-blueprint.md:364-366`): "the Data view's per-client logical scoping is enforced as an access boundary (one client's data unreachable from another's context), within single-tenant (DEC-031 G-5)." Enforcement logic above the storage layer — the storage substrate is Infrastructure. |
  | 6 | **Credential / Secret Handling Block** | P7 Security Architecture (`system-architecture-blueprint.md:367-369`): "how credentials are scoped, held, rotated, and re-authed (including the dual-path manual re-auth) — not the crypto / implementation (Phase-10)." Credential handling logic — the secret vault it reads is Infrastructure. |
  | 7 | **Platform Context Services** | Canon-endorsed by exclusion (THREE-LENS TRIO, 2026-06-09; DEC-040 G-6): client session context, client identity context, and per-client operational context are cross-cutting Core services placed in no other layer (not a domain, not a capability, not an infrastructure substrate). No direct named canon cite; confirmed unanimous. |

- **Boundary notes.**

  *Core ↔ Infrastructure cut (governing rule):*
  > Core = product-level building blocks that constitute what Faraz OS IS as a platform
  > (the platform shell). Infrastructure = abstract substrate blocks the platform runs ON.
  > Enforcement logic sits in Core; the backing resource it enforces against sits in
  > Infrastructure.

  Governing examples:

  | Core block | Its Infrastructure counterpart |
  |---|---|
  | Authorization Enforcement Block | Auth Backing Service |
  | Per-Client Isolation Enforcer | Per-Client Data Scoping Scheme |
  | Credential / Secret Handling Block | Secret Store |

  *Phase-6-not-Core guard (explicit):* The **approval gate mechanism**, **lifecycle state
  machine**, and **loop / exception pattern router** are **Phase 6-owned constructs**
  (`Faraz-OS-Canon/workflows.md:5-6, :35, :173`). Phase 8 Core Layer references the
  Phase 6 workflow runtime as a dependency; it does not name these constructs as Core
  blocks.

  *↔ Phase 1 Governance.* Authorization rules are Phase 1 (DEC-026); the Authorization
  Enforcement Block enforces them, authors none.

  *↔ Phase 2.* The Permission Matrix is Phase 2; the Authorization Enforcement Block
  enforces it. Persona portals are Phase 2; the Configurable Core Host runs them.

  *↔ Phase 4 / Plugins Layer.* The Feature-Module contract definition is Phase 4
  (→ Plugins Layer); the Feature-Module Mounting Engine (Core) is the runtime that
  mounts modules under that contract. The Extension Contract boundary definition is
  Phase 4; the Core face of that boundary is the Extension Contract Surface block.

  *↔ Phase 7.* Core blocks are named and placed here; the concern-view mechanics
  (how the application structure runs, how security enforces, how credentials are
  managed) are Phase 7 (`system-architecture-blueprint.md`).

- **Carried / deferred.** No open questions are owned by Core directly. Referenced
  dependencies: the Phase 6 workflow runtime (approval gate, lifecycle state machine,
  loop / exception router) is a dependency of the platform — owned by Phase 6, not
  resolved here. Q-004 (Client Brain partitioning) and Q-024 (Ticket lifecycle coupling)
  affect downstream Domains Layer entries. DEC-026 (authorization rules) governs the
  Authorization Enforcement Block.

---

## Infrastructure Layer

- **Definition.** The abstract substrate building blocks the platform runs on —
  persistence, compute, queuing, auth, and secrets beneath the Core and domain blocks.
  Named at abstract altitude only; physical technology is Phase 9.

- **Source phases.** Phase 7 Data Architecture (per-client scoping and persistent data
  substrate), Phase 7 Runtime Architecture (job runtime, worker, event bus), and Phase 7
  Security Architecture (auth backing service, secret store, observability) — each
  Phase-7 view names the substrate its concern runs on; Phase 8 assembles those substrate
  references into a single Infrastructure Layer. DEC-040 G-7.

- **Assembled blocks.**

  | # | Block | Abstract definition |
  |---|---|---|
  | 1 | **Persistent Store** | Abstract durable storage substrate for domain entities and artifacts. |
  | 2 | **Job Queue / Event Bus** | Abstract queuing and event-distribution substrate for async work and domain events. |
  | 3 | **Worker / Job Runtime** | Abstract compute substrate for background and async job execution. |
  | 4 | **Auth Backing Service** | Abstract authentication and identity substrate that the Core Authorization Enforcement Block enforces over. |
  | 5 | **Secret Store** | Abstract secrets vault that the Core Credential / Secret Handling Block reads from. |
  | 6 | **Observability Infrastructure** | Abstract logging, metrics, and tracing substrate for runtime visibility. |
  | 7 | **Per-Client Data Scoping Scheme** | Data-organization layout within the Persistent Store that makes per-client logical data separation a storage-level reality — the substrate beneath the Core Per-Client Isolation Enforcer. |

  Physical technology for each block is assigned by Phase 9 Infrastructure Design
  (`infrastructure.md`). No technology name is authored here.

- **Boundary notes.**

  *P8 ↔ P9 cut (structural — must not be crossed in this file):*
  > Phase 8 Infrastructure Layer names blocks at **abstract** altitude — no named
  > technology, framework, database, or service. Phase 9 Infrastructure Design
  > (`infrastructure.md`) assigns physical technology to each abstract block.

  *↔ Core Layer.* Enforcement and handling logic sits in Core; the substrate it enforces
  against or reads from sits here. The Per-Client Isolation Enforcer (Core) enforces
  over the Per-Client Data Scoping Scheme (Infrastructure). The Credential / Secret
  Handling Block (Core) reads the Secret Store (Infrastructure). The Authorization
  Enforcement Block (Core) enforces over the Auth Backing Service (Infrastructure).
  Core blocks activate as product logic; Infrastructure blocks are the resources Core
  and domain blocks consume.

  *↔ Phase 7 (Data / Runtime / Security Architecture).* The Phase 7 concern-views
  describe *how* the system handles data, runtime, and security as cross-cutting
  concerns; they name the substrate each concern runs on. Phase 8 assembles those
  substrate references into this layer; nothing is re-authored from Phase 7.

  *↔ Phase 9.* This layer holds abstract block names only. Technology selection is Phase
  9; Phase 8 must not anticipate it.

- **Carried / deferred.** Phase 9 Infrastructure Design (`infrastructure.md`) is the
  next downstream phase for each abstract block. No open question is resolved here. The
  physical implementation of per-client data isolation (partitioning strategy) is a
  Phase 9 decision.

---

*(Batch B pending — Domains Layer, Capabilities Layer, Plugins Layer.)*
*(Batch C pending — Experience Layer, AI Layer.)*
