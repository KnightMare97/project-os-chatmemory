# Phase 4 Extensibility Model: Brainstorm / Discovery Notes
Date: 2026-06-07 · Goal: Define Phase 4 scope — the canonical altitude of the extensibility model, the in-scope vs deferred sub-items, the locked distinction set, the closed cross-phase boundary set, and the writing constraints — before any content is written to `extensibility.md`. Scoping only.

## Status
Question-gate complete; promoted to DEC-025 (Active). Repository is source of
truth; this is a Phase 11 operating-method capture feeding the Phase 4 scope
decision. Nothing here is canon except as promoted via DEC-025 + (pending)
Snapshot-027. Per CLAUDE.md, this session did not silently finalize any boundary
or resolve any inherited Phase 1 open question. Same discipline as Phase 2
(Snapshot-013 / DEC-019) and Phase 3 (Snapshot-024 / DEC-024) scoping.

## Method
Inline grill-me question-gate, one OQ at a time. The gate plan was a prior-session
draft treated as UNVERIFIED: before use, every line-range citation was checked
against raw bytes, the 12-item sub-item list was confirmed against
`Faraz-OS-Canon.md`, and the gate was confirmed to resolve nothing (R-027) and
to operate at reference altitude only (R-028). Audit corrections were carried
into every later answer.

## Grounding already read (no need to re-ask)
- Canon phase map (`Faraz-OS-Canon.md:92-104`): Phase 4 = Extensibility Model =>
  `extensibility.md`; twelve sub-items: Permission, Extension Contracts, Plugin
  Model, Provider Model, Channel Model, Model, AI Model Routing, Runtime vs
  Config-Time Extensions, Versioning & Compatibility, External Integrations,
  Feature Modules, Future Domains.
- Extensibility Philosophy is Phase 0 canon (`Faraz-OS-Canon.md:8`); the twelve
  principles live in `extensibility-philosophy.md:1-46`. Load-bearing here:
  #2 (intentional, `:6-8`), #4 (contracts, `:13-15`), #5 (domains/capabilities/
  plugins distinct, `:17-20`), #6 (provider-agnostic, `:22-23`), #7 (routing &
  orchestration, `:25-27`), #8 (preserve governance, `:29-30`), #9
  (third-party-ready, internal-first, `:32-34`), #10 (runtime + config-time,
  `:36-38`), #11 (backward compatibility, `:40-41`), #12 (repeated extensions
  may become core, `:43-45`).
- AI Philosophy (`ai-philosophy.md`): #6 multi-model/provider-agnostic (`:18-19`),
  #7 model routing a core architectural capability (`:21-22`), #8 agent
  orchestration inside governed workflows (`:24-25`).
- Three-altitude permission separation locked at `decisions.md:394-404` (DEC-019)
  with Phase 1 evidentiary basis in `findings.md:331-335` (FIND-022); mirrored at
  `experience-architecture.md:502-541`.
- DEC-024 closed six-boundary set + operational rules (`decisions.md:679-734`)
  as the structural pattern; `capabilities.md:33-43` "referenced, not restated"
  precedent.
- Inbound demand: KNI-18 (`Snapshot-026:36`; `Snapshot-022:127-128`); the eight
  capability provider-dependency entry fields (`capabilities.md:83,106,128,150,
  166,179,199,229`); Video Creation tooling (`decisions.md:717-718`).

## Pre-gate verification (corrections carried forward)
- Three-altitude permission statement spans `decisions.md:394-404` and is owned
  by DEC-019 (not a standalone DEC); the earlier draft's `:394-401` was tightened.
- The "capability provider-dependency lines" list drops `:64` (the skeleton
  field-definition in "How to read an entry") and `:78` (Publishing's Serves-field
  channel aside) — neither is a per-entry Provider-dependency field. The eight
  entry fields are `:83,106,128,150,166,179,199,229`.
- The inherited-Phase-1 non-goal phrase is adapted from `decisions.md:734`, not a
  verbatim quote.
- All Philosophy and ai-philosophy principle line refs verified exact.

## Question-gate outcomes (OQ-E → OQ-M)
- **OQ-E — Model triad:** keep *Model* and *AI Model Routing* as TWO separate
  sub-items (faithful to canon `:98,:99`; both philosophies treat multi-model and
  routing as distinct principles). Not clustered.
- **OQ-F — Plugin / Provider / Channel:** (C) Channel Model stays first-class but
  is typed as a Provider-Model specialization reusing the provider contract;
  Plugin Model is the orthogonal packaging/attachment axis. Recorded in DEC-025
  as a scoping inference, not pre-existing canon.
- **OQ-A — in-scope core (8):** Permission, Extension Contracts, Plugin Model,
  Provider Model, Channel Model, Model, AI Model Routing, Runtime vs Config-Time.
- **OQ-B — deferred (4):** Versioning & Compatibility, External Integrations,
  Feature Modules, Future Domains. Future Domains is a marked-future placeholder,
  not silently resolvable. Eventual write is batched (à la Phase 3 A/B).
- **OQ-C — Channel Model depth:** (ii) unblock-altitude with a 4-item minimum and
  a verbatim acceptance test; deeper channel mechanics deferred. Taxonomy stays
  minimal and evidence-grounded; platforms illustrative only (`non-goals.md:9`).
- **OQ-D — Permission triad:** (C) hybrid — state Phase 4's own grant altitude,
  reference DEC-019 / FIND-022 for the full triad; do not restate.
- **OQ-G — closed boundary set:** Option 2 — definition/altitude + six cross-phase
  boundaries, P6 and P7 split; Phase 1 stays one Governance boundary (human
  identity = non-goal). Selection-vs-sequence test adopted, which consciously
  narrows `extensibility-philosophy.md:25` (orchestration → Phase 6); reconciled
  in OQ-L by harmonizing to the phase map. Agent/subagent identity registered as
  an open cross-phase flag (likely Phase 7).
- **OQ-H — grant-altitude rule:** (C) reference + may name the six Philosophy-#8
  touchpoint categories; (α) keep #8's terms verbatim, cite `:30`, with the
  provenance split (policy-enforcement `:2182`, authorization `:2183`/`:2252`/
  `:2284`, auditability `:2195` also in `domains.md`; authentication, validation,
  safety-controls #8-only). "safety controls" vs Governance's "safety
  constraints" registered as a vocabulary-alignment flag.
- **OQ-I / I' — skeleton:** six fields (Definition, Contract surface,
  Provider-agnostic note, Governance touchpoints, Runtime vs Config-Time,
  Boundary notes / inherited flags). Versioning is NOT a 7th field — "versioned
  interfaces" lives in the Contract-surface field; deep versioning is the deferred
  sub-item.
- **OQ-J — non-goals:** the DEC-024-shaped list extended with human identity
  (Phase 1 Workforce) and implementation technology (language/runtime/packaging/
  deployment, deferred to build/handoff; flagged phase-map-general).
- **OQ-K — Runtime vs Config-Time:** cross-cutting per-sub-item attribute
  (Philosophy #10), with the canon bullet as the framing section.
- **OQ-L — philosophy → canon:** (a) keep `extensibility-philosophy.md` standing,
  reference not fold (precedent: DEC-024 cites `:17`). Reconcile the #7 narrowing
  to the phase map (orchestration = Phase 6; precedence = phase map; optional
  doc annotation flagged for a later normalization pass). Fold in the
  safety-controls vocabulary flag.
- **OQ-M — inbound flags:** register KNI-18, the eight capability
  provider-dependencies, and Video Creation tooling without resolving any
  inherited Phase 1 question.

## Registered directives (carried into DEC-025)
- Implementation-technology exclusion: out of scope for architecture, deferred to
  build/handoff; flagged as likely phase-map-general (propose-only; no phase-map
  or `non-goals.md` edit made).
- Channel-Model acceptance test recorded verbatim in DEC-025.
- Repo-wide off-by-one citation drift on the inherited-question line refs
  registered as a minor normalization flag.

## Independent verification
A fresh read-only verifier checked every DEC-025 citation against raw bytes,
confirmed it resolves nothing and invents nothing, and confirmed each named list
is canon-sourced. It returned no FAILs and two discrepancies, both corrected
before promotion: (1) inherited-question line refs made byte-accurate
(`:1915-1916`, `:1917`, `:1918-1919`); (2) the Channel-Model specialization
re-marked as a DEC-025 inference. A subsequent independent byte-check caught a
transposition in the OQ-H provenance note (policy-enforcement ↔ authorization
refs), corrected to: policy-enforcement `:2182`, authorization `:2183`,
auditability `:2195`.

## Open flags (carried, not resolved)
- Agent / subagent identity (likely Phase 7 AI Architecture).
- "safety controls" (#8) vs "safety constraints" (Governance) vocabulary.
- Optional `extensibility-philosophy.md:25` annotation for the #7 orchestration
  refinement (a Phase 0 normalization edit).
- Inherited Phase 1 questions (`domains.md:1915-1916`, `:1917`, `:1918-1919`;
  Q-014) — referenced, not resolved.
- Repo-wide inherited-question citation drift — align in a later normalization
  pass.

## Not done (gated)
No `extensibility.md` content written. No commit, push, or Linear write. Snapshot-027
+ `Current-State.md` update + Linear reconciliation are a separate reviewed
close-out after the DEC-025 commit is approved and verified on origin/main.
