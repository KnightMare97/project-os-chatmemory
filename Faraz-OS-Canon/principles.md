## Principles

1. AI-first, but not AI-only.
AI is the default execution layer, while humans retain judgment and accountability.

2. Human-governed automation.
Automation must pause at defined checkpoints where approval, correction, or escalation is required.

3. Workflow-centered design.
The system is designed around executable business workflows, not isolated screens or disconnected modules.

4. Domain-defined boundaries.
Each major business responsibility must live within a clear bounded context.

5. Capability-based reuse.
Reusable capabilities must serve multiple workflows, channels, and providers without duplicating business logic.

6. Event-driven coordination.
Domains should coordinate through events and explicit contracts, not direct coupling or shared internal models.

7. Memory-centric architecture.
Operational knowledge, client context, rules, and learnings must be structured as reusable memory for both humans and AI.

8. Risk-tiered oversight.
Human review should increase with risk, ambiguity, low confidence, or irreversible impact.

9. Continuous learning loops.
Every execution path should generate feedback that improves prompts, policies, workflows, and memory.

10. Modular, plugin-ready evolution.
New channels, tools, providers, and services must be addable without major architectural redesign.
