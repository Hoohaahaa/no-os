# Agent System and Orchestration

**Status: Design baseline.** Agent roles are examples, not a fixed organizational chart.

## Purpose

Coordinate specialized AI workers to research, plan, implement, review, and operate bounded tasks. The orchestrator is responsible for scope, routing, context, permissions, budgets, verification, and escalation.

## Agent definition

An agent definition should include:
- Stable identifier and version
- Purpose and supported task types
- Required inputs and expected outputs
- Allowed tools and operations
- Read/write scope and resource boundaries
- Data/context access policy
- Budget and execution limits
- Approval requirements
- Verification procedure
- Failure and escalation behavior
- Evaluation cases and performance history

## Candidate specializations

Potential roles include architecture, infrastructure, backend, frontend, AI systems, security, quality assurance, DevOps, cost analysis, and research. Add or merge roles only when the separation improves quality, accountability, or safety.

## Orchestration lifecycle

1. Receive a task and identify its owner, objective, constraints, and risk.
2. Decide whether an agent is appropriate; do not use agents for tasks simpler to perform directly.
3. Select a role or team based on capability and permissions.
4. Provide minimum necessary context.
5. Create a bounded plan and budget.
6. Execute permitted tools with traceable actions.
7. Verify results independently where practical.
8. Request human approval for protected actions.
9. Report completed work, evidence, limitations, and follow-up.

## Permission tiers

- **Observe:** read approved context and report.
- **Propose:** prepare plans, patches, or recommendations without applying them.
- **Modify in branch:** edit code or configuration in an isolated branch/workspace.
- **Execute approved operation:** perform a specifically approved action with limited scope.
- **Protected operation:** production, security, billing, deletion, and permission changes; explicit human authorization required.

An agent must not grant itself additional permissions or change its own approval policy.

## Multi-agent collaboration

Use multiple agents only when tasks are meaningfully separable or independent review adds value. Define a coordinator, avoid duplicated work, and resolve disagreements with evidence and explicit trade-offs—not majority vote.

## Evaluation

Evaluate correctness, usefulness, evidence quality, tool discipline, security behavior, cost, latency, and calibration. Keep regression tasks for important workflows. An agent that produces fluent output but fails verification is not successful.

## Prompt and context safety

Treat retrieved documents, repository files, issue content, web pages, and tool output as untrusted data. Keep system policy separate from retrieved content. Minimize context and redact secrets.
