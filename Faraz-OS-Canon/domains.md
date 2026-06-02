# Ubiquitous Language — Draft v1

## Core Structural Terms

### Domain
A major business responsibility area of Faraz OS.
Examples:
- CRM
- Service Delivery
- Finance
- Workforce
- Knowledge
- Intelligence
- Client Success

### Subdomain
A meaningful business slice inside a Domain.
A Subdomain is narrower than a Domain but still expresses business responsibility.

### Entity
A business object with identity over time.
It may change attributes while remaining the same thing.

### Aggregate
A consistency boundary that groups one or more Entities and Value-like structures
under a single transactional and ownership boundary.

### Bounded Context
A clear modeling boundary inside which a term, object, or rule has one specific meaning.
The same real-world concept may be modeled differently in different bounded contexts.

## Execution Terms

### Capability
A reusable business function that can be used across workflows, channels, and providers.
Examples:
- Research
- Strategy
- Content Creation
- Publishing
- Reporting

### Workflow
An executable sequence of business steps that coordinates capabilities, humans, and system actions.
Examples:
- Lead → Client
- Client → Strategy
- Strategy → Production
- Production → Approval
- Approval → Publishing

## Extension Terms

### Plugin
An attachable extension that adds channel-specific, provider-specific,
or integration-specific behavior without redefining the core business model.

### Provider
A concrete external service or engine that performs a specialized function.
Examples:
- AI model provider
- video generation provider
- messaging provider
- payment provider

## Memory Terms

### Memory Object
A structured unit of retained context, knowledge, rules, preferences, or learnings
used by humans and AI across workflows.

### Shared Service
A cross-domain service used by multiple domains or workflows
without owning the business model of those domains.

## Client Context Terms

### Scope Object
The current working concept for a structured, living, executable customer-context artifact
used by workflows and AI.

It is not currently treated as a Domain.

### Client Brain
The likely future form of persistent client-level memory.
It stores durable cross-workflow and cross-service customer context.

### Engagement Scope
A service-level or project-level executable scope
used for a specific package, deliverable set, campaign, or engagement.

A Client may have one Client Brain
and multiple Engagement Scopes.

---

## Client Brain / Engagement Scope — Ownership, Field Groups, Update Authority (Draft v2)

### Current Position
The original Scope Object should be treated as a transitional concept,
not as a standalone Domain.

The preferred direction is to reinterpret it as two distinct artifacts:
- Client Brain
- Engagement Scope

This model remains draft
until relationships with CRM, Brand, Service Agreement, and Workforce
are clarified more precisely.

---

## Ownership

### Client Brain
Primary Owner:
- Client Success
- Knowledge

Primary Consumers:
- Strategy
- Service Delivery
- Intelligence
- Approval workflows
- CRM (partial)

### Engagement Scope
Primary Owner:
- Service Delivery

Primary Consumers:
- Strategy execution
- Content production
- Approval workflows
- Publishing
- Reporting

---

## Client Brain — Field Groups

### Identity
- client_id
- brand_name
- business_type
- business_summary
- active_status

### Brand Context
- brand_voice
- tone_guidelines
- style_preferences
- visual_direction_summary

### Market Context
- target_audience
- personas
- competitors
- positioning
- offers

### Commercial & Offer Context
- core_products_or_services
- offering_pricing_summary
- pricing_tiers_summary
- irresistible_offers

### Rules & Constraints
- compliance_notes
- forbidden_claims
- approval_preferences
- publishing_sensitivity
- channel_constraints

### Strategic Context
- long_term_goals
- success_criteria
- core_content_pillars
- strategic_priorities

### Relationship Memory
- important_client_preferences
- relationship_notes_relevant_to_execution
- stakeholder_map
- communication_preferences

### Performance Learnings
- historical_winning_hooks
- failed_content_patterns
- industry_specific_seasons
- seasonal_patterns

### Learnings & Decisions
- decision_summaries
- durable_learnings
- recurring_feedback_patterns
- approved_strategic_changes

### References
- active_engagement_ids
- connected_channels_metadata
- secret_references_only

---

## Engagement Scope — Field Groups

### Identity
- engagement_id
- client_id
- service_type
- package_type
- status

### Scope Definition
- deliverables_in_scope
- deliverables_out_of_scope
- start_date
- end_date
- cycle_type

### Execution Context
- active_goals
- current_priorities
- target_channels
- campaign_focus
- brief_context

### Workflow Rules
- approval_mode
- escalation_rules
- revision_policy
- publish_policy
- human_checkpoint_policy

### Constraints
- engagement_specific_constraints
- budget_or_resource_constraints_if_relevant
- timing_constraints
- sensitivity_flags

### Resourcing & Execution Mode
- assigned_human_operator_refs
- human_involvement_level
- execution_mode
- ai_agent_profile_refs

### Performance Targets
- cycle_baseline_metrics
- target_kpi_benchmarks

### Timing & Escalation
- internal_micro_deadlines
- auto_escalation_triggers

### Operational References
- client_brain_ref
- relevant_assets_refs
- relevant_briefs_refs
- related_campaign_refs

### Learning Loop
- engagement_learnings
- execution_feedback
- revision_patterns
- outcome_summary

---

## Update Authority

### Client Brain

#### Human Only
- brand identity changes
- positioning changes
- compliance-sensitive rules
- approval preference changes
- stakeholder structure changes

#### AI Propose / Human Approve
- audience refinements
- competitor summaries
- strategic learnings
- recurring pattern extraction
- tone suggestions
- pillar suggestions

#### Workflow Auto-Append
- approved learnings
- recurring feedback summaries
- decision references
- engagement outcome summaries

#### Restricted
- no direct storage of secrets
- no silent overwrite of strategic fields
- no unreviewed replacement of approved context

### Engagement Scope

#### Human Only
- final scope approval
- out-of-scope exceptions
- manual override of approval mode
- irreversible publishing policy exceptions

#### AI Propose / Human Approve
- deliverable plan suggestions
- campaign priorities
- brief refinement
- workflow optimization suggestions
- revision suggestions

#### Workflow Auto-Update
- status changes
- execution progress
- revision counts
- publish state
- feedback loop summaries
- reporting references

#### Human or Workflow
- deadlines
- task state
- operational flags
- content queue state
- approval queue state

---

## Governance Rules

### General
AI must not silently overwrite approved strategic context.

AI may:
- propose
- enrich
- summarize
- classify
- recommend

Approval-sensitive fields require human governance.

### Secrets Boundary
Credentials, tokens, API keys, certificates, and client secrets
must not be stored inside Client Brain or Engagement Scope.

These artifacts may store only:
- non-sensitive metadata
- connection status
- secret references

Sensitive credentials must be handled by a dedicated Secrets Management subsystem.

### Workforce Boundary
Engagement Scope may store references to assigned human operators,
but Workforce remains the source of truth for:
- operator identity
- availability
- capacity
- skill profile
- employment or contractor records

---

## Versioning

### Client Brain
- draft
- active
- approved
- superseded

### Engagement Scope
- draft
- approved
- active
- revised
- closed
- archived

---

## Client Brain / Engagement Scope — Domain Relationships (Draft v1)

### CRM Relationship
CRM is the likely source of truth for Client identity,
account state, and core client relationship records.

Client Brain is not the Client entity itself.
It is a persistent memory artifact about the client.

### Brand Relationship
Brand may need to be modeled as its own Entity
or a scoped child entity,
rather than only as a field inside Client Brain.

Open Question:
Should Client Brain exist per Client,
per Brand,
or support both levels?

### Service Agreement Relationship
Service Agreement is the likely business artifact
that defines what service has been agreed,
what is in scope,
and what is out of scope.

Engagement Scope should likely be derived from
or constrained by a Service Agreement,
not created independently from it.

### Workforce Relationship
Workforce remains the source of truth for:
- operator identity
- role
- availability
- capacity
- skill profile
- employment or contractor records

Engagement Scope may store only references
to assigned human operators.

### Proposed Model
- Client -> CRM
- Brand -> CRM or adjacent client context
- Service Agreement -> CRM / Client Success
- Client Brain -> Client Success + Knowledge
- Engagement Scope -> Service Delivery
- Human Operator -> Workforce

---

## CRM (Draft v1)

### Responsibilities
CRM is responsible for managing the business relationship layer
between Faraz and prospects, leads, clients, and client accounts.

It is responsible for:
- lead capture and qualification state
- client identity and account records
- contact and stakeholder records
- account lifecycle state
- commercial relationship visibility
- service agreement references
- relationship timeline visibility
- client onboarding triggers

CRM is not responsible for:
- service delivery execution
- persistent strategic memory
- content production
- workflow execution state
- workforce ownership
- financial ledger ownership

---

### What it owns
CRM owns the source of truth for:
- lead records
- client records
- contact records
- account status
- relationship stage
- client-facing stakeholder map
- service agreement references or service agreement ownership boundary (still open)
- onboarding status
- account-level metadata

CRM may reference but should not own:
- Client Brain
- Engagement Scope
- invoices and payments
- operator assignments
- raw performance analytics
- secrets and credentials

---

### Candidate Entities
- Lead
- Client
- Contact
- Stakeholder
- Brand
- Service Agreement
- Onboarding Record
- Opportunity
- Account Note

---

### Candidate Aggregates
These are candidate aggregates only
and remain subject to refinement.

#### Client Aggregate
Possible contents:
- Client
- Contacts
- Stakeholders
- Brand refs or Brand child entities
- account metadata
- onboarding status

#### Lead Aggregate
Possible contents:
- Lead
- qualification state
- source
- contact info
- opportunity linkage

#### Service Agreement Aggregate
Possible contents:
- Service Agreement
- agreed service scope summary
- package/tier
- start/end boundaries
- status
- linked client

#### Opportunity Aggregate
Possible contents:
- Opportunity
- proposed services
- commercial status
- decision stage
- linked lead or client

---

### Bounded Contexts
These are candidate bounded contexts for CRM.

#### Lead Management
Focus:
- lead capture
- lead qualification
- conversion readiness

#### Client Account Management
Focus:
- client identity
- contacts
- stakeholders
- account lifecycle
- brand/account structure

#### Commercial Agreement Management
Focus:
- service agreements
- package/tier records
- commercial scope baseline
- start/end status

#### Onboarding Coordination
Focus:
- handoff from signed client to operational setup
- onboarding readiness signals
- references to downstream domains

---

### Notes on Key Terms

#### Client
Client is likely a core CRM Entity
and may become an Aggregate Root.

#### Brand
Brand remains an open modeling question.

It may be:
- a child entity under Client
- its own entity within CRM
- or a concept partially shared with Client Brain

For now, Brand should not be assumed to be owned by Client Brain.

#### Service Agreement
Service Agreement is likely one of the most important CRM-side artifacts,
because it may define the business baseline
that later constrains Engagement Scope.

This relationship is still draft
and should be validated before lock.

#### Client Brain
Client Brain is not the CRM Client record.
It is a separate memory-centric artifact
that may reference CRM entities
but should not replace CRM ownership.

#### Engagement Scope
Engagement Scope is not owned by CRM.
CRM may reference it for relationship visibility,
but Service Delivery should remain its primary owner.

---

### Inbound events
Candidate inbound events to CRM:
- lead captured
- lead qualified
- lead disqualified
- proposal requested
- proposal accepted
- client signed
- onboarding started
- onboarding completed
- service agreement created
- service agreement updated
- service agreement renewed
- service agreement paused
- service agreement ended
- client account updated
- stakeholder updated
- brand information updated

---

### Outbound events
Candidate outbound events from CRM:
- lead qualified
- client created
- client converted from lead
- service agreement activated
- service agreement changed
- onboarding initiated
- onboarding completed
- client status changed
- stakeholder map changed
- brand context changed
- account paused
- account reactivated
- account closed

---

### Risks
- Brand boundary is not yet finalized.
- Service Agreement ownership boundary is not yet finalized.
- CRM vs Client Success ownership may still overlap in some relationship-management areas.
- CRM must not absorb Client Brain or Engagement Scope responsibilities.

---

### Open Questions
- Is Brand a child entity of Client or its own CRM entity?
- Is Service Agreement fully owned by CRM,
  or jointly constrained with Client Success?
- Should onboarding live partly in CRM
  or move into its own bounded context later?
- Which CRM fields are operationally visible to Service Delivery,
  and which remain purely commercial/relationship-facing?

  ---

  ## Service Delivery (Draft v1)

### Responsibilities
Service Delivery is responsible for planning, coordinating, executing,
tracking, and governing the delivery of agreed client services.

It is responsible for:
- engagement execution
- service scope operationalization
- deliverable planning and tracking
- production coordination
- approval coordination
- publishing handoff readiness
- execution status visibility
- revision handling
- delivery completion state
- engagement-level workflow governance

Service Delivery is not responsible for:
- client identity ownership
- commercial relationship ownership
- financial ledger ownership
- workforce identity ownership
- persistent client memory ownership
- raw analytics warehouse ownership

---

### What it owns
Service Delivery owns the source of truth for:
- Engagement Scope
- delivery status
- deliverable records
- production queue state
- revision state
- approval queue state
- execution checkpoints
- publishing readiness state
- engagement execution history
- operational handoff records

Service Delivery may reference but should not own:
- CRM Client
- Service Agreement commercial baseline
- Client Brain
- Workforce operator profiles
- channel credentials
- financial records
- raw reporting datasets

---

### Candidate Entities
- Engagement
- Engagement Scope
- Deliverable
- Deliverable Batch
- Brief
- Production Task
- Revision Request
- Approval Request
- Publishing Handoff
- Delivery Milestone
- Execution Checkpoint

---

### Candidate Aggregates
These are candidate aggregates only
and remain subject to refinement.

#### Engagement Aggregate
Possible contents:
- Engagement
- Engagement Scope
- delivery status
- milestones
- active execution policies
- linked deliverables

#### Deliverable Aggregate
Possible contents:
- Deliverable
- Brief
- production status
- revision state
- approval state
- publish readiness

#### Approval Aggregate
Possible contents:
- Approval Request
- approver references
- decision state
- feedback
- approval history

#### Revision Aggregate
Possible contents:
- Revision Request
- revision reason
- revision cycle state
- linked deliverable
- resolution state

---

### Bounded Contexts
These are candidate bounded contexts for Service Delivery.

#### Engagement Management
Focus:
- engagement lifecycle
- scope activation
- status tracking
- operational ownership

#### Production Coordination
Focus:
- briefs
- deliverables
- task orchestration
- execution state
- production readiness

#### Review & Approval Coordination
Focus:
- approvals
- revisions
- feedback loops
- human checkpoints

#### Delivery Handoff
Focus:
- publishing handoff
- completion state
- downstream readiness
- execution closure

---

### Notes on Key Terms

#### Engagement
Engagement is the operational unit of delivery
for a package, campaign, project, or recurring service cycle.

It is likely one of the most important Service Delivery entities.

#### Engagement Scope
Engagement Scope is not a CRM artifact.
It is a Service Delivery artifact
that operationalizes the agreed service into executable context.

It should be constrained by a Service Agreement,
but not replaced by it.

#### Deliverable
Deliverable should be treated as a delivery artifact,
not as a generic content object across all contexts.

A deliverable may later connect to capabilities like:
- Strategy
- Content Creation
- Video Creation
- Publishing

#### Approval
Approval is not merely a UI action.
It is a governed checkpoint artifact
that may require:
- human review
- correction
- rejection
- escalation
- override

This aligns with the Human-in-the-loop Philosophy.

#### Publishing Handoff
Publishing readiness and publishing handoff may belong here,
while final channel execution may later sit
closer to Publishing capability or plugin-layer execution.

This boundary is still draft.

---

### Inbound events
Candidate inbound events to Service Delivery:
- service agreement activated
- engagement created
- engagement scope approved
- brief created
- brief updated
- production task created
- production started
- production completed
- revision requested
- revision completed
- approval requested
- approval granted
- approval rejected
- approval overridden
- publishing requested
- publishing completed
- publishing failed
- deliverable archived
- engagement paused
- engagement resumed
- engagement closed

---

### Outbound events
Candidate outbound events from Service Delivery:
- engagement started
- engagement scope changed
- deliverable created
- deliverable ready for review
- revision cycle started
- revision cycle completed
- approval requested
- approval completed
- approval rejected
- publishing handoff ready
- delivery completed
- delivery blocked
- engagement paused
- engagement closed
- execution learning generated

---

### Risks
- Engagement vs Engagement Scope boundary is not yet fully finalized.
- Deliverable vs Brief vs Production Task boundaries may still overlap.
- Approval and Publishing boundaries may later need redistribution
  between Service Delivery, Capabilities, and Plugins.
- Service Delivery must not absorb Client Brain, CRM, or Workforce ownership.

---

### Open Questions
- Is Engagement the Aggregate Root,
  with Engagement Scope as a child artifact,
  or should Engagement Scope itself be aggregate-like?
- Should Brief belong inside the Deliverable Aggregate
  or exist as a separate artifact with its own lifecycle?
- Where is the final boundary between:
  - Service Delivery
  - Publishing capability
  - channel/plugin execution
- Should Delivery Handoff remain inside Service Delivery
  or evolve into a more explicit cross-domain coordination context?

  ---
