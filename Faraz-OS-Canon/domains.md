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

## CRM (Draft v2)

### Domain Position
CRM is a Domain responsible for managing relationship-facing
commercial records and pipeline visibility across the client lifecycle.

At this stage, CRM should be modeled as having two major parts:
- Lead Acquisition & Conversion
- Current Client Management

The current implementation strongly supports
Lead Acquisition & Conversion.

Current Client Management is valid as part of the CRM Domain,
but remains less mature and more draft in the current system.

---

### Responsibilities
CRM is responsible for managing the relationship and commercial-facing layer
between Faraz and prospects, leads, current clients, and client accounts.

It is responsible for:
- lead intake
- lead qualification flow
- sales pipeline stage tracking
- follow-up scheduling
- manager assignment for lead handling
- interaction and call summary tracking
- dead lead archiving and recheck flow
- commercial relationship visibility
- current client account visibility
- client status visibility
- service history visibility at CRM level
- client-facing stakeholder/contact visibility
- sales and CRM dashboard reporting

CRM is not responsible for:
- service delivery execution
- persistent strategic memory ownership
- Engagement Scope ownership
- workforce identity ownership
- financial ledger ownership
- channel credential ownership
- raw analytics warehouse ownership

---

### What it owns
CRM owns the source of truth for:
- lead records
- lead pipeline state
- lead follow-up state
- lead interaction history
- dead lead archive entries
- manager-to-lead handling visibility
- current client account records
- client contact records
- account lifecycle status
- high-level service relationship visibility
- CRM dashboard and reporting views

CRM may reference but should not own:
- Client Brain
- Engagement Scope
- workforce operator profiles
- financial contracts or ledger records
- publishing state
- knowledge artifacts
- secrets and credentials

---

### Bounded Contexts

#### Lead Acquisition & Conversion
This Bounded Context is responsible for:
- lead capture
- channel/source tracking
- qualification flow
- sales stage progression
- follow-up management
- signal-based prioritization
- manager work queue visibility
- conversion to signed client or dead lead

This is the strongest and most grounded part
of the current CRM implementation.

#### Current Client Management
This Bounded Context is responsible for:
- active client account visibility
- current client contact and stakeholder visibility
- client status tracking
- client service relationship visibility
- relationship notes at CRM level
- commercial continuity and retention visibility

This part is valid as a CRM concern,
but is still more draft and less explicit
in the current implementation.

#### Dead Lead Recovery
This Bounded Context is responsible for:
- dead lead archive management
- dead reason tracking
- recheck scheduling
- lead reactivation back into pipeline

#### CRM Reporting & Dashboarding
This Bounded Context is responsible for:
- sales summary visibility
- manager performance visibility
- service demand visibility
- active pipeline reporting
- conversion-facing dashboard views

---

### Candidate Entities

#### Lead Acquisition & Conversion
- Lead
- Lead Source
- Lead Stage
- Follow-up Schedule
- Signal
- Interaction Note
- Manager Assignment
- Dead Lead Archive Entry

#### Current Client Management
- Client Account
- Client Contact
- Stakeholder
- Client Status
- Service Relationship Record
- Account Note

#### Shared or Cross-Context Candidates
- Manager
- Service Selection
- Relationship Timeline Entry

---

### Candidate Aggregates

#### Lead Aggregate
Possible contents:
- Lead
- source
- stage
- follow-up state
- signal
- interaction summary
- assigned manager
- requested services
- notes

#### Dead Lead Aggregate
Possible contents:
- Dead Lead Archive Entry
- dead reason
- dead date
- recheck date
- previous manager ref
- reactivation state

#### Client Account Aggregate
Possible contents:
- Client Account
- contact refs
- stakeholder refs
- client status
- service relationship summary
- account notes

#### Manager Queue Projection
This is likely not an Aggregate.

It is better treated as a read model or operational projection
generated from pipeline data.

#### CRM Dashboard Projection
This is likely not an Aggregate.

It is better treated as a reporting projection
generated from CRM records.

---

### Notes on Key Terms

#### Domain
CRM is a Domain.

It should not be reduced to only a spreadsheet implementation,
even if the current operational system is built on Google Sheets
and Apps Script.

#### Bounded Context
Lead Acquisition & Conversion
and Current Client Management
should be treated as separate Bounded Contexts
inside the CRM Domain.

#### Entity
Lead is a strong candidate Entity
in the current implementation.

Client Account is also a valid candidate Entity,
but currently less evidenced in the implementation.

#### Aggregate
Lead Aggregate is the strongest candidate Aggregate
in the current CRM system.

Client Account Aggregate is a valid candidate,
but remains more draft.

#### Memory Object
Client Brain is not a CRM Entity or CRM Aggregate.

It is a separate Memory Object
that may reference CRM records
but should not replace CRM ownership.

#### Shared Service
CRM Dashboarding behaves more like a reporting view
or projection than a Shared Service.

It should not be mistaken for the CRM Domain itself.

---

### Inbound events
Candidate inbound events to CRM:
- lead captured
- lead manually created
- lead updated
- source recorded
- signal updated
- follow-up scheduled
- follow-up completed
- stage advanced
- stage reverted
- lead marked dead
- dead lead recheck triggered
- dead lead reactivated
- manager assigned
- manager changed
- client converted from lead
- current client updated
- client contact updated
- stakeholder updated
- service relationship updated

---

### Outbound events
Candidate outbound events from CRM:
- lead created
- lead qualified
- lead became overdue
- lead requires follow-up today
- lead converted to client
- lead moved to dead archive
- dead lead scheduled for recheck
- dead lead reactivated
- manager queue changed
- client account created
- client status changed
- client relationship updated
- CRM dashboard updated

---

### Risks
- If CRM is modeled only around the current implementation,
  Current Client Management may be underrepresented.
- If CRM is modeled too broadly,
  it may incorrectly absorb Client Brain responsibilities.
- Lead pipeline logic is strongly evidenced,
  but client account modeling is still structurally lighter.
- Manager queue views and dashboard views
  may be mistaken for source-of-truth aggregates
  when they are better treated as projections.

---

### Open Questions
- When a lead becomes a signed client,
  does Lead evolve into Client Account,
  or does a new Client Account Entity get created?
- How much of current client management
  should remain inside CRM
  versus move into Client Success?
- Should Service Relationship Record stay inside CRM
  as a commercial/account view,
  while Engagement Scope remains in Service Delivery?
- What is the exact boundary between:
  - CRM Client Account
  - Client Success account handling
  - Client Brain memory ownership

---

### Implementation Grounding Notes
The current operational backend strongly supports:
- pipeline stages
- follow-up dates
- manager assignment
- signal scoring
- dead lead archive
- recheck cycle
- manager tabs
- CRM dashboard reporting

The current operational backend provides weaker evidence for:
- rich client account structure
- standalone brand modeling
- explicit service agreement artifacts
- mature current-client account management structures

Therefore:
- Lead Acquisition & Conversion is implementation-grounded
- Current Client Management is architecturally valid,
  but still draft and extensible

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

## Client Success (Draft v1)

### Responsibilities
Client Success is responsible for managing the active client relationship
after commercial conversion,
with emphasis on communication,
coordination,
approval handling,
expectation management,
and continuity of service experience.

It is responsible for:
- active client relationship coordination
- client-facing communication
- expectation management
- approval request communication
- revision communication
- issue escalation intake
- service continuity visibility
- client-side coordination for operational decisions
- meeting and coordination confirmation flow
- client response tracking
- client satisfaction-related signals
- relationship-level account handling

Client Success is not responsible for:
- lead acquisition ownership
- raw sales pipeline ownership
- service execution ownership
- Engagement Scope ownership
- workforce availability ownership
- financial ledger ownership
- durable memory ownership
- policy rule ownership

---

### What it owns
Client Success owns the source of truth for:
- active client communication records
- client coordination records
- approval response records
- revision communication records
- escalation intake records
- relationship status visibility
- client-facing scheduling confirmation state
- client-side issue and concern tracking
- account handling notes at the relationship layer

Client Success may reference but should not own:
- CRM lead pipeline
- CRM client account baseline
- Client Brain
- Engagement Scope
- workforce assignments
- financial invoices or payment records
- publishing execution state
- internal delivery task state

---

### Candidate Entities
- Client Relationship
- Client Contact
- Stakeholder
- Approval Response
- Revision Communication
- Escalation Case
- Coordination Request
- Scheduling Confirmation
- Relationship Note
- Satisfaction Signal

---

### Candidate Aggregates
These are candidate aggregates only
and remain subject to refinement.

#### Client Relationship Aggregate
Possible contents:
- Client Relationship
- primary contact refs
- stakeholder refs
- relationship status
- relationship notes
- active coordination state

#### Escalation Aggregate
Possible contents:
- Escalation Case
- escalation source
- severity
- current status
- resolution summary
- linked engagement refs

#### Coordination Aggregate
Possible contents:
- Coordination Request
- request type
- client response state
- confirmation state
- linked service context
- linked scheduling context

#### Approval Response Aggregate
Possible contents:
- Approval Response
- client decision
- response timestamp
- revision or feedback notes
- linked deliverable or request ref

---

### Bounded Contexts
These are candidate bounded contexts for Client Success.

#### Relationship Management
Focus:
- active client relationship handling
- client communication continuity
- stakeholder visibility
- relationship health signals

#### Approval & Revision Coordination
Focus:
- client approvals
- rejections
- revision communication
- expectation clarification
- feedback capture

#### Client Coordination
Focus:
- meetings
- scheduling confirmations
- operational communication to clients
- response collection
- exception follow-up

#### Escalation Handling
Focus:
- complaints
- blockers
- dissatisfaction signals
- issue intake
- client-facing escalation routing

---

### Notes on Key Terms

#### Domain
Client Success is a Domain.

It should represent the relationship-management layer
for active clients,
not just a communication inbox.

#### Bounded Context
Client Coordination is especially important
because many operational workflows
still need client confirmation,
even if planning itself becomes increasingly automated.

#### Entity
Client Relationship is likely a central Entity
because the key concern here is not just a client record,
but the state of the ongoing relationship.

#### Aggregate
Client Relationship Aggregate is likely stronger
than treating every message or note
as an isolated object.

#### Memory Object
Client Brain is not owned by Client Success.

Client Success may contribute signals or updates to it,
but durable structured memory should remain separate.

#### Scheduling Confirmation
Scheduling Confirmation is not the same as scheduling ownership.

Client Success should own the client-facing confirmation state,
while actual operational scheduling logic
likely belongs elsewhere.

---

### Inbound events
Candidate inbound events to Client Success:
- client converted from lead
- client contact added
- stakeholder updated
- approval requested
- revision requested
- schedule proposal prepared
- coordination request created
- engagement delayed
- issue reported
- escalation triggered
- deliverable ready for client review
- service status changed

---

### Outbound events
Candidate outbound events from Client Success:
- client notified
- approval requested from client
- approval response received
- revision feedback captured
- schedule confirmed by client
- schedule rejected by client
- coordination pending
- escalation opened
- escalation resolved
- relationship status changed
- client success signal updated

---

### Risks
- Client Success may overlap with CRM
  if current-client account visibility is not separated
  from relationship handling.
- Client Success may overlap with Service Delivery
  if operational execution coordination is pulled too far inward.
- Client Success may overlap with Knowledge
  if communication notes and durable client memory are mixed.
- Scheduling-related coordination may become ambiguous
  unless planning,
  confirmation,
  and workforce assignment are explicitly separated.

---

### Open Questions
- What is the final boundary between:
  - CRM Current Client Management
  - Client Success Relationship Management
- Should client-facing approval handling live fully in Client Success,
  or partly in Service Delivery for certain workflows?
- Which client-facing scheduling artifacts belong here
  versus in Service Delivery?
- When a client repeatedly rejects proposed timing or deliverables,
  does that remain normal coordination,
  or become an Escalation Case?

---

### Scheduling Automation Note
A historically human planner role existed
for coordinating shoot times across many clients.

Faraz OS should aim to reduce or remove this dedicated planner role
through automation-first workflow design.

In the likely target model:
- Service Delivery prepares or requests scheduling options
- Workforce provides human availability constraints
- Client Success communicates proposed timing to the client
- the client confirms,
  rejects,
  or requests change
- the final confirmed plan is distributed downstream

This workflow should be designed
to run with minimal human intervention,
while still supporting escalation
when ambiguity,
conflict,
or high-risk coordination appears.

---

## Intelligence (Draft v1)

### Responsibilities
Intelligence is responsible for interpreting data,
detecting patterns,
generating insights,
producing recommendations,
and supporting optimization decisions
for humans and AI workflows.

It is responsible for:
- performance interpretation
- pattern detection
- recommendation generation
- optimization suggestions
- anomaly detection
- trend analysis
- comparative analysis
- scoring and prioritization logic
- decision-support outputs
- insight generation for workflows and operators

Intelligence is not responsible for:
- raw source-of-truth ownership for CRM records
- service execution ownership
- durable memory ownership
- client relationship ownership
- financial ledger ownership
- workforce identity ownership
- channel/plugin execution ownership

---

### What it owns
Intelligence owns the source of truth for:
- analytical interpretations
- derived insights
- recommendations
- scores
- prioritization outputs
- optimization suggestions
- analytical summaries
- anomaly and trend findings

Intelligence may reference but should not own:
- CRM pipeline records
- Service Delivery execution records
- Knowledge artifacts
- Client Brain
- raw analytics source systems
- workforce records
- financial records

---

### Candidate Entities
- Insight
- Recommendation
- Score
- Analytical Finding
- Trend Signal
- Anomaly Signal
- Optimization Suggestion
- Priority Model Output
- Comparative Analysis Result

---

### Candidate Aggregates
These are candidate aggregates only
and remain subject to refinement.

#### Insight Aggregate
Possible contents:
- Insight
- source refs
- interpretation summary
- confidence
- time window
- linked recommendations

#### Recommendation Aggregate
Possible contents:
- Recommendation
- target domain or workflow
- rationale
- priority
- expected impact
- acceptance state

#### Scoring Aggregate
Possible contents:
- Score
- scoring type
- input refs
- score value
- confidence
- effective date

---

### Bounded Contexts
These are candidate bounded contexts for Intelligence.

#### Performance Intelligence
Focus:
- performance interpretation
- KPI analysis
- outcome analysis
- trend summaries

#### Recommendation Engine
Focus:
- next-best-action suggestions
- optimization proposals
- prioritization outputs
- intervention recommendations

#### Scoring & Prioritization
Focus:
- lead scoring
- task prioritization
- opportunity ranking
- risk or urgency scoring

#### Anomaly & Pattern Detection
Focus:
- unusual behavior detection
- recurring pattern detection
- variance identification
- emerging signal interpretation

---

### Notes on Key Terms

#### Domain
Intelligence is a Domain.

It should represent interpretive and analytical logic,
not just a chart or dashboard.

#### Entity
Insight is a strong candidate Entity
because Intelligence should produce meaningful interpreted outputs,
not just raw numbers.

#### Aggregate
Recommendation Aggregate may become important
if recommendation lifecycle,
acceptance,
and learning feedback
need explicit modeling.

#### Bounded Context
Scoring & Prioritization is especially important
because Faraz OS already assumes decision support
and next-step guidance in multiple workflows.

#### Memory Object
Knowledge stores durable reusable memory.

Intelligence produces new interpretation from data.
These must remain separate,
even though Intelligence outputs may later be stored in Knowledge.

---

### Inbound events
Candidate inbound events to Intelligence:
- CRM data updated
- delivery outcome recorded
- engagement completed
- lead status changed
- campaign performance updated
- reporting data refreshed
- client response captured
- human correction recorded
- workflow exception logged
- learning request triggered

---

### Outbound events
Candidate outbound events from Intelligence:
- insight generated
- recommendation generated
- score updated
- priority changed
- anomaly detected
- trend identified
- optimization opportunity detected
- decision support prepared
- intelligence summary published

---

### Risks
- Intelligence may overlap with Knowledge
  if derived insight and durable memory are not separated clearly.
- Intelligence may overlap with Reporting capability
  if dashboards and interpretation are treated as the same thing.
- Intelligence may become too broad
  if every type of automation logic is pushed into it.
- Confidence and recommendation governance
  may be weak unless downstream acceptance rules are defined.

---

### Open Questions
- What belongs in Intelligence
  versus Analytics / Reporting capability?
- When does an insight become durable knowledge?
- Should lead scoring live fully inside Intelligence,
  or partly inside CRM as domain-local logic?
- Should optimization suggestions remain advisory only,
  or may some become auto-applied under policy?

---
