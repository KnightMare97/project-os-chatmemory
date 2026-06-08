# Faraz OS — Gap Analysis & Roadmap

**Status:** Analysis of `grounding/Gap-and-Enhancement-Register.md` against canon, through three senior lenses (Product, Workflow Design, System Architecture). **NOT canon.** Decides nothing; opens no gate. Concept-level only; every named technology / threshold / workflow-ID is deferred to the Build / Phase-10 layer. Canon is referenced by file + concept + open-question/DEC IDs; specific line-anchors live in the canon files and the per-lens working notes (not reproduced here, to avoid citation drift in a non-canon doc).

**Method:** each register item was read by three independent perspectives — PM (value + launch tier T1/T2/T3), Workflow Designer (process shape, dual-path, dependencies), System Architect (gap verdict: (a) covered / (b) new→gated / (c) reopens a complete phase; owning phase; inversion-guard / domain-truth flags). Their verdicts are reconciled below.

---

## 1. Executive synthesis (the headline)

**The register is overwhelmingly Phase-1 (domain truth — new entities/owners) and Phase-6 (new workflows) work — NOT Phase-7 "how" work.** This is the single most important finding, and it has a direct consequence for the current build:

- The genuinely-Phase-7 items are **few and clean**: agent supervision/observability, idempotency/duplicate-post prevention, the degraded-mode/resilience *engine*, rate-limit *mechanism*, and the *enforcement* half of security/audit/privacy-wall/retention. These are legitimate "how" and can be architected when their views come up.
- Almost everything else is a **WHAT** (a new entity nobody owns) or a **sequence** (a new workflow). Under the inversion guard (DEC-031 G-1), Phase 7 **cannot** architect storage/data/integration for these until Phase 1 owns the entity and Phase 6 owns the flow. **Architecting them in Phase 7 first would fire the guard.**
- **Q-018 is the proof and the unlock:** the Phase-7 Data Architecture view cannot draw the asset data model until a domain owns "Client Asset." Q-018 is not an isolated question — it is the first instance of a broad pattern: *the register pushes hardest on Phase 1, which is marked complete.*

**Implication for sequencing:** the natural next move after the Phase-7 views that are unblocked (Logical + AI are done; Integration/Security/Runtime are mostly clean "how") is **a controlled reopening of Phase 1** to settle the entity keystones (Section 5), then Phase 6 for the new flows (Section 6). The three lenses independently converged on this.

---

## 2. Reconciled verdicts by register section

Legend — **Tier:** T1 launch-critical / T2 post-launch / T3 later. **WF:** ✔ = a workflow (process), ◇ = not a workflow (data/policy/capability/mechanism). **Verdict:** (a) covered / (b) new→gated / (c) reopens-complete-phase. **Own:** owning phase. **⚠** = inversion-guard or P1-domain-truth flag.

### 1. Commercial & Revenue
| Item | Tier | WF | Verdict · Own · ⚠ |
|---|---|---|---|
| Billing/invoicing/payment (card-to-card→confirm→dunning) | **T1** | ✔ | (b) partial(a) · Finance entities exist; confirm-flow P6, manual path P4 |
| Pre-sales funnel (Lead→Qualify→Proposal→Contract→onboarding) | **T1** | ✔ | (c) reopens P1 + P6 · ⚠ Proposal/Contract/Service-Agreement (Q-002) |
| Service package catalog; scope-change/upsell re-price | T2 | ◇/✔ | (b) · P1 (Service Package, Amendment) + Finance · ⚠ domain-truth |

### 2. Iran / Localization / Resilience
| Item | Tier | WF | Verdict · Own · ⚠ |
|---|---|---|---|
| Card-to-card w/ operator confirmation | **T1** | ✔ | = §1 · P6+P4 |
| **Dual-path + manual fallback** (publish/upload/payment) + access-status routing | **T1** | ✔ (pattern) | (b) deep · principle=P0/P6, mechanism=P7 · ⚠ INVERSION (P7 engine, Gov authors *when*) |
| Bilingual Farsi/English (gen + UI) | **T1** | ◇ | (b) · P2 (UI) + P3 (gen attribute) |
| Data residency / legal exposure | T2 | ◇ | (b) · P1 Governance + P7 enforce · ⚠ INVERSION |
| Degraded-mode / manual continuity | T2 | ◇ | (b) · P7 Runtime + P0 principle (umbrella of dual-path) |

### 3. AI Operations — Economics & Quality
| Item | Tier | WF | Verdict · Own · ⚠ |
|---|---|---|---|
| AI cost governance + usage/cost ledger + budget caps | T2 (cap→T1.5) | ◇ | (b) · P1 ledger owner (Finance/Intelligence) + P4 cap + P7 meter · ⚠ domain-truth |
| Quality loop (QA-fail/revision → Learn→Memory) | T2 | ✔ | **(a) covered** · P6/P5 (enriches Learn→Memory Update) |
| Operator-as-bottleneck / capacity routing | T2 | ◇ | (a) mostly · P1 Workforce+Governance |
| Agent supervision / observability (kill/restart) | T2 | ✔ ctrl | (b) · **P7 AI/Runtime** (clean how) |
| Prompt/template versioning (A/B, rollback) | T3 | ◇ | (b) · P1 Knowledge (versioned entity) + P7 · ⚠ domain-truth |
| Confidence-based escalation | T2 | ✔ | **(a) covered** · Escalation Loop + Gov checkpoints |

### 4. AI Memory & Moat
| Item | Tier | WF | Verdict · Own · ⚠ |
|---|---|---|---|
| Client Brain population & freshness (seed/enrich/decay) | T2 (seed→T1.5) | ✔ | (a) mostly; **decay** = conscious P5 extension · Q-004 underneath |
| Cross-client learning + privacy wall | T3 | ◇ | (b) · P1 Gov (wall rule) + P5 + P7 enforce · ⚠ INVERSION |
| Cultural & calendar intelligence (Iranian calendar) | T2 | ◇ | (b) · P3 capability / P5 Agency Brain |

### 5. AI Trust, Safety & Accountability
| Item | Tier | WF | Verdict · Own · ⚠ |
|---|---|---|---|
| AI-incident response (detect→takedown→notice→post-mortem) | T2 | ✔ | (b) · P6 flow + P1 Gov (incident family) · ⚠ domain-truth (Incident) |
| Immutable dispute-grade approval-of-record | **T1** | ◇ | **(a) covered** (Gov Audit Aggregate) · P7 architects immutability · ⚠ INVERSION |
| Prompt-injection defense (sanitize briefs/uploads) | T2 | ◇ | (b) · P7 Security (mech) + P1 Gov (rule) |
| AI-content disclosure | T3 | ◇ | (b) · P1 Governance |

### 6. Business Self-Observation
| Item | Tier | WF | Verdict · Own · ⚠ |
|---|---|---|---|
| Agency operational analytics (profitability, cost-ratio, utilization, forecast) | T3 | ◇ | (a) capability; cost-ratio needs §3 ledger · Intelligence |
| Client churn / health prediction | T3 | ◇ | (a) covered · Intelligence + Client Success |
| Capacity/growth beyond 50-client cap | T3 | ◇ | (b) · **threshold→P10** + Intelligence |
| SLA tracking + breach handling | T3 | ✔ (breach) | (b) · P1 (SLA on Service Agreement) + P6 · ⚠ domain-truth |

### 7. Content & Creative
| Item | Tier | WF | Verdict · Own · ⚠ |
|---|---|---|---|
| Multi-platform adaptation engine | T2 | ✔ (sub-flow) | (b) · P3 capability + P4 channel attrs |
| Campaigns / content series | T2 | ✔ (orchestration) | (c) reopens P1 · ⚠ Campaign/Series entity |
| Content A/B testing | T3 | ✔ | (b) · P3/Intelligence |
| Trend & competitor intelligence | T3 | ◇ | (a) mostly · Intelligence |
| Visual consistency / brand-style enforcement | T2 | ◇ | (b) · P1 Brand (Q-003) + Gov · ⚠ domain-truth |
| Brand Kit + reusable content library | T2 | ◇ | (c) reopens P1+P5 · ⚠ Client Asset/Brand Kit/Library (Q-018) |
| **Asset rights / licensing / releases (per-asset metadata)** | T2 (decision urgent) | ◇ | **(c) reopens P1 — keystone** · **Q-018** · ⚠ Client Asset |

### 8. Engagement & Community (post-publish) — **the structural cliff**
| Item | Tier | WF | Verdict · Own · ⚠ |
|---|---|---|---|
| Community management (AI-draft replies, human-escalate, sentiment) | T2 (strongest) | ✔ (new 8th flow) | **(c) reopens P1 AND P6** · new domain/Client-Success ext + P6 flow + P4 inbound channel · ⚠ Comment/DM/Conversation/Sentiment |
| Inbound lead capture from social | T3 | ✔ | (b) · P4 inbound channel + CRM |
| Crisis / negative-sentiment detection | T3 | ✔ (trigger) | (b) · Intelligence + the new community domain · ⚠ depends §8 |

### 9. Performance Optimization Loop
| Item | Tier | WF | Verdict · Own · ⚠ |
|---|---|---|---|
| Closed-loop optimization (perf → strategy/calendar) | T3 | ✔ | (a) mostly (Learn→Memory + Intelligence→Strategy); calendar entity gap |
| Ad-spend / paid-campaign mgmt (ROAS) | T3 | ✔ | (c)/(b) new domain · P1 (Ad Account/Spend) + Finance + Intelligence · ⚠ domain-truth |
| Scheduling intelligence | T3 | ◇ | (b) · P1 (resolve scheduling ownership — open) + Intelligence · ⚠ Schedule |
| Hashtag / discoverability | T3 | ◇ | (a) covered · Strategy/Content |

### 10. Client Experience & Lifecycle
| Item | Tier | WF | Verdict · Own · ⚠ |
|---|---|---|---|
| Onboarding quality / time-to-value | **T1** (flow) | ✔ (new flow) | (b) partial(a) · P6 + Intelligence (TTV) |
| Multi-stakeholder client orgs | T2 | ◇ | (a) mostly · P1 CRM/Governance routing |
| Approval delegation & deadlines | T2 | ✔ (timeout) | (b) · P1 Gov + Workforce (Escalation Loop) |
| Self-serve client controls + ticketing | T3 | ✔ | (c) reopens P1 · ⚠ Ticket entity + P2 surface |
| Client offboarding/churn (handover/export/OAuth-revoke/retention) | T2 | ✔ (new flow) | (b) · P6 + P1 Gov (retention) + P4 (OAuth) |

### 11. Workforce & Contractors
| Item | Tier | WF | Verdict · Own · ⚠ |
|---|---|---|---|
| Contractor vetting & quality rating → assignment | T3 | ◇ | (a) mostly; rating attr new · P1 Workforce |
| Fair load-balancing | T3 | ◇ | (a) covered · P1 Workforce |
| Contractor lifecycle (source/onboard/suspend/dispute) | T3 | ✔ | (b) partial(a) · P1 Workforce + P6 |
| Payment terms / multi-currency | T2 | ◇ | (b) · P1 Finance · ⚠ Currency/FX |
| Internal roles beyond operator | T3 | ◇ | (a) covered (Workforce Role; P2 personas locked) |

### 12. Governance, Compliance & Data
| Item | Tier | WF | Verdict · Own · ⚠ |
|---|---|---|---|
| Per-client / per-industry content rules | T2 | ◇ | (a) mostly · P1 Governance (per-industry family new) |
| Consent & data-subject rights | T3 | ✔ | (b) · P1 Gov + P7 Data · ⚠ Consent record |
| Retention nuance (per-type / legal beyond 29-day) | T2 (base→T1.5) | ◇ | (b) · P1 Gov + P5 + Client Asset (Q-018) · ⚠ via Client Asset |
| Audit & traceability (system-wide) | T2 | ◇ | **(a) covered** (Gov Audit) · P7 architects mech · ⚠ INVERSION |

### 13. System / Meta
| Item | Tier | WF | Verdict · Own · ⚠ |
|---|---|---|---|
| Configuration & feature flags (config-time) | T2 (strategic) | ◇ | **(a) covered** · P4 Runtime-vs-Config-Time |
| Change management / safe rollout | T3 | ✔ ctrl | (b) · P7/P10 |
| Multi-language beyond Farsi/English | T3 | ◇ | (b) · P2/P3 (generalizes §2) |
| Notification preferences & anti-fatigue | T3 | ◇ | (b) partial(a) · P2 |

### Additional deep-layer items (round 4)
| Item | Tier | WF | Verdict · Own · ⚠ |
|---|---|---|---|
| **Platform connection health & OAuth lifecycle (+ manual re-auth)** | **T1** | ✔ (root signal) | (b) · P4 External Integrations (deferred stub) + P7 Integration |
| Security & breach response + backup/recovery | T2 (backup→T1.5) | ✔ ctrl | (b) · P7 Security/Runtime + P9 |
| Rate-limit / API-quota mgmt across clients | T2 | ◇ | (b) · P4 + **P7 Integration/Runtime** (clean how) |
| **Idempotency / duplicate-post prevention** | **T1** | ◇ | (b) · **P7 Runtime** (clean how; makes dual-path safe) |
| Per-job unit economics; multi-currency/FX; refunds/credits; contract lifecycle | T2 (e-sign→T3) | ◇/✔ | (b)/(c) · P1 Finance + Service Agreement (Q-002) · ⚠ Credit/Currency/Contract |
| Content-quality governance (fact-check/plagiarism/accessibility/voice-drift) | T3 (a11y→T2) | ◇ | (b) · P1 Gov + Intelligence; voice-drift→Brand (Q-003) |
| Intelligence & foresight (anomaly/forecast/what-if/upsell/NPS) | T3 | ◇ | (a) mostly · Intelligence |
| AI governance & self-improvement (eval/regression/override-mining/explainability/playbooks) | T3 | ◇ | (b) · P7 AI + P1 Gov + P5 · ⚠ INVERSION |

---

## 3. Tiered roadmap

### T1 — Minimal launch-critical core
The smallest set that lets the agency **take a client → produce + approve + publish → get paid → not break legally/operationally in Iran**:
1. Pre-sales → onboarding handoff (Contract triggers onboarding; basic funnel).
2. Card-to-card billing loop (issue → client pays → operator confirms → mark paid).
3. **Dual-path with manual fallback** for publish & upload + per-client/per-platform access-status routing.
4. Bilingual Farsi/English (Farsi generation + UI).
5. Approval-of-record (trustworthy who-approved-what; immutability hardens later — note system says the *requirement* is already covered by Governance Audit).
6. Basic onboarding flow (start a client; seed Client Brain).
7. Platform connection health + manual re-auth (the access-state signal everything routes on).
8. Idempotency / duplicate-post prevention (makes auto+manual safe).

**T1.5 (build alongside if cheap):** hard AI budget cap · base 29-day retention enforcement · basic action logging · data backup · Client Brain seeding at onboarding.

### T2 — Important, post-launch
Community management (the strongest T2 — the post-publish cliff) · multi-platform adaptation · Brand Kit/library · AI cost governance · quality loop · capacity routing · agent supervision · cultural/calendar intelligence · prompt-injection defense · offboarding · multi-stakeholder/delegation · per-client content rules · retention nuance · audit · feature-flags · connection lifecycle polish · rate-limits · backup/breach · refunds/credits/FX · accessibility.

### T3 — Later / scale-stage
Self-observation analytics, churn prediction, capacity planning, A/B testing, paid-media/ROAS, closed-loop optimization, scheduling/hashtag intelligence, self-serve/ticketing, contractor lifecycle/vetting, consent/data-subject, change-mgmt, multi-language, prompt versioning, foresight/anomaly, AI-governance/self-improvement, AI-content disclosure.

---

## 4. First gated decisions (ranked; reconciled across lenses)
1. **Q-018 — Client Asset ownership (P1) + un-defer Asset Intelligence (P5).** Unblocks §7 (asset rights, Brand Kit, library), §12 (retention), AND the **Phase-7 Data Architecture view** (cannot draw the asset model without an owning domain). **Take first.**
2. **Service Agreement → firm (P1; resolves Q-002, advances Q-006).** Unblocks §1 funnel/proposal/package, §6 SLA, §Additional renewals/e-sign, and the billing-confirmation flow. Most entangled existing open question.
3. **Post-publish Engagement/Community domain (P1) + its workflow (P6).** Unblocks the entire §8 cliff + §9 crisis + §3 community quality-loop. The biggest *coverage* gap — the workflow chain literally stops at "post-live."
4. **Brand placement (P1; resolves Q-003, unblocks Q-004).** Unblocks §7 visual consistency/Brand Kit, §Additional voice-drift, and finally settles Client Brain partitioning (Q-004).
5. **Dual-path / degraded-mode posture (P0 principle → P6 sequence → P7 mechanism).** The Iran reality; settle as a first-class principle (and likely a 4th workflow pattern — see §6) so it isn't re-invented per feature. ⚠ INVERSION seam: P7 architects the fallback *engine*; Governance authors *when* to fall back.
6. **AI cost-ledger ownership (P1: Finance vs Intelligence) + budget-cap-as-routing-constraint (P4).** Unblocks §3 economics, §6 cost analytics, §Additional unit economics.

*(Q-018, Q-002, Q-003/Q-004 are existing repo open questions; the dual-path and cost-ledger decisions are register-driven and not yet carrying question IDs.)*

---

## 5. Domain-truth gaps (Phase-1 keystones) — the most important output
New entities the register implies that **no domain currently owns** (candidates for a controlled Phase-1 extension), ranked by downstream unlock:
1. **Client Asset** (+ rights/licence/release/provenance/retention metadata) — today only *references* exist (`relevant_assets_refs`). **= Q-018**, + un-defer Asset Intelligence (`memory.md`). Highest leverage.
2. **Engagement/Community set: Comment, DM, Conversation, Sentiment Signal** — no domain owns post-publish inbound; the chain ends at Publishing→Reporting.
3. **Service Agreement / Contract / Proposal / Service Package** — Service Agreement is the known unresolved Business Artifact (Q-002); register adds Proposal/Package/SLA/renewal as dependents.
4. **Brand** — known open entity (Q-003, entangled with Q-004); creative items can't ground without it.
5. **Campaign / Content Series** — referenced only as Engagement-Scope fields; needs entity status.
6. **AI Usage/Cost record + Prompt/Template (versioned)** — cost-ledger owner + prompt-as-artifact unowned.
7. **Ticket** (§10), **Ad Account / Ad Spend / Budget** (§9), **Schedule/Calendar** + scheduling ownership (open), **Consent** (§12), **Currency/FX + Credit** on Finance, **Quality Rating** on Contractor, **SLA terms** on Service Agreement.

---

## 6. Phases that reopen + the proposed workflow pattern
- **Phase 1 (COMPLETE) — reopens hardest and most often.** The register is overwhelmingly a domain-truth expansion (Section 5). Each is a *what/who-owns-it* question — Phase-1's exclusive concern; none can be absorbed by Phase 7 without firing the inversion guard. This is the single biggest pressure point and the reason Q-018 surfaced.
- **Phase 6 (COMPLETE) — reopens for the post-publish cliff + new flows.** Community management (8th flow), pre-sales funnel, payment-confirmation, onboarding/offboarding, incident response are new flows beyond the seven authored; several depend on the Phase-1 entities existing first.
- **Phase 2 (COMPLETE) — reopens lightly.** Bilingual UI, self-serve client controls, notification preferences — mostly hang off the existing surface set / Channel-Behaviors framework.
- **Phases 3/4/5 (written / in-progress) — absorb extensions as designed-for growth** (P4 channel taxonomy is seed-and-grow; P5 has the Asset Intelligence un-defer slot) rather than "reopening."
- **Proposed structural addition (Workflow lens):** a **fourth cross-cutting Loop/Exception pattern — "Dual-Path / Manual-Fallback"** — alongside Escalation / Revision / Failure-Exception. The manual-fallback behavior is the same shape reused across publish, upload, payment, community, ads, takedown, and OAuth; modelling it once as a pattern (not per-flow) matches the canon's "define once, reference per flow" discipline. This would be a gated Phase-6 increment (does not reopen the seven flows).

### Workflow dependency spine (build order, from the Workflow lens)
1. Platform connection / OAuth health (+ manual re-auth) → emits per-client/per-platform access state.
2. Dual-Path / Manual-Fallback pattern (+ idempotency) → wraps Approval→Publishing and every external action.
3. Pre-sales funnel → package catalog → billing (card-to-card) → enables onboarding.
4. Onboarding (contract → OAuth setup → Client Brain seed) → feeds the existing Client→Strategy.
5. Existing production spine runs (Client→Strategy … Learn→Memory Update — already canon).
6. Closed-loop optimization wires Reporting + Learn→Memory back into Strategy (needs the full spine).
7. Engagement/Community (8th flow) attaches after Publishing→Reporting; feeds inbound-lead→pre-sales and crisis→incident.
8. Control-plane flows (incident, breach, change-mgmt, supervision) over the live system.
9. Offboarding (mirror of onboarding; OAuth revoke + retention).

---

## 7. Method note (how this feeds decisions)
1. This is grounding analysis, **not canon** — no DEC, no canon edit, no Linear, nothing decided.
2. Each gated decision above runs through its **owning phase's** normal gate (question-gate or DEC), with the two-part self-review and Ali's go — exactly as DEC-024/025/027/028/031/032 did.
3. All technology / thresholds / workflow-IDs stay earmarked for the Build / Phase-10 layer, out of the Phase 1–8 architecture.
4. The recommended immediate path: continue the Phase-7 views that are clean "how" (Integration / Security / Runtime can proceed where they don't depend on an unowned entity), and in parallel open **Q-018** (asset ownership) since it both unblocks the Phase-7 Data view and is the first instance of the Phase-1 reopening the register forces.
