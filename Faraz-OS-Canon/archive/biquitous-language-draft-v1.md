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
