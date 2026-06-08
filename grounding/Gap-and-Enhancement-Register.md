# Faraz OS — Gap & Enhancement Register

**Status:** Grounding input — Ali's vision + design exploration. **NOT canon.** Concept-level only; all named technology, thresholds, and workflow IDs are deferred to the Build / handoff layer (Phase 10), never the architecture.

**Sources:** Ali's operational-map screenshots (illustrative samples, *not* hard locks) · interview answers · design rounds 1–4.

**Key decisions captured so far (Ali):**
- Payments = **card-to-card**, operator confirms receipt (manual-confirmation step; no automated gateway assumed).
- **Dual-path principle** — every external action has an automated/AI path *and* a manual/human path, with automatic fallback to manual when the automated one is unavailable (driven by the Iran platform-access reality). Applies to publish, upload, payment.
- Asset retention: **29 days default, deletable on admin/manager request.**
- **Bilingual Farsi/English**; content/script/caption generation must support Farsi.
- **IR sensitivity** as a first-class compliance dimension, not a single QA checkbox.
- All workflows to be designed from scratch in the system; the screenshots are directional only.

## 1. Commercial & Revenue
- Client billing / invoicing / payments (retainer + one-off); card-to-card → operator-confirmed → paid; unpaid → dunning.
- Pre-sales funnel: Lead → Qualify → Proposal (package + price) → Contract → triggers onboarding.
- Service package catalog; scope-change / upsell request that re-prices and amends the engagement.

## 2. Iran / Localization / Resilience
- Card-to-card payment with operator confirmation.
- Dual-path with manual fallback for publish & upload; per-client/per-platform access status as routing state.
- Bilingual Farsi/English across generation and UI; cultural fit for Farsi.
- Data residency / legal exposure flagged as governance.
- Degraded-mode / continuity — agency can run manually if the AI system is down.

## 3. AI Operations — Economics & Quality
- AI cost governance — token/model cost per job and per client, margin view, budget caps wired into AI Model Routing; an AI Usage/Cost ledger.
- Quality loop — QA-fail reasons + client revision feedback feed Learn→Memory Update so per-client memory improves each cycle.
- Operator-as-bottleneck — model operator capacity; route gates by load; AI auto-handles low-risk, humans reserved for high-risk; human-capacity view.
- Agent supervision / observability — detect looping/misbehaving agents; kill/restart/alert.
- Prompt / template versioning — version, A/B test, roll back.
- Confidence-based escalation — AI self-scores; low confidence auto-routes to a human.

## 4. AI Memory & Moat
- Client Brain population & freshness — seeded at onboarding, enriched each interaction, with decay.
- Cross-client learning with a privacy wall.
- Cultural & calendar intelligence — Iranian calendar (Nowruz, Ramadan, Yalda, national days) + platform-trend shifts.

## 5. AI Trust, Safety & Accountability
- AI-incident response — detection → takedown → client notice → post-mortem.
- Immutable, dispute-grade approval-of-record.
- Prompt-injection defense — sanitize client briefs/uploads.
- AI-content disclosure where required.

## 6. Business Self-Observation
- Agency operational analytics: per-service profitability, AI-cost-vs-human-cost ratio, contractor utilization, pipeline forecast.
- Client churn / health prediction.
- Capacity & growth planning beyond the 50-client cap.
- SLA tracking + breach handling.

## 7. Content & Creative
- Multi-platform adaptation engine.
- Campaigns / content series.
- Content A/B testing.
- Trend & competitor intelligence.
- Visual consistency / brand-style enforcement.
- Brand Kit + reusable content library.
- Asset rights / licensing / releases — provenance + usage-rights metadata per asset.

## 8. Engagement & Community (post-publish)
- Community management — comment/DM responses (AI-drafted, human-escalated), sentiment monitoring. (Map currently stops at "post live" — major gap.)
- Inbound lead capture from social.
- Crisis / negative-sentiment detection.

## 9. Performance Optimization Loop
- Closed-loop optimization — post performance feeds back into strategy and the calendar.
- Ad-spend / paid-campaign management (ROAS).
- Scheduling intelligence.
- Hashtag / discoverability strategy.

## 10. Client Experience & Lifecycle
- Onboarding quality / time-to-value.
- Multi-stakeholder client orgs — multiple contacts/roles; approval gate checks the right contact.
- Approval delegation & deadlines.
- Self-serve client controls + ticketing (route to destination + CRM notify).
- Client offboarding / churn — handover, data export, OAuth revocation, retention countdown.

## 11. Workforce & Contractors
- Contractor vetting & quality rating feeding assignment alongside skill + load.
- Fair load-balancing.
- Contractor lifecycle — sourcing, onboarding, suspension/termination, dispute resolution.
- Payment terms / multi-currency.
- Internal roles beyond operator (account managers, creative directors).

## 12. Governance, Compliance & Data
- Per-client / per-industry content rules.
- Consent & data-subject rights.
- Retention nuance — per-asset-type / legal retention beyond the 29-day default.
- Audit & traceability (system-wide).

## 13. System / Meta
- Configuration & feature flags (config-time extensibility).
- Change management / safe rollout.
- Multi-language expansion beyond Farsi/English.
- Notification preferences & anti-fatigue.

## Additional deep-layer items (round 4)
- Platform connection health & OAuth lifecycle (incl. manual re-auth for Iran).
- Security & breach response + backup & data recovery.
- Rate-limit / API-quota management across clients.
- Idempotency / duplicate-post prevention on retries.
- Per-job unit economics; multi-currency/FX; refunds/credits; contract lifecycle (renewals, e-signature).
- Content-quality governance: fact-checking, plagiarism/originality, accessibility (alt-text/captions), brand-voice drift detection.
- Intelligence & foresight: anomaly detection, demand forecasting, what-if simulation, proactive recommendations/upsell, NPS/satisfaction.
- AI governance & self-improvement: model-eval & regression governance, human-override mining, AI explainability, templates/playbooks library, OS-level self-improvement.

## How this folds into the architecture (method note)
1. This register is grounding input, not canon.
2. Each item gets a concept-level gap-analysis against canon: (a) already covered, (b) new → gated decision in its owning phase, (c) reopens a completed phase.
3. All technology/thresholds/workflow-IDs are earmarked for the Build / Phase-10 layer, kept out of the Phase 1–8 architecture.
4. The asset-ownership question (Q-018) still unblocks the Phase-7 Data Architecture view — likely the first gated decision to take.
