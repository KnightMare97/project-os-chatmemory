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
