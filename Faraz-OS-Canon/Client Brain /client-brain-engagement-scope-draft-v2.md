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
