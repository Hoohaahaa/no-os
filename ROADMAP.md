# Roadmap

**Roadmap status: directional.** Dates and detailed sequencing should be set after validating the first implementation slice. A phase is complete only when its acceptance criteria are demonstrated.

## Phase 1 — Foundation

### Outcomes
- Clear identity, vision, principles, and research method.
- Provisional architecture and explicit open questions.
- Domain model for products, environments, providers, capabilities, resources, integrations, agents, workflows, events, and knowledge.
- Security and trust model.
- Engineering, testing, and documentation standards.
- Decision records and governed evolution process.
- A minimal repository and application plan that can be tested.

### Acceptance gate
A reviewer can explain the system boundaries, data ownership, credential flow, agent authority, lifecycle states, and what is intentionally not being built yet. The first technical slice has a defined test plan.

## Phase 2 — Product Factory

### Outcomes
- Project and environment registry.
- Provider registry and adapter contract.
- Secure connection flow and secret references.
- Initial provider integrations selected by actual use cases.
- Product templates and provisioning plans.
- Resource inventory, lifecycle, audit trail, and cost metadata.
- Safe setup workflow for a new product.

### Acceptance gate
Create a test product from a template, provision at least one real external resource with explicit authorization, record the result, and safely handle failure or cleanup.

## Phase 3 — AI Orchestration

### Outcomes
- Agent runtime and task model.
- Specialized, configurable agent roles.
- Tool allowlists, context boundaries, budgets, and approval gates.
- Research, challenge, evaluation, and synthesis workflows.
- Evaluation harness and traceable outputs.
- Human review and safe execution.

### Acceptance gate
An agent completes a bounded task end-to-end, provides evidence and tests, cannot exceed its permissions, and requests approval for a protected action.

## Phase 4 — Ecosystem

### Outcomes
- Product-facing APIs and SDK or equivalent integration contract.
- Event and webhook infrastructure.
- Explicit cross-product service sharing.
- Permissioned knowledge exchange and portfolio-level insights.
- Shared operational visibility and cost allocation.
- Recovery, revocation, and isolation tests.

### Acceptance gate
Two independent products exchange a permitted event or use a shared capability without sharing unrestricted databases or credentials; access can be audited and revoked.

## Continuous work across all phases

Security, quality, documentation, cost awareness, observability, accessibility, and simplification are continuous requirements—not later add-ons.

## Priority rule

Choose the next increment by user value, risk reduction, learning value, and reversibility. Do not implement a later-phase feature merely because it sounds more advanced.
