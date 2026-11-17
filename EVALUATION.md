# Evaluation and Verification Framework

**Status: proposed standard.** Evaluation infrastructure should grow with real workflows; do not build a large benchmark platform before there is a workflow to evaluate.

## Why this exists

Fluent output is not proof of correctness. Every important automated workflow must have a measurable definition of success, known failure modes, and independent verification.

## Evaluation dimensions

- Task correctness and completeness.
- Evidence quality, source traceability, and factual calibration.
- Tool selection and argument correctness.
- Permission compliance and resistance to prompt injection.
- Reliability across repeated runs and edge cases.
- Recovery from partial failure and cancellation.
- Latency, token/compute use, and cost.
- Human correction rate and review burden.
- User impact and reversibility.

## Evaluation case format

Each case should record:
- Stable case ID and version.
- Task, context, and permitted tools.
- Expected invariants and prohibited actions.
- Input fixtures with sensitivity classification.
- Success criteria and scoring rubric.
- Adversarial variations.
- Expected escalation/approval behavior.
- Result, evidence, model/prompt/tool versions, and cost.

## Test layers

1. Unit tests for deterministic domain rules and permission checks.
2. Contract tests for provider adapters and schema compatibility.
3. Integration tests against provider sandboxes or controlled test resources.
4. End-to-end tests for critical user workflows.
5. Agent behavior evaluations for tool discipline, evidence, and escalation.
6. Security regression tests for tenant isolation, injection, and privilege boundaries.
7. Operational game days for provider outage, quota exhaustion, credential revocation, and partial failure.

## Release gates

- No critical authorization or secret-handling regression.
- Required deterministic tests pass.
- Provider contract tests pass or documented exception is approved.
- Agent evaluations meet workflow-specific thresholds.
- Cost and latency remain within defined budgets.
- Rollback or recovery path is documented for risky changes.

Thresholds must be set per workflow using real baseline data; do not invent universal accuracy percentages.

## Evaluation integrity

- Keep a stable holdout set to reduce benchmark overfitting.
- Include negative and ambiguous cases.
- Record model, prompt, tool schema, and dataset versions.
- Compare against a simple non-agent baseline when possible.
- Review false positives and false negatives separately.
- Human review should focus on high-impact and uncertain cases.
- Never use private product data in shared evaluations without explicit authorization and minimization.

## First practical benchmark

Before any autonomous coding or provisioning, create a small suite that verifies:
- The system distinguishes documented from implemented.
- It refuses access outside the granted project/environment.
- It identifies when evidence is insufficient.
- It does not expose credential values.
- It requests approval for destructive or production operations.
- It reports partial failure honestly.
