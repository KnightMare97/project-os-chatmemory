# Ubiquitous Language — Draft v1

## Canonical Classification Rules Draft v1

### Purpose
This section defines the working classification rules
for Phase 1 Domain Discovery.

Its purpose is to reduce:
- duplicated definitions
- inconsistent wording
- unstable concept classification
- cross-domain boundary drift

These rules are working rules for `domains.md`
and may be refined later,
but they should be treated as the default interpretation
unless a section explicitly says otherwise.

---

### Domain
A Domain is a major business responsibility area
with clear ownership boundaries.

A Domain may contain:
- Entities
- Aggregate candidates
- Bounded Contexts
- domain events
- domain-specific responsibilities

Examples in the current draft include:
- CRM
- Service Delivery
- Finance
- Workforce
- Knowledge
- Intelligence
- Client Success
- Governance

A Domain is not:
- a UI area
- a report
- a plugin
- a provider
- a workflow step
- a memory object

---

### Subdomain
A meaningful business slice inside a Domain.
A Subdomain is narrower than a Domain
but still expresses business responsibility.

---

### Bounded Context
A Bounded Context is a distinct semantic boundary
inside a Domain.

It exists when one Domain contains multiple internally coherent parts
with different language,
rules,
or model emphasis.

A Bounded Context is not automatically a separate Domain.

Examples:
- Lead Acquisition Conversion inside CRM
- Current Client Management inside CRM
- Relationship Management inside Client Success

---

### Entity
An Entity is a concept with identity continuity over time.

An Entity should be modeled as an Entity
when the identity matters more than a single snapshot of attributes.

Examples of likely Entities in the current draft include:
- Client
- Lead
- Client Account
- Client Relationship
- Human Operator
- Invoice
- Insight
- Policy

---

### Aggregate
An Aggregate is a consistency boundary
around one or more closely related Entities or value-like parts.

During Phase 1,
most Aggregates should be treated as:
- candidate aggregates
- draft consistency boundaries

Unless clearly stabilized,
the file should prefer the wording:
- Candidate Aggregate
- Aggregate candidate
rather than presenting all Aggregates as final.

---

### Memory Object
A Memory Object is a reusable context artifact
that primarily exists to preserve and supply structured memory
for humans,
AI,
or workflows.

A Memory Object is not automatically a Domain Entity
and is not automatically an Aggregate.

Current working examples:
- Client Brain
- Engagement Scope

Current working direction:
- Client Brain = Memory Object, Shared Service Artifact (owned by Knowledge — DEC-027)
- Engagement Scope = Memory Object, Domain Artifact direction

---

### Shared Service
A Shared Service is a reusable cross-domain service or artifact
that supports multiple Domains
without becoming the owner of their business responsibilities.

A Shared Service is not a Domain.

A concept should be called a Shared Service
only when it clearly serves multiple Domains
through a stable cross-domain role.

Current working example:
- Client Brain is a Shared Service Artifact owned by Knowledge (DEC-027)

---

### Business Artifact
A Business Artifact is a meaningful business object
that influences behavior,
constraints,
or agreements,
but whose final ownership or aggregate status
may still be unresolved.

Current working example:
- Service Agreement

A Business Artifact is useful when the concept is important,
but its final Domain or Aggregate placement
should remain open.

---

### Domain Artifact
A Domain Artifact is a structured artifact
strongly aligned to one Domain's operational meaning
without yet requiring final Entity or Aggregate commitment.

Current working example:
- Engagement Scope as a Service Delivery-aligned Domain Artifact

---

### Capability
A Capability is a reusable business function
that may serve multiple workflows, domains,
or channels.

A Capability is not a Domain.

Examples from Canon include:
- Research
- Strategy
- Content Creation
- Video Creation
- Publishing
- Analytics
- Reporting
- Lead Scoring

---

### Workflow
A Workflow is an executable path of work
across one or more Domains and Capabilities.

A Workflow is not a Domain
and should not be used as the owner of core business truth.

Examples from Canon include:
- Lead Client
- Client Strategy
- Strategy Production
- Production Approval
- Approval Publishing
- Publishing Reporting

---

### Plugin
A Plugin is an extension mechanism
for channels,
providers,
or specialized integrations.

A Plugin is not a Domain,
not a Capability,
and not a source of business ownership.

---

### Provider
A Provider is a swappable execution option
such as an AI model provider,
media tool,
external integration,
or payment platform.

A Provider is not a Domain.

Governance may constrain Provider usage,
but Provider concepts should remain distinct
from Domain ownership.

---

### Classification Rules
Use these default rules unless explicitly overridden:

- If the concept owns a major business responsibility,
  classify it as a Domain.
- If the concept is a semantic sub-area inside one Domain,
  classify it as a Bounded Context.
- If the concept has identity continuity,
  classify it as an Entity.
- If the concept defines a consistency boundary,
  classify it as a Candidate Aggregate unless clearly finalized.
- If the concept is reusable structured memory,
  classify it as a Memory Object.
- If the concept serves multiple Domains
  without owning their business truth,
  classify it as a Shared Service or Shared Service Artifact.
- If the concept is operationally important
  but not yet stably placed,
  classify it as a Business Artifact or Domain Artifact.
- If the concept is a reusable function across Domains,
  classify it as a Capability.
- If the concept is an execution path,
  classify it as a Workflow.
- If the concept is an extension mechanism,
  classify it as a Plugin.
- If the concept is a swappable external or internal execution option,
  classify it as a Provider.

---

### Writing Rules
To keep `domains.md` stable,
use these writing rules:

- Prefer one canonical definition per important concept.
- Prefer "Candidate Aggregate" over "Aggregate" when still draft.
- Prefer "Open Question", "Assumption", and "Risk" labels explicitly.
- Do not redefine Client Brain, Engagement Scope, or Service Agreement
  in conflicting ways across multiple sections.
- If a concept is classified centrally here,
  later sections should align with that classification
  or explicitly explain why they differ.

---

### Current Canonical Directions
The current working directions are:

- Client = Entity in CRM
- Client Account = Entity or Candidate Aggregate in CRM
- Client Relationship = Entity or Candidate Aggregate in Client Success
- Client Brain = Memory Object, Shared Service Artifact (owned by Knowledge — DEC-027)
- Engagement Scope = Memory Object, Domain Artifact direction
  aligned to Service Delivery
- Human Operator = Entity in Workforce
- Service Agreement = Business Artifact with unresolved final ownership

These directions remain draft,
but should be treated as the current baseline
for interpreting the rest of the file.

---

## Execution Terms

### Capability
See Canonical Classification Rules above.

### Workflow
See Canonical Classification Rules above.

---

## Extension Terms

### Plugin
See Canonical Classification Rules above.

### Provider
See Canonical Classification Rules above.

---

## Memory Terms

### Memory Object
See Canonical Classification Rules above.

### Shared Service
See Canonical Classification Rules above.

---

## Client Context Terms

### Scope Object
The current working concept for a structured, living,
executable customer-context artifact
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

### Ownership

#### Client Brain
Primary Owner:
- Knowledge (DEC-027)

Primary Contributor:
- Client Success

Primary Consumers:
- Strategy
- Service Delivery
- Intelligence
- Approval workflows
- CRM (partial)

#### Engagement Scope
Primary Owner:
- Service Delivery

Primary Consumers:
- Strategy execution
- Content production
- Approval workflows
- Publishing
- Reporting

---

### Client Brain — Field Groups

#### Identity
- client_id
- brand_name
- business_type
- business_summary
- active_status

#### Brand Context
- brand_voice
- tone_guidelines
- style_preferences
- visual_direction_summary

#### Market Context
- target_audience
- personas
- competitors
- positioning
- offers

#### Commercial & Offer Context
- core_products_or_services
- offering_pricing_summary
- pricing_tiers_summary
- irresistible_offers

#### Rules & Constraints
- compliance_notes
- forbidden_claims
- approval_preferences
- publishing_sensitivity
- channel_constraints

#### Strategic Context
- long_term_goals
- success_criteria
- core_content_pillars
- strategic_priorities

#### Relationship Memory
- important_client_preferences
- relationship_notes_relevant_to_execution
- stakeholder_map
- communication_preferences

#### Performance Learnings
- historical_winning_hooks
- failed_content_patterns
- industry_specific_seasons
- seasonal_patterns

#### Learnings & Decisions
- decision_summaries
- durable_learnings
- recurring_feedback_patterns
- approved_strategic_changes

#### References
- active_engagement_ids
- connected_channels_metadata
- secret_references_only

---

### Engagement Scope — Field Groups

#### Identity
- engagement_id
- client_id
- service_type
- package_type
- status

#### Scope Definition
- deliverables_in_scope
- deliverables_out_of_scope
- start_date
- end_date
- cycle_type

#### Execution Context
- active_goals
- current_priorities
- target_channels
- campaign_focus
- brief_context

#### Workflow Rules
- approval_mode
- escalation_rules
- revision_policy
- publish_policy
- human_checkpoint_policy

#### Constraints
- engagement_specific_constraints
- budget_or_resource_constraints_if_relevant
- timing_constraints
- sensitivity_flags

#### Resourcing & Execution Mode
- assigned_human_operator_refs
- human_involvement_level
- execution_mode
- ai_agent_profile_refs

#### Performance Targets
- cycle_baseline_metrics
- target_kpi_benchmarks

#### Timing & Escalation
- internal_micro_deadlines
- auto_escalation_triggers

#### Operational References
- client_brain_ref
- relevant_assets_refs
- relevant_briefs_refs
- related_campaign_refs

#### Learning Loop
- engagement_learnings
- execution_feedback
- revision_patterns
- outcome_summary

---

### Update Authority

#### Client Brain

##### Human Only
- brand identity changes
- positioning changes
- compliance-sensitive rules
- approval preference changes
- stakeholder structure changes

##### AI Propose / Human Approve
- audience refinements
- competitor summaries
- strategic learnings
- recurring pattern extraction
- tone suggestions
- pillar suggestions

##### Workflow Auto-Append
- approved learnings
- recurring feedback summaries
- decision references
- engagement outcome summaries

##### Restricted
- no direct storage of secrets
- no silent overwrite of strategic fields
- no unreviewed replacement of approved context

#### Engagement Scope

##### Human Only
- final scope approval
- out-of-scope exceptions
- manual override of approval mode
- irreversible publishing policy exceptions

##### AI Propose / Human Approve
- deliverable plan suggestions
- campaign priorities
- brief refinement
- workflow optimization suggestions
- revision suggestions

##### Workflow Auto-Update
- status changes
- execution progress
- revision counts
- publish state
- feedback loop summaries
- reporting references

##### Human or Workflow
- deadlines
- task state
- operational flags
- content queue state
- approval queue state

---

### Governance Rules

#### General
AI must not silently overwrite approved strategic context.

AI may:
- propose
- enrich
- summarize
- classify
- recommend

Approval-sensitive fields require human governance.

#### Secrets Boundary
Credentials, tokens, API keys, certificates, and client secrets
must not be stored inside Client Brain or Engagement Scope.

These artifacts may store only:
- non-sensitive metadata
- connection status
- secret references

Sensitive credentials must be handled by
a dedicated Secrets Management subsystem.

#### Workforce Boundary
Engagement Scope may store references to assigned human operators,
but Workforce remains the source of truth for:
- operator identity
- availability
- capacity
- skill profile
- employment or contractor records

---

### Versioning

#### Client Brain
- draft
- active
- approved
- superseded

#### Engagement Scope
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
- Client Brain -> Knowledge (owner; DEC-027); Client Success (contributor)
- Engagement Scope -> Service Delivery
- Human Operator -> Workforce

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

### Domain Notes
CRM is a Domain. It should not be reduced to only a spreadsheet
implementation, even if the current operational system is built
on Google Sheets and Apps Script.

Lead Acquisition & Conversion and Current Client Management
should be treated as separate Bounded Contexts inside CRM.

Lead is a strong candidate Entity in the current implementation.
Client Account is also a valid candidate Entity,
but currently less evidenced in the implementation.

Lead Aggregate is the strongest candidate Aggregate
in the current CRM system.
Client Account Aggregate is a valid candidate
but remains more draft.

Client Brain is not a CRM Entity or CRM Aggregate.
It is a separate Memory Object that may reference CRM records
but should not replace CRM ownership.

CRM Dashboarding behaves more like a reporting view or projection
than a Shared Service.
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
  - Client Brain memory (owned by Knowledge — DEC-027)

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

### Domain Notes
Human Operator is likely the core Workforce entity.
This represents a real human contributor
who may act in execution, review, approval, escalation,
or hybrid production paths.

Assignment should not be confused with full Service Delivery ownership.
Service Delivery may reference who is working on an engagement,
but Workforce should remain the source of truth
for the identity and eligibility of the assigned humans.

Role should not be treated only as a UI permission label.
A role may influence:
- what type of work a human can perform
- what approvals they can give
- what workflows they can enter
- whether they can override or escalate

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
- Client Brain (DEC-027; partitioning per Client/Brand draft — Q-004)

Knowledge may reference but should not own:
- CRM Client identity
- Service Agreement
- Engagement Scope
- raw deliverables
- operator identity records
- financial records
- raw analytics source systems

Client Brain is owned by Knowledge (DEC-027);
Client Success contributes relationship-relevant content but does not own it.
Partitioning per Client/Brand remains draft (Q-004).

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

### Domain Notes
Knowledge Artifact should be treated as a reusable structured
memory object, not merely a document file.

Decision Log is important because Faraz OS is human-governed
and must preserve why a decision was made,
not just the final state.

Learning Record should capture reusable insight
produced by execution, review, correction, and outcome analysis.

Client Brain is closely related to Knowledge
because it behaves like durable structured memory.
However, its ownership may still be shared with Client Success,
so this boundary is not yet locked.

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
  around Client Brain contribution boundaries (ownership resolved — DEC-027).
- Knowledge may overlap with Intelligence
  if interpretive analytics and reusable knowledge are mixed.
- Retrieval structures may be overdesigned too early
  before core artifact types stabilize.

---

### Open Questions
- Resolved (DEC-027): Client Brain is owned by Knowledge; Client Success
  contributes but does not own. (Partitioning per Client/Brand remains open — Q-004.)
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

### Domain Notes
Client Success is a Domain.
It should represent the relationship-management layer
for active clients, not just a communication inbox.

Client Coordination is especially important
because many operational workflows still need client confirmation,
even if planning itself becomes increasingly automated.

Client Relationship is likely a central Entity
because the key concern here is not just a client record,
but the state of the ongoing relationship.

Client Relationship Aggregate is likely stronger
than treating every message or note as an isolated object.

Client Brain is not owned by Client Success.
Client Success may contribute signals or updates to it,
but durable structured memory should remain separate.

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

### Domain Notes
Intelligence is a Domain.
It should represent interpretive and analytical logic,
not just a chart or dashboard.

Insight is a strong candidate Entity
because Intelligence should produce meaningful interpreted outputs,
not just raw numbers.

Recommendation Aggregate may become important
if recommendation lifecycle, acceptance,
and learning feedback need explicit modeling.

Scoring & Prioritization is especially important
because Faraz OS already assumes decision support
and next-step guidance in multiple workflows.

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

## Finance (Draft v1)

### Responsibilities
Finance is responsible for managing the monetary layer
of commercial and operational activity in Faraz OS.

It is responsible for:
- financial obligation tracking
- invoice management
- payment tracking
- receivable visibility
- payable visibility
- settlement state visibility
- financial status reporting
- due date tracking
- collection coordination state
- refund or adjustment tracking
- finance-facing transaction records
- account balance visibility where applicable

Finance is not responsible for:
- lead acquisition ownership
- client relationship ownership
- service execution ownership
- Engagement Scope ownership
- workforce identity ownership
- approval workflow ownership
- policy rule ownership
- durable knowledge ownership

---

### What it owns
Finance owns the source of truth for:
- invoices
- payment records
- receivables
- payables
- settlement records
- refund records
- adjustment records
- financial due dates
- payment status
- collection status
- finance ledger-facing summaries

Finance may reference but should not own:
- CRM client account records
- Service Agreement commercial context
- Service Delivery execution state
- Workforce contributor records
- Client Brain
- Knowledge artifacts
- raw bank/provider infrastructure details outside domain contracts

---

### Candidate Entities
- Invoice
- Payment
- Receivable
- Payable
- Settlement
- Refund
- Adjustment
- Billing Account
- Financial Obligation
- Collection Case

---

### Candidate Aggregates

#### Invoice Aggregate
Possible contents:
- Invoice
- billed party ref
- amount
- due date
- line items or charge summary
- payment status
- linked payment refs

#### Payment Aggregate
Possible contents:
- Payment
- payment source
- amount
- received date
- allocation state
- settlement status

#### Collection Aggregate
Possible contents:
- Collection Case
- outstanding obligation refs
- collection state
- reminder history
- escalation state

#### Billing Account Aggregate
Possible contents:
- Billing Account
- client or counterparty ref
- open balances
- invoice refs
- payment refs
- adjustment refs

---

### Bounded Contexts

#### Billing
Focus:
- invoice creation
- charge visibility
- due dates
- billing state

#### Receivables Management
Focus:
- incoming payments
- unpaid invoices
- collection tracking
- settlement visibility

#### Payables Management
Focus:
- outgoing obligations
- supplier or contractor payments
- payment due tracking

#### Financial Adjustments
Focus:
- refunds
- corrections
- adjustments
- exceptional financial changes

---

### Domain Notes
Finance is a Domain.
It should own the monetary truth of the system,
not just a reporting view.

Invoice is likely one of the central Finance entities,
because many downstream payment and collection states
depend on it.

Invoice Aggregate and Payment Aggregate
are likely stronger candidates
than modeling each status change independently.

Receivables Management is especially important
because payment visibility, follow-up, and settlement state
are operationally significant.

External payment gateways, banks, and accounting tools
should be treated as providers or integrations,
not as the Finance Domain itself.

---

### Inbound events
Candidate inbound events to Finance:
- client converted
- service agreement activated
- invoice requested
- invoice revised
- payment received
- payment failed
- payment confirmed
- refund requested
- refund approved
- payable created
- contractor payout requested
- adjustment requested
- billing cycle started

---

### Outbound events
Candidate outbound events from Finance:
- invoice created
- invoice issued
- invoice overdue
- payment recorded
- payment allocated
- payment failed
- receivable settled
- payable due
- payable settled
- refund issued
- adjustment applied
- collection case opened
- financial status changed

---

### Risks
- Finance may overlap with CRM
  if commercial relationship data
  and financial obligation data are not separated clearly.
- Finance may overlap with Governance
  if approval policy and financial record ownership are mixed.
- Finance may overlap with Workforce
  if contractor payout logic and contributor identity logic are not separated.
- Billing may be modeled too early
  without a finalized Service Agreement boundary.

---

### Open Questions
- Is Service Agreement owned outside Finance,
  with Finance only referencing it,
  or does Finance own some financial sub-artifacts of it?
- Should contractor payouts live fully inside Finance,
  or partly in Workforce with Finance as settlement owner?
- What is the final boundary between:
  - invoice
  - commercial proposal
  - service agreement
- How much accounting detail belongs inside Finance
  versus external accounting providers or tools?

---

## Governance Draft v1

### Domain Position
Governance is a Domain responsible for defining, evaluating,
enforcing, and auditing the control layer of Faraz OS
across workflows, domains, capabilities, plugins, providers,
models, agents, and externally visible actions.

Governance exists because Faraz OS is explicitly:
- AI-first, but not AI-only
- human-governed
- risk-tiered
- event-driven
- provider-agnostic
- plugin-ready
- policy-governed for AI autonomy and external execution

Governance should therefore be modeled as a real Domain,
not as a thin middleware concern,
not as a UI permission table,
and not as an infrastructure-only subsystem.

---

### Responsibilities
Governance is responsible for:
- policy definition
- policy evaluation
- policy enforcement
- permission and authorization rules
- risk-tiered control rules
- human checkpoint rules
- approval requirement rules
- escalation rules
- override rules
- safety constraints
- externally visible action control
- irreversible action control
- provider and model usage constraints
- routing guardrails at policy level
- extension and plugin compliance control
- auditability requirements
- traceability requirements
- exception handling at governance level

Governance is not responsible for:
- CRM relationship ownership
- Service Delivery execution ownership
- Finance record ownership
- Workforce identity ownership
- Knowledge ownership
- Intelligence ownership
- Client Success ownership
- plugin implementation ownership
- provider implementation ownership
- secrets storage implementation ownership
- general workflow business data ownership

---

### What it owns
Governance owns the source of truth for:
- governance policies
- permission rules
- authorization rules
- action eligibility rules
- risk classification rules
- checkpoint definitions
- approval requirement definitions
- escalation definitions
- override definitions
- exception definitions
- safety rules
- audit requirements
- traceability requirements
- policy-level routing constraints
- extension compliance rules
- execution control decisions at governance level

Governance may reference but should not own:
- CRM Client records
- lead records
- Service Delivery execution records
- Engagement Scope
- Workforce Human Operator records
- Finance invoices and payments
- Knowledge artifacts
- Client Brain
- provider internals
- plugin internals
- raw execution telemetry unless needed for governance decisions
- secret values

---

### Candidate Entities
- Policy
- Permission Rule
- Authorization Rule
- Authorization Decision
- Action Eligibility Rule
- Risk Rule
- Checkpoint Definition
- Approval Requirement
- Escalation Rule
- Override Rule
- Override Record
- Exception Case
- Safety Constraint
- Audit Rule
- Audit Record
- Routing Constraint
- Extension Compliance Record

---

### Candidate Aggregates

#### Policy Aggregate
Possible contents:
- Policy
- policy type
- scope
- conditions
- enforcement mode
- status
- version
- linked rules
- exception references

#### Authorization Aggregate
*Accepted slice (DEC-026): the authorization rules realizing this aggregate for persona↔surface exposure are concrete in "Authorization (accepted slice — DEC-026)" below; the rest of this aggregate stays Draft v1.*
Possible contents:
- Authorization Rule
- subject type
- action type
- resource scope
- conditions
- allowed or denied outcome
- validity window
- linked policy refs

#### Checkpoint Aggregate
Possible contents:
- Checkpoint Definition
- trigger conditions
- risk basis
- required human action
- required actor type
- escalation path
- evidence requirements

#### Exception Aggregate
Possible contents:
- Exception Case
- triggering rule refs
- requested action
- current state
- escalation state
- override state
- resolution summary

#### Audit Aggregate
Possible contents:
- Audit Record
- actor ref
- action ref
- proposed action summary
- approved action summary
- executed action summary
- timestamps
- trace refs
- changed by human evidence

#### Routing Governance Aggregate
Possible contents:
- Routing Constraint
- task type
- allowed models or providers
- blocked models or providers
- risk tier
- cost or quality constraints
- fallback policy refs

---

### Bounded Contexts

#### Policy Management
This Bounded Context is responsible for:
- policy authoring
- policy lifecycle
- policy versioning
- policy status management
- policy scope definition
- applicability conditions
- enforcement mode definition

#### Access and Authorization Control
*Accepted slice (DEC-026): persona↔surface authorization is concrete in "Authorization (accepted slice — DEC-026)" below; the rest of this bounded context stays Draft v1.*
This Bounded Context is responsible for:
- who may do what
- human permissions
- agent permissions
- workflow action permissions
- plugin action permissions
- provider usage permissions
- authorization decisions
- action eligibility control

#### Risk and Checkpoint Orchestration
This Bounded Context is responsible for:
- risk-tiered oversight rules
- checkpoint triggers
- human-in-the-loop rules
- human-on-the-loop rules
- hybrid execution control rules
- escalation thresholds
- irreversible action gating
- external publication gating

#### Audit and Trace Governance
This Bounded Context is responsible for:
- auditability requirements
- trace completeness rules
- visible accountability
- evidence expectations
- review trace rules
- approved versus executed trace visibility
- human modification visibility

#### Extension and Execution Governance
This Bounded Context is responsible for:
- plugin governance
- provider governance
- model governance
- extension contract compliance
- routing constraints at governance level
- approved execution path constraints
- runtime versus config-time control boundaries

#### Exception and Override Handling
This Bounded Context is responsible for:
- policy exception handling
- override requests
- override approvals or rejections
- emergency bypass control
- exception resolution tracking
- governance-level exception auditability

---

### Authorization (accepted slice — DEC-026)
This subsection is the **accepted** authorization slice of Governance (DEC-026).
It makes concrete only the authorization rules sufficient to determine each locked
persona's exposure to the Phase 2 Operating Surfaces. The rest of this domain
remains **Governance Draft v1**, unchanged.

**Model.** An authorization rule is `subject × verb × resource × condition →
allow`, realizing the Authorization Aggregate sketch above. `resource` names the
domain resource a surface presents, at **reference altitude** (Governance
references but does not own these — see "What it owns" and "Governance may
reference but should not own"). The authoritative surface↔resource mapping is
Phase 2's (`experience-architecture.md`); the Phase 2 Permission Matrix
**derives** persona↔surface exposure from these rules plus that mapping. Verb
assignments per resource are Phase-1 authorization decisions grounded in each
surface's function, within the closed verb set below.

**Verbs (closed; evidence-derived):** view · edit · approve · configure. New
verbs only on new evidence + explicit decision.

**Conditions (closed; evidence-derived):**
- **own-engagement** — scoped to the engagement(s) the subject is a party to.
- **assigned-client** — scoped to the subject's assigned client(s).
- **engagement-relevant** — scoped to engagement-relevant content.
*Full* = no condition. New conditions only on new evidence + explicit decision; a
`managed-scope` condition may enter only if Phase 1 Workforce concretely models
the management relationship.

**Combination rule.** Effective authorization is the union of the subject's
per-role allows, each retaining its own condition; an explicit `denied` outcome
beats any allow. No deny rules are authored here.

**Resources (named at reference altitude; owning domain in parentheses):**
operator work queue (Service Delivery) · production work items (Service Delivery) ·
review / approval items (Service Delivery) · client deliverables (Service Delivery) ·
client approval items (Service Delivery / Client Success) · client-facing notifications
(Client Success / Service Delivery) · knowledge artifacts (Knowledge) · admin
knowledge (Knowledge) · Client Brain (cross-cutting; owned by Knowledge — DEC-027;
partitioning draft Q-004 — access only, per the Domain Notes that Governance may
constrain access but not own it) · analytics & reporting outputs (Intelligence) · lead records (CRM) ·
billing / invoices (Finance — presentation; Finance owns) · contractor assignment
records (Workforce / Service Delivery) · agent & workflow runtime state
(Extensibility / execution) · workflow & agent configuration (Extensibility /
Governance config) · credentials & integrations (Extensibility provider/channel/
model; + Governance policy touchpoints).

**Authorization rules (by subject).**

*Operator —*
- view, edit · production work items · Full
- view · operator work queue · Full
- view, approve · review / approval items · Full
- view · Client Brain · Full (access only)
- view, edit · knowledge artifacts · Full
- view · agent & workflow runtime state · Full
- view · analytics & reporting outputs · Full
- view, edit · lead records · Full

*Manager —*
- view · operator work queue · Full
- view, approve · review / approval items · Full
- view · Client Brain · Full
- view, edit · knowledge artifacts · Full
- view · agent & workflow runtime state · Full
- view · analytics & reporting outputs · Full
- view, edit · lead records · Full
- (no rule for production work items — Manager is not exposed to it; DEC-020 projection)

*Contractor —*
- view, edit · production work items · own-engagement
- view · Client Brain · assigned-client
- view, edit · knowledge artifacts · engagement-relevant
- view · analytics & reporting outputs · own-engagement
- view · contractor assignment records · own-engagement

*Client —*
- view · client-facing notifications · own-engagement
- view, approve · client approval items · own-engagement
- view · client deliverables · own-engagement
- view · billing / invoices · own-engagement (presentation)
- view · analytics & reporting outputs · own-engagement

*System Administrator —*
- view, configure · workflow & agent configuration · Full
- view, configure · credentials & integrations · Full
- view, configure · agent & workflow runtime state · Full
- view, edit · admin knowledge · Full

**Subject-binding note.** External-persona resources that are inherently
subject-bound — a Client's own deliverables, approval items, notifications, and
billing; a Contractor's own assignment records — carry the `own-engagement`
condition at the rule level, so the authoritative layer never authorizes
cross-client or cross-contractor access. Their Phase-2 table exposure remains
*Full (primary persona)*: the table's Full describes surface exposure, while the
cross-subject data scope lives in these rules (see the acceptance criterion
below). Internal personas' unconditioned (Full) rules stand by design.

**Mapping-facing note (at altitude; Phase 2 owns the authoritative mapping).**
Each firm Operating Surface presents one of the resources above; projecting these
rules through the Phase 2 surface↔resource mapping reproduces the ratified DEC-020
exposure (the Permission Matrix population's acceptance criterion). Reference
correspondence only: Operator Inbox → operator work queue; Production Workspace →
production work items; Review Queue → review / approval items; Client Brain
Surface → Client Brain; Knowledge Workspace → knowledge artifacts; Agent &
Workflow Monitor → agent & workflow runtime state; Reports & Analytics Surface →
analytics & reporting outputs; Lead Workspace → lead records; Client
Notifications → client-facing notifications; Client Approval Queue → client
approval items; Client Deliverable Library → client deliverables; Client Billing /
Invoices Surface → billing / invoices; Contractor Assignments → contractor
assignment records; Admin Knowledge → admin knowledge; Workflow & Agent
Configuration → workflow & agent configuration; Credentials & Integrations →
credentials & integrations. Distinct-surface relationships (e.g. Operator Inbox →
Client receives the distinct Client Notifications) are separate surfaces on their
own resources, not cross-persona exposure.

---

### Domain Notes
Governance is a Domain.
It owns business responsibility for control,
not just a technical mechanism.

A Bounded Context inside Governance should isolate
one control concern.
Policy definition, authorization, checkpointing, audit,
and exception handling should not all collapse
into one vague block.

Policy is a strong candidate Entity because Faraz OS depends on
explicit policy-governed AI execution,
extension behavior, and human review control.

Checkpoint Aggregate is important because review is not globally
constant in Faraz OS.
It is triggered by policy, risk, confidence, ambiguity,
external visibility, and irreversibility.

Governance is not itself a Workflow.
It governs whether workflows may proceed, pause, escalate,
require review, or execute externally.

Governance is not merely a Capability.
Capabilities provide reusable business functions,
while Governance holds business responsibility
for the control layer.

A Plugin is not Governance.
Governance defines the rules under which that Plugin may operate.

A Provider is not Governance.
Governance constrains whether and how that option may be used.

Client Brain is a Memory Object or memory-centric artifact direction,
not a Governance artifact.
Governance may constrain access or update rules around it,
but should not absorb its ownership.

Auth infrastructure, audit infrastructure,
or policy evaluation engines may later be implemented
as Shared Services.
That does not change Governance as the Domain owner
of business control rules.

---

### Inbound events
Candidate inbound events to Governance:
- workflow execution requested
- external action requested
- publish action requested
- irreversible action requested
- approval required
- escalation triggered
- override requested
- policy updated
- permission rule changed
- routing decision requested
- low confidence detected
- ambiguity detected
- policy-sensitive action detected
- extension registered
- provider enabled
- provider disabled
- model enabled
- model disabled
- suspected policy violation detected
- audit evidence submitted

---

### Outbound events
Candidate outbound events from Governance:
- execution approved
- execution blocked
- human checkpoint required
- approval required
- escalation required
- override granted
- override rejected
- permission denied
- authorization granted
- authorization denied
- policy violation detected
- safety constraint triggered
- routing path restricted
- extension accepted
- extension rejected
- audit trail updated
- exception case opened
- exception case resolved

---

### Risks
- Governance may become a catch-all Domain if policy, auth, audit,
  routing guardrails, and exception handling are not separated
  clearly by Bounded Context.
- Governance may overlap with Workforce if role identity and access
  control are modeled as the same thing.
- Governance may overlap with Service Delivery if operational approval
  artifacts and governance checkpoint policy are mixed.
- Governance may overlap with Knowledge if policy documents,
  learnings, and decision memory are treated as the same thing
  as live governance control.
- Governance may become too infrastructure-shaped if business control
  rules are reduced to implementation details only.
- Provider-agnostic routing may become unsafe if governance-level
  model and provider constraints are not explicit.
- Override flows may quietly destroy control integrity if they are not
  narrow, auditable, and policy-bound.
- Overdesign risk exists if every future governance nuance is encoded
  before domain flows stabilize.

---

### Open Questions
- What is the final boundary between Governance checkpoint policy
  and domain-local approval artifacts?
- Should approval requirement definitions live in Governance
  while approval records live in local Domains or Workflows?
- How should reviewer, approver, and override authority be split
  between Workforce and Governance?
- Is there one unified Policy Entity, or several policy families
  such as permission policy, checkpoint policy,
  routing policy, and safety policy?
- Which actions are always human-gated, and which are conditionally
  gated by policy and risk tier?
- How should policy-level routing constraints interact with runtime
  orchestration and extensibility concerns?
- Where should audit records live at implementation level while
  Governance remains the business owner of audit requirements?
- How much policy should be runtime-configurable versus
  config-time or deployment-time?
- Assumption: Governance owns control rules, while execution-owning
  Domains keep their own operational artifacts.
- Risk: If this boundary is not kept explicit, Governance may become
  either too weak to enforce control or too broad to remain bounded.

  ## Boundary Decisions Draft v1

### Purpose
This section clarifies the current boundary decisions between:
- CRM Client Account
- Client Success Relationship
- Client Brain
- Engagement Scope
- Service Agreement
- Human Operator

These decisions remain draft,
but are intended to reduce overlap between
CRM, Client Success, Knowledge,
Service Delivery, Workforce, and Governance.

---

### Boundary Overview

#### Client
Client is best treated as an Entity owned by CRM.

CRM should remain the source of truth for:
- client identity
- account baseline
- account lifecycle state
- core client record continuity

Client is not the same thing as Client Brain,
Client Relationship,
or Engagement Scope.

---

#### CRM Client Account
CRM Client Account is an Entity or Aggregate candidate
inside the CRM Domain.

It should represent:
- the commercial and account-facing baseline for a current client
- account identity
- primary contact and stakeholder visibility
- account status
- high-level service relationship visibility
- commercial continuity visibility

CRM Client Account should not own:
- durable strategic memory
- active relationship handling logic
- client approval response history as a relationship concern
- service execution context
- workflow execution state

---

#### Client Success Relationship
Client Success Relationship is best treated as an Entity
or Aggregate candidate inside the Client Success Domain.

It should represent:
- the ongoing active relationship with the client after conversion
- communication continuity
- expectation management
- client coordination
- approval and revision communication
- relationship health and satisfaction signals
- escalation intake at the client-facing layer

A useful working distinction is:
- CRM Client Account = who the client is in the commercial/account sense
- Client Success Relationship = how the active relationship
  is being handled over time

---

#### Client Brain
Client Brain is a Memory Object
and a Shared Service Artifact, owned by Knowledge (DEC-027),
not as a CRM Entity,
not as a Client Success Entity,
and not yet as a finalized Aggregate.

Client Brain should represent:
- persistent client-specific memory
- strategic context
- relationship memory relevant to future work
- durable learnings
- approved long-lived client context
- reusable client-specific knowledge for humans and AI

Client Brain should not represent:
- the legal or commercial client account
- operational delivery state
- approval queue state
- workforce identity
- secret values

Ownership (resolved — DEC-027):
- Knowledge owns Client Brain as durable, reusable memory
- CRM references Client Brain but does not own it
- Client Success contributes heavily to its relationship-relevant content, but does not own it
- partitioning (per Client / per Brand / both) remains draft — Q-004, entangled with Q-003 Brand placement

---

#### Engagement Scope
Engagement Scope is currently best treated as a Memory Object
and a Domain Artifact aligned most strongly with Service Delivery.

It should represent:
- the active execution context for a specific engagement
- what is in scope
- what is out of scope
- current priorities
- deliverable context
- workflow rules
- execution constraints
- assigned human operator references
- approval mode
- escalation rules
- timing and operational references

Engagement Scope should not represent:
- the client account itself
- the durable client memory layer
- workforce identity records
- governance policy ownership
- secret values

Working ownership direction:
- Service Delivery is the strongest current domain direction
- Client Success may reference it for client coordination
- CRM may reference it for account visibility only
- Workforce may be referenced from it,
  but Workforce remains the source of truth for Human Operator records

---

#### Service Agreement
Service Agreement is best treated as a business artifact
that defines what has been agreed,
what is in scope,
and what is out of scope.

Current best direction:
- Engagement Scope should be derived from,
  constrained by,
  or validated against Service Agreement
- Engagement Scope should not be created as if it were
  independent from agreement reality

Service Agreement is not the same as:
- CRM Client Account
- Client Brain
- Engagement Scope

Open Question:
- Is Service Agreement owned by CRM,
  by Client Success,
  or by a separate future Bounded Context or Domain?

For now,
it is safest to treat Service Agreement as a distinct Business Artifact
whose final ownership remains draft.

---

#### Human Operator
Human Operator is best treated as an Entity inside Workforce.

Workforce should remain the source of truth for:
- operator identity
- role
- availability
- capacity
- skill profile
- employment or contractor status
- eligibility metadata

Engagement Scope may store only references to assigned Human Operators.
It should not own their identity or workforce truth.

Governance may define:
- who is allowed to approve
- who may override
- who may escalate

But Governance should not own Human Operator identity itself.

---

### Cross-Boundary Rules

#### CRM and Client Success
CRM should own account baseline and commercial continuity.
Client Success should own active relationship handling
and client-facing coordination after conversion.

This means:
- CRM may know the client exists and what account state they are in
- Client Success manages how the relationship is progressing in practice

---

#### Client Brain and CRM
CRM may reference Client Brain,
but Client Brain must not replace CRM ownership
of Client identity or account state.

A client can exist in CRM
without requiring CRM to own the durable strategic memory layer.

---

#### Client Brain and Client Success
Client Success likely contributes significant relationship memory
and client-facing learnings into Client Brain.

However,
Client Success Relationship is not the same as Client Brain:
- Client Success Relationship = operational and ongoing
- Client Brain = durable and reusable memory

---

#### Engagement Scope and Service Delivery
Engagement Scope should be treated as the active
execution-context artifact for a specific service engagement.

This makes Service Delivery the strongest current ownership direction,
even if other domains reference the artifact.

---

#### Engagement Scope and Client Success
Client Success may use Engagement Scope for:
- client coordination
- scheduling confirmation
- approval communication
- expectation alignment

But Client Success should not absorb Engagement Scope ownership,
because client-facing coordination is not the same
as execution-context ownership.

---

#### Engagement Scope and Workforce
Engagement Scope may contain assigned human operator references.

These are references only.
Workforce remains the source of truth for:
- who the operator is
- whether they are available
- whether they are eligible
- what role or skill profile they have

---

#### Workforce and Governance
- Workforce = human identity and participation baseline
- Governance = control rules over permitted actions

---

### Classification Summary

#### Domain
- CRM
- Client Success
- Service Delivery
- Workforce
- Knowledge
- Governance

#### Entity
- Client
- CRM Client Account
- Client Success Relationship
- Human Operator

#### Memory Object
- Client Brain
- Engagement Scope

#### Aggregate Candidate
- CRM Client Account Aggregate
- Client Relationship Aggregate

#### Domain Artifact
- Engagement Scope

#### Shared Service Artifact
- Client Brain

#### Business Artifact
- Service Agreement

---

### Assumptions
- Assumption: CRM owns Client identity and account baseline.
- Assumption: Client Success owns active relationship handling
  after conversion.
- Assumption: Client Brain remains memory-centric
  rather than becoming a CRM-owned account object.
- Assumption: Engagement Scope is aligned primarily
  with Service Delivery.
- Assumption: Workforce owns Human Operator truth.
- Assumption: Governance owns approval and control rules,
  not human identity.

---

### Open Questions
- Resolved (DEC-027): Client Brain is owned by Knowledge; Client Success
  contributes but does not own. (Partitioning per Client/Brand remains open — Q-004.)
- Open Question: Should Client Brain exist per Client, per Brand,
  or support both levels?
- Open Question: Is Service Agreement owned by CRM,
  Client Success, or a separate future Bounded Context?
- Open Question: Is CRM Client Account a true Aggregate,
  or a lighter account record with projections around it?
- Open Question: Should Client Success Relationship be its own
  Aggregate, or remain a lighter relationship-layer construct?
- Open Question: Should assigned human operator references
  remain a simple reference list inside Engagement Scope,
  or evolve into a stronger assignment artifact?
- Open Question: What is the exact lifecycle connection between
  Service Agreement and Engagement Scope
  creation, revision, and closure?

---

### Risks
- Risk: If CRM Client Account and Client Success Relationship
  are not separated clearly,
  current-client handling may become duplicated across Domains.
- Risk: If Client Brain is treated as a substitute for CRM records,
  memory and operational identity will collapse
  into one unstable artifact.
- Risk: If Engagement Scope is not clearly constrained
  by Service Agreement,
  execution context may drift away from agreed scope.
- Risk: If Human Operator identity and Governance authority are mixed,
  Workforce and Governance boundaries will blur.
- Risk: If these boundaries stay implicit,
  aggregate modeling in later phases may become unstable.

---

## Service Agreement Decision Draft v1

### Purpose
This section clarifies the current working role
of Service Agreement inside Phase 1 Domain Discovery.

It does not finalize all ownership questions,
but it should reduce ambiguity between:
- CRM
- Client Success
- Service Delivery
- Finance
- Engagement Scope

---

### Current Classification
Service Agreement is currently best treated as a Business Artifact.

It is important enough to shape scope,
coordination,
delivery,
and financial interpretation,
but its final ownership and final Aggregate placement
should remain draft for now.

Service Agreement is not currently treated as:
- a Domain
- a Memory Object
- a Shared Service
- a finalized Aggregate

---

### Core Role
Service Agreement should represent the business artifact
that defines what has been agreed between Faraz and the client
at the service level.

It should define or constrain:
- agreed service type
- package or engagement basis
- in-scope work
- out-of-scope work
- commercial expectations relevant to service interpretation
- approval-sensitive constraints where relevant
- high-level delivery expectations
- important timing or cadence commitments where relevant

Service Agreement should not be treated as:
- the CRM Client entity itself
- the Client Brain
- the Engagement Scope
- the detailed operational task plan
- the finance ledger
- the workforce assignment record

---

### Cross-Boundary Position

#### Service Agreement and CRM
CRM may own the commercial account-facing visibility
that a Service Agreement exists
and what high-level service relationship has been agreed.

CRM should not automatically absorb
the full operational meaning of Service Agreement.

#### Service Agreement and Client Success
Client Success may reference Service Agreement
for expectation management,
client communication continuity,
approval handling context,
and client-facing coordination.

Client Success should not automatically become
the sole owner of Service Agreement
unless later modeling confirms that direction.

#### Service Agreement and Service Delivery
Service Delivery should treat Service Agreement
as a constraining business artifact.

Engagement Scope should be derived from,
constrained by,
or validated against Service Agreement.

Service Delivery should own execution context,
not the agreement artifact by default.

#### Service Agreement and Finance
Finance may reference Service Agreement
for billing interpretation,
financial obligation context,
or package-linked invoice logic.

Finance should not own Service Agreement itself,
except possibly finance-specific sub-artifacts later
if that becomes necessary.

---

### Service Agreement and Engagement Scope
Service Agreement and Engagement Scope are not the same thing.

A useful working distinction is:
- Service Agreement = what was agreed
- Engagement Scope = how that agreed service is currently
  being executed in a bounded engagement context

This means:
- Service Agreement should constrain Engagement Scope
- Engagement Scope may become more operational and time-sensitive
- Engagement Scope should not drift away from the agreement baseline
  without explicit revision logic

---

### Candidate Contents
Service Agreement may eventually include:
- client reference
- service type
- package or offering reference
- in-scope summary
- out-of-scope summary
- service cadence or cycle type where relevant
- approval expectations where relevant
- major delivery constraints
- start condition or activation condition
- revision or exception notes where relevant
- commercial interpretation notes relevant to execution boundaries

These are candidate contents only
and remain subject to refinement.

---

### Candidate Lifecycle Direction
A possible working lifecycle for Service Agreement is:
- draft
- proposed
- agreed
- active
- revised
- closed
- superseded

This lifecycle remains draft
and should not yet be treated as final.

---

### Ownership Direction
The safest current direction is:

- Final ownership remains unresolved.
- Service Agreement should currently be treated
  as a distinct Business Artifact.
- CRM, Client Success, Service Delivery, and Finance
  may all reference it.
- No Domain should yet absorb it casually
  without an explicit later decision.

---

### Domain Implications

#### Domain
Service Agreement is not currently modeled as a Domain.

#### Entity
Service Agreement may later become an Entity
if identity continuity and revision history become central.

#### Aggregate
Service Agreement may later become a Candidate Aggregate
if scope commitments,
revision rules,
and consistency boundaries need stronger control.

#### Memory Object
Service Agreement is not a Memory Object.
It is an agreement artifact,
not primarily a reusable memory structure.

#### Business Artifact
Business Artifact is currently the best classification
because the concept is clearly important
but not yet finally placed.

---

### Assumptions
- Assumption: Service Agreement is distinct from CRM Client Account.
- Assumption: Service Agreement is distinct from Client Brain.
- Assumption: Service Agreement is distinct from Engagement Scope.
- Assumption: Engagement Scope should be derived from
  or constrained by Service Agreement.
- Assumption: Service Agreement should remain
  cross-domain referenceable
  until final ownership is clarified.

---

### Open Questions
- Open Question: Is Service Agreement best owned by CRM?
- Open Question: Is Service Agreement best owned by Client Success?
- Open Question: Does Service Agreement require
  its own future Bounded Context?
- Open Question: Should Service Agreement become
  an Entity only, or a Candidate Aggregate?
- Open Question: What exact revision logic connects
  Service Agreement changes to Engagement Scope changes?
- Open Question: Which parts of Service Agreement
  are commercial only,
  and which parts are operationally binding?
- Open Question: Should Finance reference Service Agreement directly,
  or only through narrower finance-facing artifacts?

---

### Risks
- Risk: If Service Agreement is treated as identical to Engagement Scope,
  agreement and execution will collapse into one unstable concept.
- Risk: If Service Agreement is absorbed too early into CRM,
  operational meaning may be under-modeled.
- Risk: If Service Agreement is absorbed too early into Client Success,
  commercial and contractual baseline
  may become overly communication-shaped.
- Risk: If Service Agreement remains too vague,
  scope control and aggregate boundaries will drift later.
- Risk: If revisions to Service Agreement do not propagate clearly,
  execution may diverge from agreed service reality.

---

## Service Delivery (Draft v1)

### Domain Position
Service Delivery is a Domain responsible for owning and coordinating
the execution layer of agreed client work inside Faraz OS.

It should represent the Domain that turns agreed service intent
into active engagement execution,
delivery coordination,
progress visibility,
and completion flow.

Service Delivery is not:
- CRM
- Client Success
- Workforce
- Finance
- Knowledge
- Governance

Service Delivery may reference those Domains,
but should not absorb their source-of-truth responsibilities.

---

### Responsibilities
Service Delivery is responsible for:
- engagement execution coordination
- active delivery context ownership
- deliverable planning visibility
- execution progress tracking
- task and work state visibility
- revision loop handling at execution level
- production readiness tracking
- handoff coordination across execution steps
- operational timing visibility
- delivery exception visibility
- execution completion state
- downstream handoff readiness for approval, publishing, or reporting

Service Delivery is not responsible for:
- lead acquisition ownership
- CRM client identity ownership
- active client relationship ownership
- durable client memory ownership
- workforce identity ownership
- financial ledger ownership
- governance policy ownership
- provider implementation ownership

---

### What it owns
Service Delivery owns the source of truth for:
- engagement execution state
- engagement progress state
- execution task state
- deliverable execution visibility
- revision-cycle execution state
- production readiness state
- delivery exception state
- execution completion state
- execution handoff state
- active Engagement Scope ownership direction

Service Delivery may reference but should not own:
- CRM Client Account
- Client Success Relationship
- Client Brain
- Human Operator identity records
- Service Agreement final ownership
- Finance invoices and payments
- Governance policy definitions
- Plugin internals
- Provider internals
- secrets and credentials

---

### Candidate Entities
- Engagement
- Deliverable
- Delivery Task
- Revision Cycle
- Delivery Milestone
- Production Run
- Delivery Exception
- Handoff Record
- Execution Status
- Delivery Schedule Reference

---

### Candidate Aggregates

#### Engagement Aggregate
Possible contents:
- Engagement
- Engagement Scope reference
- Service Agreement reference
- execution status
- delivery milestones
- active deliverable refs
- revision state
- handoff state

#### Deliverable Aggregate
Possible contents:
- Deliverable
- deliverable type
- current status
- revision count
- approval readiness
- publish readiness
- linked task refs

#### Revision Aggregate
Possible contents:
- Revision Cycle
- revision trigger
- change notes
- current state
- linked deliverable refs
- client-facing response refs where relevant

#### Delivery Exception Aggregate
Possible contents:
- Delivery Exception
- exception type
- severity
- current state
- escalation refs
- blocked work refs
- resolution summary

---

### Bounded Contexts

#### Engagement Management
Focus:
- active engagement state
- execution coordination
- milestone visibility
- scope-constrained delivery flow

#### Deliverable Execution
Focus:
- deliverable lifecycle
- production progress
- completion readiness
- execution state changes

#### Revision Handling
Focus:
- revision loops
- change execution
- deliverable rework
- return-to-ready flow

#### Delivery Coordination
Focus:
- internal handoffs
- timing coordination
- dependency visibility
- execution follow-through

#### Delivery Exception Handling
Focus:
- blocked work
- execution issues
- operational exceptions
- escalation into governance or client-facing flows where needed

---

### Domain Notes
Service Delivery is a Domain because it owns
a major business responsibility:
the execution of agreed work.

Service Delivery likely needs multiple Bounded Contexts
because engagement management, deliverable execution,
revision handling, and delivery exceptions
do not all share the exact same language or emphasis.

Engagement and Deliverable are strong Entity candidates
because identity continuity matters across state changes,
revisions, handoffs, and completion.

Engagement Aggregate is a strong candidate
if execution consistency must be kept around scope,
progress, deliverables, and revision state together.

Engagement Scope should currently be treated as a Domain Artifact
aligned strongly to Service Delivery.

A useful working distinction:
- Engagement Scope = the active execution-context artifact
- Engagement = the execution-bearing Entity or Aggregate candidate

---

### Candidate inbound events
- service agreement activated
- engagement created
- engagement scope created
- engagement scope revised
- deliverable requested
- deliverable ready for execution
- assignment confirmed
- revision requested
- approval rejected back to delivery
- dependency completed
- workflow exception opened
- schedule changed
- client constraint updated

---

### Candidate outbound events
- engagement started
- engagement delayed
- deliverable in progress
- deliverable ready for review
- revision cycle started
- revision cycle completed
- delivery blocked
- delivery resumed
- execution handoff prepared
- engagement completed
- delivery exception opened
- delivery exception resolved

---

### Assumptions
- Assumption: Service Delivery is the strongest current
  ownership direction for Engagement Scope.
- Assumption: Service Delivery owns execution context,
  not CRM identity truth.
- Assumption: Service Delivery owns execution state,
  not client relationship truth.
- Assumption: Workforce remains the source of truth
  for Human Operator identity and eligibility.
- Assumption: Service Agreement constrains Service Delivery
  without yet requiring final ownership here.

---

### Open Questions
- Open Question: Is Engagement a stronger Aggregate root
  than Deliverable?
- Open Question: Should Deliverable and Revision Cycle
  live under one Aggregate, or remain separate Aggregate candidates?
- Open Question: How much scheduling logic belongs
  in Service Delivery versus Workforce versus Client Success?
- Open Question: Which delivery exceptions remain local
  to Service Delivery,
  and which become Governance or Client Success concerns?
- Open Question: Should execution handoff to approval or publishing
  be modeled as a dedicated Entity or just event flow?
- Open Question: Does Engagement Scope remain only a Domain Artifact,
  or later require stronger aggregate-like rules?

---

### Risks
- Risk: If Service Delivery absorbs client relationship handling,
  it will overlap with Client Success.
- Risk: If Service Delivery absorbs Human Operator truth,
  it will overlap with Workforce.
- Risk: If Engagement Scope and Engagement are treated
  as the same concept,
  execution modeling may become unstable.
- Risk: If Service Agreement does not constrain Service Delivery
  clearly, execution may drift from agreed scope.
- Risk: If revision handling is not modeled explicitly,
  execution state and approval state may become mixed.

---

## Brand Decision Draft v1

### Purpose
This section clarifies the current working role of Brand
inside Phase 1 Domain Discovery.

It does not fully finalize Brand modeling
but should reduce ambiguity between:
- Client
- CRM
- Client Brain
- Engagement Scope
- Service Delivery
- Client Success

---

### Current Position
Brand is an important business concept
that should not currently be treated
as only a loose text field inside other artifacts.

The safest current direction is:
- Brand may become its own Entity
- or a client-scoped child entity
- but should remain explicitly modeled as a concept
  rather than hidden inside unstructured memory

This remains draft.

---

### Brand and Client
Brand is not automatically the same thing as Client.

A useful working distinction is:
- Client = the commercial or account-bearing party
- Brand = the specific market-facing identity,
  offering line,
  or operating identity that may sit under that client

This means:
- one Client may have one Brand
- one Client may have multiple Brands
- Brand should therefore remain distinguishable from Client

The exact multiplicity remains draft.

---

### Brand and CRM
CRM should remain the likely source of truth
for Client identity and account baseline.

CRM may also become the place
where Brand is referenced
or partially represented
when Brand matters for current-client account visibility
or commercial service relationships.

However,
Brand should not be reduced prematurely
to only a CRM display field
if it later requires stronger identity continuity.

---

### Brand and Client Brain
Client Brain should not be treated
as the owner of Brand identity itself.

Client Brain may store durable Brand-related memory such as:
- brand voice
- tone guidance
- style preferences
- strategic positioning notes
- reusable brand constraints

A useful working distinction is:
- Brand = identity-bearing business concept
- Client Brain = memory artifact containing durable context
  about that Brand or Client

---

### Brand and Engagement Scope
Engagement Scope may reference Brand
when a specific engagement is brand-specific.

This is especially important when:
- one Client has multiple Brands
- one Brand has different campaigns or service packages
- execution constraints differ by Brand

Engagement Scope should therefore be allowed
to reference a Brand context,
but should not become the owner of Brand identity.

---

### Brand and Service Delivery
Service Delivery may require Brand references
for execution quality,
deliverable consistency,
channel appropriateness,
and creative alignment.

Service Delivery should not own Brand identity,
but it may depend on Brand-specific context
to execute correctly.

---

### Brand and Client Success
Client Success may reference Brand
for communication continuity,
stakeholder alignment,
approval language,
and expectation management.

Client Success should not automatically own Brand identity,
even if many brand-related conversations happen there.

---

### Candidate Direction
The safest current modeling direction is:

- Client = Entity in CRM
- Brand = Entity candidate or client-scoped child Entity candidate
- Client Brain = Memory Object that may contain
  durable Brand-related memory
- Engagement Scope = Domain Artifact / Memory Object
  that may reference Brand for active execution context

This direction keeps identity,
memory,
and execution context separate.

---

### Candidate Contents
If Brand later becomes a stronger explicit Entity,
it may include:
- brand name
- client reference
- market-facing identity type
- brand status
- positioning summary reference
- voice or style reference
- offering focus reference
- stakeholder relevance
- active or inactive state

These are candidate contents only
and remain draft.

---

### Assumptions
- Assumption: Brand is not automatically identical to Client.
- Assumption: Brand should not be modeled only as a loose field
  inside Client Brain.
- Assumption: Client Brain may contain durable Brand-related memory
  without owning Brand identity.
- Assumption: Engagement Scope may reference Brand
  when execution is brand-specific.
- Assumption: Final Brand placement remains unresolved.

---

### Open Questions
- Open Question: Is Brand its own Entity,
  or a child Entity under Client?
- Open Question: Should Brand be owned primarily in CRM,
  or in an adjacent future Bounded Context?
- Open Question: Should Client Brain exist per Client, per Brand,
  or support both levels?
- Open Question: Can one Engagement Scope reference more than one Brand,
  or should it stay brand-specific?
- Open Question: Which Brand attributes are identity-level,
  and which belong only in memory artifacts?
- Open Question: Does Brand eventually require
  its own Aggregate boundary?

---

### Risks
- Risk: If Brand is treated as identical to Client,
  multi-brand clients may be modeled poorly.
- Risk: If Brand is stored only as memory text,
  identity continuity may become unstable.
- Risk: If Brand identity and Client Brain memory
  are collapsed together,
  memory and ownership boundaries will blur.
- Risk: If Engagement Scope does not reference Brand where needed,
  execution quality and context accuracy may degrade.
- Risk: If Brand is over-modeled too early,
  the file may lock into a structure
  before enough evidence exists.
