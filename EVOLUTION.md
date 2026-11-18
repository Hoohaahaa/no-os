# Evolution and Governed Self-Improvement

## Purpose
NO OS should learn from operation and improve its own methods, architecture, and recommendations. Evolution must be evidence-driven and governed; autonomy does not mean unrestricted self-modification.

## Learning loop
Observe → interpret → form hypotheses → challenge → evaluate → experiment → verify → record → revise.

The loop is adaptive. It should not be run ceremonially when there is no meaningful uncertainty or value.

## Knowledge record
For each consequential discovery or proposal, capture:
- Title and scope
- Date and source/provenance
- Observation or problem
- Evidence and confidence
- Hypothesis or proposed change
- Alternatives and strongest counterargument
- Expected benefit and cost
- Risks and reversibility
- Experiment or validation plan
- Outcome and follow-up
- Status: hypothesis, proposed, accepted, experimental, rejected, superseded

## Decision & alternatives memory
DECISION_LEDGER.md is the portfolio-wide source of truth for material decisions and paths not taken. Product-connected conversations, agents, and workflows must follow its capture protocol. Record why meaningful alternatives were rejected, deferred, blocked, superseded, or not investigated; preserve evidence and provenance; and never invent missing rationale.

For legacy work, create a bounded retrospective backfill task across accessible product artifacts and connected conversations. Mark reconstructed records as retrospective, include confidence and source references, and leave unknown reasons explicitly unknown. Create follow-up tasks for recoverable gaps. Do not claim access to conversations or systems that are not actually available.

## Change classes
### Class A — Low risk
Documentation corrections, local refactors, isolated tests, and reversible non-production improvements. May be automated within repository and branch permissions.

### Class B — Moderate risk
Provider adapter changes, schema evolution, workflow changes, or changes affecting multiple products. Require tests, review, and an explicit rollout plan.

### Class C — High risk
Production infrastructure, security boundaries, credential scopes, authentication, payments, data deletion/migration, cross-product access, or NO OS governance. Require explicit human approval, a tested plan, and rollback or recovery strategy.

The exact classification may be refined as the implementation matures; never downgrade a change merely to avoid approval.

## Self-critique
The system should periodically inspect:
- Complexity added versus value delivered
- Unused abstractions and integrations
- Architecture drift
- Security and permission creep
- Cost and operational burden
- Repeated incidents and failed assumptions
- Documentation that no longer matches reality
- Opportunities to simplify or remove capabilities

## Constitutional stability
The identity and core safety principles should be difficult to change casually, but not immune to revision. Changes require a documented proposal, explicit rationale, adversarial review, impact analysis, and human approval.

## No infinite-growth assumption
The system is not expected to compute endlessly or improve automatically. It should operate within explicit budgets for time, tokens, compute, money, and human attention. Stop when additional investigation is unlikely to change the decision.
