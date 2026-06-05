# Phase 2 Operating Surfaces: Brainstorm / Discovery Notes
Date: 2026-06-06 · Goal: Name the concrete Operating Surfaces for Phase 2 Experience Architecture, settle the discovery method and granularity rule, and produce enough scope clarity to drive a content write into `experience-architecture.md`. KNI-14 sub-item: Operating Surfaces only. Permission Matrix population deferred (Governance rules not yet concrete).

## Status
Interview in progress. Repository is source of truth; this is a Phase 11 operating-method capture feeding Phase 2 content decisions. Per CLAUDE.md, this session must not silently finalize boundaries — decisions are flagged for explicit human confirmation. Nothing here is canon until promoted via an explicit decision and snapshot.

## Grounding already read (no need to re-ask)
- Phase 2 framework in `Faraz-OS-Canon/experience-architecture.md`:
  - Operating Surface = functional workspace through which a human persona performs work; reusable across portals.
  - Portal = visual panel per persona group; contains surfaces; one definition per persona group.
  - Multi-role humans get one composed portal (union of role-scoped surfaces).
  - Persona = Phase 2 experience archetype (distinct from Workforce identity in Phase 1).
  - Locked persona set: Client (external), Contractor (external), Workforce/Operator (internal), Manager (internal), System Administrator (internal), + Future Personas.
- Governing boundary test:
  - presentation / surface / navigation → Phase 2
  - reusable functional ability → Phase 3 Capability Map
  - ordered cross-step flow + approval gates → Phase 6 Workflow Design
- Cross-Domain Views = persona-facing presentation/composition; consumes only; KPI computation = P3, dashboard surface = P2.
- Phase 3 capability set per canon: Research, Strategy, Content Creation, Video Creation, Publishing, Analytics, Reporting, Lead Scoring.
- Phase 1 domains in `domains.md`: CRM, Service Delivery, Finance, Workforce, Knowledge, Intelligence, Client Success, Governance.

## Out-of-scope for this session (locked)
- Permission Matrix population (deferred until Governance rules in `domains.md` are concrete).
- Portal contents per persona (downstream of this session).
- Cross-Domain Views by name (downstream of this session unless they fall naturally out of surface discovery).
- Channel Behaviors detail.
- Visual/brand design system, screen layout, UI components.

## Summary / key decisions (final synthesis)

**Discovery method (Q1).** Persona-driven, starting with Workforce/Operator. Reuse across other personas is then mapped; persona-distinct emerging surfaces become separate inventory entries (not specializations). Activity-driven and domain-driven approaches rejected: activity-driven risks Phase 3 drift; domain-driven would explode into one surface per domain × persona.

**Granularity rule (Q2 / Q6).** **One surface per coherent work-mode, not one per task type.** Canon-worthy; to be stated in `experience-architecture.md`.

**Naming convention (Q5).** **Persona-facing surfaces are persona-prefixed**; subject-facing surfaces use distinct subject words (e.g., "Client Brain Surface" — not "Client Context"). The word "Client" carries the persona meaning everywhere it appears as a prefix.

**Persona reuse vocabulary (Q3 / Q6).** **Full / Scoped / Distinct surface / —**. Canon-worthy; to be stated in `experience-architecture.md`. Feeds the structural shape of the Permission Matrix even though population is deferred.

**Scoped marker (Q3).** The "Scoped" marker lives in Phase 2 as a surface↔persona property. The *rules* for what is scoped come from Phase 1 Governance and are projected via the Permission Matrix (deferred this session; out of scope until Governance rules are concrete).

**Final inventory: 16 firm + 5 flagged = 21 entries.**

**Firm (16):**

| # | Surface | Primary persona | Reuse pattern |
|---|---|---|---|
| 1 | Operator Inbox | Operator | Manager Full; Client → Distinct (Client Notifications) |
| 2 | Production Workspace | Operator | Contractor Scoped (own engagement) |
| 3 | Review Queue | Operator | Manager Full; Client → Distinct (Client Approval Queue) |
| 4 | Client Brain Surface *(renamed from Client Context Surface)* | Operator | Manager Full; Contractor Scoped (assigned client). Tentative *Client Profile* for the Client persona. |
| 5 | Knowledge Workspace | Operator | Manager Full; Contractor Scoped (engagement-relevant); System Administrator → Distinct (Admin Knowledge) |
| 6 | Agent & Workflow Monitor *(renamed from Workflow Control Panel)* | Operator | Manager Full or Scoped; System Administrator Full |
| 7 | Reports & Analytics Surface *(flag: possibly Cross-Domain View)* | Operator | Manager Full; Contractor Scoped; Client Scoped |
| 8 | Lead Workspace *(new in Q6)* | Operator | Manager Full; Contractor — |
| 9 | Client Notifications | Client | — |
| 10 | Client Approval Queue | Client | — |
| 11 | Client Deliverable Library | Client | — |
| 12 | Client Billing / Invoices Surface | Client | — (Finance owns data; this is presentation) |
| 13 | Contractor Assignments | Contractor | — |
| 14 | Admin Knowledge | System Administrator | — |
| 15 | Workflow & Agent Configuration | System Administrator | — |
| 16 | Credentials & Integrations | System Administrator | References Phase 4 (provider/channel/model) and Phase 1 Governance (policy touchpoints) |

**Flagged (5):**
- *Client Profile* (Client persona) — tentative; needs later confirmation.
- *Team Performance / Oversight Surface* (Manager) — possibly a Cross-Domain View; defer.
- *System Configuration / Settings* (System Administrator) — depends on Phase 4 / Phase 9 maturity; defer.
- *Operator-finance gap* — operator's view of engagement revenue, contractor payment status, etc. Currently absorbed by Client Brain Surface / Reports & Analytics; may need its own surface later.
- *Onboarding / first-time-use surfaces* — none named for any persona; may be Phase 2 oversight or out of scope; defer.

**Non-goals / not resolved this session (locked at file top):**
- Permission Matrix population (deferred; Governance rules not concrete).
- Portal contents per persona (next sub-issue, downstream).
- Cross-Domain Views by name (next sub-session); flagged candidates from this session: Reports & Analytics, Team Performance.
- Channel Behaviors.
- Visual / brand design system, screen layout, UI components.

**Decisions implied for the canon write:**
- Update `Faraz-OS-Canon/experience-architecture.md` § Operating Surfaces from framework-only to the 16-firm-inventory framework, with the granularity rule, naming convention, and reuse vocabulary stated.
- Carry the 5 flags forward in the Open / Deferred Items section of the same file.
- Do NOT populate the Permission Matrix.
- Do NOT name Portals' contents yet.
- Do NOT enumerate Cross-Domain Views yet.

## Q&A log

### Q1 — Discovery method
- Asked: Persona-driven (starting Workforce/Operator), activity-driven, or domain-driven?
- Captured: Persona-driven, Workforce/Operator first. Rationale (confirmed by selection): internal operator likely touches the largest, most reused surface set; surfaces named from observed work tend to stay at presentation altitude (lower P3/P6 drift risk).
- Flags: none.

### Q2 — Workforce/Operator surface set + granularity assumption
- Asked: Which Operating Surfaces does Workforce/Operator need? Confirm or adjust the proposed 7-surface set; granularity assumption was "one surface per coherent work-mode, not one per task type."
- Captured: **7 operator surfaces confirmed.** Granularity assumption ratified.
  1. **Operator Inbox** — triage entry; incoming work + AI-flagged exceptions/escalations/approvals.
  2. **Production Workspace** — where the operator actively works on deliverables (content, video, strategy); composes AI-generated drafts + editing.
  3. **Review Queue** — items awaiting human review/approval before publish/send. Distinct from Inbox (pending-judgment vs pending-triage).
  4. **Client Context Surface** — pulls up a specific client's brain, history, engagement state, brand. The "what do I need to know about this client right now" workspace.
  5. **Knowledge Workspace** — internal playbooks, SOPs, agency knowledge base.
  6. **Agent & Workflow Monitor** (renamed from "Workflow Control Panel") — display + intervention surface for agent chains and workflows in progress. Display + controls are P2; the workflow logic itself is P6. The renamed name clarifies the separation from Phase 6.
  7. **Reports & Analytics Surface** — operator-relevant performance views; KPI computation lives in P3, this surface displays.
- Decisions on flagged items:
  - **Settings / Profile** is **not** an operator surface. It's System Administrator territory (admin of system-level config) or a global utility. Excluded from operator set.
  - **Agent & Workflow Monitor** name confirmed; "Control Panel" rejected for sharper P2/P6 separation.
  - **Reports & Analytics Surface** is **likely a Cross-Domain View** (composition of multi-domain info). **Flagged**, not resolved this session. Carried forward as a working entry on the operator surface list until Cross-Domain Views are scoped.
- Flags:
  - **Reports & Analytics Surface ↔ Cross-Domain View classification** — defer to the Cross-Domain Views sub-session.

### Q3 — Persona reuse map + emerging persona-distinct surfaces
- Asked: For each of the 7 operator surfaces, what is the reuse pattern across Manager / Contractor / Client / System Administrator? Ratify the reuse vocabulary (Full / Scoped / Distinct surface / —). Decide (a) where "Scoped" lives (P2 marker or Permission Matrix) and (b) whether persona-distinct surfaces become separate inventory entries or specializations.
- Captured:
  - **Reuse vocabulary confirmed:** Full / Scoped / Distinct surface / — (none).
  - **Reuse map confirmed** (with adjustments below):
    - **Operator Inbox** → Operator Full, Manager Full, Client → Distinct (*Client Notifications*).
    - **Production Workspace** → Operator Full, Contractor Scoped (own engagement).
    - **Review Queue** → Operator Full, Manager Full, Client → Distinct (*Client Approval Queue*).
    - **Client Context Surface** → Operator Full, Manager Full, Contractor Scoped (assigned client). Client themselves may have a tentative *Client Profile* surface.
    - **Knowledge Workspace** → Operator Full, Manager Full, Contractor Scoped, System Administrator → Distinct (*Admin Knowledge*). *Client Resource Hub* dropped as redundant with Client Context.
    - **Agent & Workflow Monitor** → Operator Full, Manager Full (or Scoped), System Administrator Full.
    - **Reports & Analytics Surface** → Operator Full, Manager Full, Contractor Scoped, Client Scoped. Carried with the open flag (likely Cross-Domain View).
  - **(a) Scoped placement:** Phase 2 records "Scoped" as a marker on the surface↔persona relationship. The *rules* that define what's scoped are Phase 1 Governance and are projected via the Permission Matrix (deferred this session).
  - **(b) Persona-distinct surfaces are separate Operating Surfaces**, not persona-specialized variants of a parent. Each becomes its own inventory entry. Rationale: clearer altitude, lower P3/P4 risk, easier independent authorship.
  - **Persona-distinct surfaces added to inventory:**
    - *Client Notifications* (Client persona)
    - *Client Approval Queue* (Client persona)
    - *Client Profile* (Client persona) — **tentative**, flagged for later confirmation
    - *Admin Knowledge* (System Administrator persona)
  - **Dropped:** *Client Resource Hub* (redundant with Client Context).

- **Final inventory at this checkpoint: 10 firm + 1 tentative = 11 entries.**
  - Operator: Operator Inbox, Production Workspace, Review Queue, Client Context Surface, Knowledge Workspace, Agent & Workflow Monitor, Reports & Analytics Surface (flagged: likely Cross-Domain View).
  - Client: Client Notifications, Client Approval Queue, Client Profile (tentative).
  - System Administrator: Admin Knowledge.

- Flags:
  - *Client Profile* — tentative; needs confirmation in a later session.
  - *Client Context Surface* vs *Client Notifications* / *Client Approval Queue* / *Client Profile*: the word "Client" carries two meanings in this set — **the subject the operator is looking at** (Client Context) vs **the persona doing the looking** (Client-prefixed surfaces). Naming ambiguity to surface; resolve before the canon write.
  - *Reports & Analytics Surface* still flagged for Cross-Domain Views sub-session.

### Q4 — Completeness backstop: persona-unique surfaces not yet captured
- Asked: For each persona (Client, Contractor, Manager, System Administrator), are there surfaces the operator-anchored discovery missed? Accept, drop, or flag each proposed addition.
- Captured: **5 firm additions + 2 flagged additions confirmed.**
  - **Client additions (firm):**
    - *Client Deliverable Library* — post-approval browsing / download of accepted deliverables (videos, content, reports). Distinct from Client Approval Queue (pre-approval queue vs post-approval archive).
    - *Client Billing / Invoices Surface* — Finance-domain-backed presentation; client views invoices and payment history. Finance owns the data (`domains.md`); this is the presentation only.
  - **Contractor addition (firm):**
    - *Contractor Assignments* — contractor's own assigned-work view (engagements, SOW status). Functionally distinct from Operator Inbox: contractor sees assigned work, not AI exception triage.
  - **System Administrator additions (firm):**
    - *Workflow & Agent Configuration* — authoring/configuring workflows, agent chains, gates, prompts. Distinct from Agent & Workflow Monitor (configuration vs observation).
    - *Credentials & Integrations* — managing external provider credentials, channel integrations, model routing config. References Phase 4 extensibility (provider/channel/model) and Phase 1 Governance (policy touchpoints).
  - **Manager flagged:**
    - *Team Performance / Oversight Surface* — manager-only view of team capacity, throughput, quality, escalations. **Flagged** — possibly a Cross-Domain View (parallel to Reports & Analytics Surface). Defer resolution.
  - **System Administrator flagged:**
    - *System Configuration / Settings* — global settings, feature flags, environment config. **Flagged** — may be too implementation-specific for Phase 2 to name now; depends on Phase 9 Infrastructure / Phase 4 Extensibility maturity.
  - **Meta-flag:** System Administrator surface count is growing fast (Admin Knowledge + Workflow & Agent Config + Credentials & Integrations + flagged System Config = 3 firm + 1 flagged, with full Agent & Workflow Monitor reused on top). Defensible (admin is genuinely multi-headed) but worth flagging as a **potential refactor candidate**. **Do not act on it now.**

- **Final inventory at this checkpoint: 15 firm + 3 flagged = 18 entries.**

  **Firm (15):**
  - Operator-anchored (7):
    1. Operator Inbox
    2. Production Workspace
    3. Review Queue
    4. Client Context Surface *(naming-ambiguity flag, see below)*
    5. Knowledge Workspace
    6. Agent & Workflow Monitor
    7. Reports & Analytics Surface *(classification flag: possibly Cross-Domain View)*
  - Client-persona (4):
    8. Client Notifications
    9. Client Approval Queue
    10. Client Deliverable Library
    11. Client Billing / Invoices Surface
  - Contractor-persona (1):
    12. Contractor Assignments
  - System Administrator (3):
    13. Admin Knowledge
    14. Workflow & Agent Configuration
    15. Credentials & Integrations

  **Flagged (3):**
  - *Client Profile* — tentative; needs later confirmation.
  - *Team Performance / Oversight Surface* — possibly a Cross-Domain View; defer.
  - *System Configuration / Settings* — depends on later Phase 4/9 maturity; defer.

- Flags carried forward:
  - SysAdmin refactor candidacy — informational only; no action this session.

## Open flags (pending input)

- *Reports & Analytics Surface*: Operating Surface, Cross-Domain View, or both? — owner: a later Cross-Domain Views sub-session.
- *Client Profile* surface: real or absorbed? — owner: a later persona-specific session (tentative).
- *Team Performance / Oversight Surface*: Operating Surface or Cross-Domain View? — owner: a later Cross-Domain Views sub-session.
- *System Configuration / Settings*: defer until Phase 4 / Phase 9 maturity defines its real shape — owner: a later cross-phase session.
- ~~"Client" naming ambiguity (subject vs persona) in *Client Context Surface* vs Client-persona surfaces~~ **RESOLVED in Q5** — see below.
- System Administrator surface count is growing — potential later refactor candidate; informational only.

### Q5 — Naming convention + "Client" ambiguity resolution
- Asked: Pick a naming convention (A-i / A-ii / A-iii) and a rename strategy for *Client Context Surface* (B-1 / B-2 / B-3 / B-4).
- Captured: **A-(ii) + B-(2) confirmed.**
  - **Naming convention (A-ii):** Persona-facing surfaces are prefixed with the persona name; subject-facing surfaces use distinct subject words. The 5 Client-persona surfaces (Client Notifications, Client Approval Queue, Client Deliverable Library, Client Billing / Invoices Surface, Client Profile) keep their "Client" prefix as a *persona marker*.
  - **Rename (B-2):** *Client Context Surface* → **Client Brain Surface**. The surface anchors directly on the Phase 5 Knowledge & Memory concept of Client Brain. Operators primarily access this surface to retrieve strategic client memory and context for execution — that's exactly what Client Brain is.
  - **Accepted scope narrowing:** Client Brain Surface covers **current-client** strategic memory and context. **Pre-engagement lead context** lives in CRM, not here.
- Implications:
  - The "Client" word now has a consistent meaning across surfaces: **the persona**, not the subject. Operator-facing subject surfaces use the underlying memory/domain concept (Client Brain) rather than "Client".
  - Operator surface #4 is now formally **Client Brain Surface**.
- Emerged gap:
  - The rename narrowed scope to current-client strategic memory. **Operator's view of pre-engagement leads / CRM lead context has no named surface yet.** Options: add a CRM-anchored *Lead* surface, accept that Operator Inbox handles new leads, or defer. **Carried into Q6** as a completeness item.
- Flags:
  - ~~Pre-engagement / lead-context surface gap~~ **RESOLVED in Q6** — see below.

### Q6 — Completeness backstop + formalization decisions
- Asked: (a) Resolve the lead-context gap; (b) formalize the granularity rule; (c) formalize the persona reuse vocabulary; (d) completeness backstop.
- Captured: **All four sub-asks confirmed at the recommended setting.**
  - **(a) Lead-context gap → add *Lead Workspace*** as a firm operator surface. Structurally analogous to Client Brain Surface (subject-focused operator workspace, persona = Operator, anchors on the CRM domain). Adding it prevents Operator Inbox from absorbing lead-context responsibility and confusing its triage purpose.
  - **(b) Granularity rule formalized as canon-worthy:** *Operating Surfaces are sized at one surface per coherent work-mode, not one per task type.* To be stated in the Operating Surfaces section of `experience-architecture.md`.
  - **(c) Persona reuse vocabulary formalized as canon-worthy:** Four modes — **Full** (same surface, same content), **Scoped** (same surface, restricted data), **Distinct surface** (different surface for that persona, added to inventory), **—** (no access). To be stated in the Operating Surfaces section of `experience-architecture.md`. Feeds the Permission Matrix structure (rows = personas, columns = surfaces, cells = reuse mode + scoping marker); matrix *population* remains deferred.
  - **(d) Completeness backstop:**
    - No further firm additions this session.
    - Two flags carried: **operator-finance gap** (operator may need a financial-context view; absorbed by Client Brain Surface / Reports & Analytics for now) and **onboarding gap** (no first-time-use surfaces named for any persona). Both deferred; not resolved.

(Final synthesis lives at the top of this file under "Summary / key decisions (final synthesis)".)

## Open flags (pending input)

- *Reports & Analytics Surface*: Operating Surface, Cross-Domain View, or both? — owner: a later Cross-Domain Views sub-session.
- *Client Profile* surface: real or absorbed? — owner: a later persona-specific session (tentative).
- *Team Performance / Oversight Surface*: Operating Surface or Cross-Domain View? — owner: a later Cross-Domain Views sub-session.
- *System Configuration / Settings*: defer until Phase 4 / Phase 9 maturity defines its real shape — owner: a later cross-phase session.
- *Operator-finance gap* — operator's financial-context view not surfaced; absorbed by Client Brain Surface / Reports & Analytics for now — owner: revisit when Finance domain detail matures.
- *Onboarding / first-time-use surfaces* — none named; defer — owner: a later UX-specific session.
- System Administrator surface count is growing — potential later refactor candidate; informational only.
