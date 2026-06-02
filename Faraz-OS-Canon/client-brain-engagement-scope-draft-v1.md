## Scope Object / Client Brain / Engagement Scope — Draft v1

### Current Position
The original Scope Object concept should be treated as a transitional concept,
not as a standalone Domain.

### Proposed Split
The Scope Object concept should likely evolve into two distinct artifacts:
1. Client Brain
2. Engagement Scope

### Client Brain
[Memory Object]
[Shared Service Artifact]

Persistent client-level memory used across services, workflows, and time.

Owns:
- durable brand context
- audience
- positioning
- voice
- restrictions
- long-lived preferences
- strategic learnings
- decision summaries

Primary Owner:
- Client Success
- Knowledge

### Engagement Scope
[Memory Object]
[Domain Artifact]

Service-level or project-level executable scope
for a specific package, campaign, or deliverable set.

Owns:
- active service scope
- deliverables
- execution constraints
- workflow policies
- current priorities
- engagement-specific goals
- approval mode
- references to Client Brain context

Primary Owner:
- Service Delivery

### Relationship
One Client may have one Client Brain
and multiple Engagement Scopes.

### Architectural Benefit
This separation reduces:
- memory fragmentation
- domain confusion
- workflow coupling

and improves:
- reusability
- versioning
- auditability
- extensibility


### DEC-PROPOSED
The original Scope Object should be reinterpreted as a transitional concept.

Faraz OS should likely distinguish between:
- Client Brain as persistent client memory
- Engagement Scope as service-level executable context
