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

## Workforce (Draft v1)

### Responsibilities
Workforce is responsible for representing, organizing, and governing
the human contributors who participate in Faraz OS operations.

It is responsible for:
- human operator identity
- role definitions
- skill visibility
- capacity visibility
- availability visibility
- assignment eligibility
- contributor status
- human participation modes
- operator-level accountability references
- execution resource visibility

Workforce is not responsible for:
- client identity ownership
- service delivery execution ownership
- persistent client memory ownership
- commercial agreement ownership
- approval artifact ownership
- financial ledger ownership

---

### What it owns
Workforce owns the source of truth for:
- human operator records
- contributor profiles
- role assignments
- skill profiles
- availability state
- capacity state
- employment or contractor status
- operator eligibility for certain workflows or tasks
- execution participation metadata

Workforce may reference but should not own:
- Engagement Scope
- Client Brain
- CRM Client
- Service Agreement
- deliverables
- approval requests
- financial payouts or ledger records
- secrets and credentials unrelated to workforce identity/access policy

---

### Candidate Entities
- Human Operator
- Contributor
- Role
- Skill Profile
- Availability Record
- Capacity Record
- Assignment
- Team
- Contractor Profile
- Operator Status
- Participation Policy

---

### Candidate Aggregates
These are candidate aggregates only
and remain subject to refinement.

#### Human Operator Aggregate
Possible contents:
- Human Operator
- role refs
- skill profile
- availability state
- capacity state
- status
- participation eligibility

#### Assignment Aggregate
Possible contents:
- Assignment
- operator ref
- engagement ref
- role-in-engagement
- assignment status
- time window

#### Team Aggregate
Possible contents:
- Team
- member refs
- team role structure
- active participation scope

---

### Bounded Contexts
These are candidate bounded contexts for Workforce.

#### Operator Registry
Focus:
- human operator identity
- contributor records
- role membership
- status tracking

#### Skills & Capacity Management
Focus:
- skills
- availability
- capacity
- assignment readiness

#### Assignment Coordination
Focus:
- operator-to-engagement assignment references
- assignment lifecycle
- role in execution

#### Participation Governance
Focus:
- who may act in which workflows
- who may review, approve, override, or escalate
- human participation mode constraints

---

### Notes on Key Terms

#### Human Operator
Human Operator is likely the core Workforce entity.

This represents a real human contributor
who may act in execution, review, approval, escalation,
or hybrid production paths.

#### Assignment
Assignment should not be confused with full Service Delivery ownership.

Service Delivery may reference who is working on an engagement,
but Workforce should remain the source of truth
for the identity and eligibility of the assigned humans.

#### Role
Role should not be treated only as a UI permission label.

A role may influence:
- what type of work a human can perform
- what approvals they can give
- what workflows they can enter
- whether they can override or escalate

#### Participation Policy
Given the Human-in-the-loop philosophy,
it may be useful to model human participation rules
as explicit workforce-aware policy artifacts,
especially for high-risk or hybrid execution paths.

---

### Inbound events
Candidate inbound events to Workforce:
- operator created
- operator updated
- operator activated
- operator deactivated
- contractor onboarded
- role assigned
- role removed
- skill profile updated
- capacity updated
- availability updated
- assignment requested
- assignment created
- assignment changed
- assignment removed
- participation policy changed
- operator access changed

---

### Outbound events
Candidate outbound events from Workforce:
- operator available
- operator unavailable
- operator capacity changed
- operator eligible for assignment
- operator ineligible for assignment
- assignment confirmed
- assignment removed
- reviewer assigned
- approver assigned
- escalation target assigned
- workforce status changed

---

### Risks
- Workforce may overlap with Service Delivery
  if assignment ownership is not kept clear.
- Workforce may overlap with Governance
  if access control and role modeling are mixed incorrectly.
- Human role, reviewer role, approver role,
  and operator role may blur if not separated clearly.
- Capacity and assignment modeling may become too operationally heavy
  if overdesigned too early.

---

### Open Questions
- Is Assignment owned primarily by Workforce,
  or should Service Delivery own a lighter operational assignment artifact?
- How far should Workforce go into capacity planning
  versus staying a lean contributor registry?
- Should reviewer, approver, and escalation authority
  be modeled inside Workforce,
  Governance,
  or jointly across both?
- Is Team a true aggregate,
  or just a coordination view over operators?

---

## Knowledge (Draft v1)

### Responsibilities
Knowledge is responsible for capturing, structuring, storing,
retrieving, and evolving reusable organizational knowledge
for both humans and AI.

It is responsible for:
- durable knowledge storage
- client-relevant memory structures
- agency-level reusable knowledge
- decision logging
- learnings capture
- policy-adjacent knowledge references
- retrieval-ready context structuring
- knowledge version visibility
- cross-workflow memory reuse

Knowledge is not responsible for:
- CRM identity ownership
- live service execution ownership
- workforce identity ownership
- financial ledger ownership
- raw analytics interpretation ownership
- channel/plugin execution ownership

---

### What it owns
Knowledge owns the source of truth for:
- Agency Brain
- Knowledge Base
- Decision Logs
- durable learnings
- reusable playbooks or knowledge artifacts
- retrieval-oriented knowledge structures
- memory references and knowledge indexing
- approved organizational memory artifacts

Knowledge may reference but should not own:
- CRM Client identity
- Service Agreement
- Engagement Scope
- raw deliverables
- operator identity records
- financial records
- raw analytics source systems

Client Brain remains closely related to Knowledge,
but its final ownership boundary with Client Success
is still draft.

---

### Candidate Entities
- Knowledge Artifact
- Knowledge Entry
- Decision Log
- Learning Record
- Playbook
- Retrieval Context
- Memory Reference
- Agency Brain Entry
- Client Brain
- Knowledge Version

---

### Candidate Aggregates
These are candidate aggregates only
and remain subject to refinement.

#### Knowledge Artifact Aggregate
Possible contents:
- Knowledge Artifact
- content body or structured payload
- tags
- version state
- retrieval metadata
- approval state

#### Decision Log Aggregate
Possible contents:
- Decision Log
- decision summary
- rationale
- decision maker refs
- effective date
- linked domain refs

#### Learning Aggregate
Possible contents:
- Learning Record
- source context
- confidence or validation state
- reusable recommendation
- linked workflow/domain refs

#### Client Brain Aggregate or Memory Aggregate
Possible contents:
- Client Brain
- strategic context
- relationship memory
- reusable client learnings
- approved memory updates
- linked engagement refs

This remains draft
because Client Brain may stay a Memory Object
rather than becoming a full aggregate.

---

### Bounded Contexts
These are candidate bounded contexts for Knowledge.

#### Organizational Knowledge
Focus:
- agency-wide reusable knowledge
- methods
- templates
- standards
- reusable guidance

#### Decision Memory
Focus:
- decision logs
- rationale capture
- audit-friendly knowledge trails
- decision visibility over time

#### Learning Memory
Focus:
- post-execution learnings
- recurring patterns
- validated improvements
- reusable lessons

#### Client Memory
Focus:
- Client Brain
- client-specific reusable context
- durable client learnings
- client execution memory

#### Retrieval Context Management
Focus:
- indexing
- memory references
- retrieval slices
- context packaging for workflows and AI execution

---

### Notes on Key Terms

#### Knowledge Artifact
Knowledge Artifact should be treated as a reusable,
structured memory object,
not merely a document file.

It may later back:
- prompts
- workflows
- policy guidance
- strategic recommendations
- reusable agency methods

#### Decision Log
Decision Log is important because Faraz OS is human-governed
and must preserve why a decision was made,
not just the final state.

This supports auditability, learning, and future retrieval.

#### Learning Record
Learning Record should capture reusable insight
produced by execution, review, correction, and outcome analysis.

This aligns with the principle of continuous learning loops.

#### Client Brain
Client Brain is closely related to Knowledge
because it behaves like durable structured memory.

However, its ownership may still be shared
with Client Success,
so this boundary is not yet locked.

#### Agency Brain
Agency Brain is likely the reusable memory layer
for organization-wide knowledge,
distinct from client-specific memory.

---

### Inbound events
Candidate inbound events to Knowledge:
- decision made
- decision revised
- learning generated
- learning approved
- client memory updated
- engagement completed
- revision cycle completed
- approval completed
- strategy updated
- policy changed
- workflow feedback recorded
- knowledge artifact created
- knowledge artifact updated
- retrieval context requested

---

### Outbound events
Candidate outbound events from Knowledge:
- knowledge artifact created
- knowledge artifact approved
- knowledge artifact superseded
- decision logged
- learning published
- client brain updated
- agency brain updated
- retrieval context prepared
- reusable pattern detected
- memory recommendation generated

---

### Risks
- Knowledge may become an unbounded dumping ground
  if artifact types are not kept explicit.
- Knowledge may overlap with Client Success
  around Client Brain ownership.
- Knowledge may overlap with Intelligence
  if interpretive analytics and reusable knowledge are mixed.
- Retrieval structures may be overdesigned too early
  before core artifact types stabilize.

---

### Open Questions
- Is Client Brain primarily owned by Knowledge,
  Client Success,
  or jointly across both?
- Which artifact types require explicit approval
  before becoming durable reusable knowledge?
- Should Decision Log and Learning Record
  be separate aggregates,
  or just specialized Knowledge Artifact types?
- How much retrieval structure should be modeled now
  versus deferred to Phase 3 memory architecture?

---
