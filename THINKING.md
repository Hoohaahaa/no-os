# Thinking and Research Method

## Purpose

NO OS should reason deeply without turning every task into bureaucracy. The method is adaptive: use only as much investigation and structure as the risk and uncertainty require.

## A useful reasoning cycle

1. **Observe** — clarify the goal, context, constraints, stakeholders, and current evidence.
2. **Deconstruct** — identify the underlying problem, system boundaries, invariants, dependencies, and hidden assumptions.
3. **Explore** — generate materially different approaches, including the option to do nothing or defer.
4. **Challenge** — seek counterexamples, failure modes, security implications, lock-in, operational burden, and evidence against the leading option.
5. **Evaluate** — compare value, cost, complexity, risk, reliability, reversibility, and fit.
6. **Synthesize** — choose a proportionate approach and state why alternatives were not selected.
7. **Test** — validate the most consequential assumptions with prototypes, tests, benchmarks, or provider documentation.
8. **Learn** — record outcomes and update the model when evidence changes.

This is a loop, not a mandatory linear pipeline. A small reversible decision may need only a brief check. A security-sensitive or expensive decision deserves deeper investigation.

## Required distinctions

Every meaningful analysis should separate:
- Verified fact
- Source-backed but time-sensitive fact
- Inference
- Hypothesis
- Recommendation
- Unknown / not yet tested

Do not invent certainty, metrics, provider features, or implementation status.

## Evaluation dimensions

Use context-appropriate dimensions; do not mechanically score everything. Common dimensions include:
- User and product value
- Functional fit
- Security and privacy
- Reliability and failure recovery
- Cost now and at scale
- Complexity and maintenance
- Latency and performance
- Portability and vendor lock-in
- Reversibility and migration cost
- Team and operational capability
- Evidence quality and freshness

If using a score, define the scale and weights. A numeric score must not hide a critical disqualifying risk.

## Adversarial review

For consequential proposals, explicitly ask:
- What must be true for this to work?
- What is the strongest argument against it?
- What happens when the provider is unavailable, expensive, or changes its API?
- What data or authority does this expose?
- Can we remove or replace it?
- What is the simplest alternative?
- What evidence would change our minds?

## Research quality

Prefer primary documentation for provider capabilities, pricing, limits, security, and terms. Use independent sources for comparison and operational experience. Record access date for volatile information. Never treat a marketing claim as proof of reliability.

## Practical use of mathematical metaphors

Fractals suggest reusable patterns at different scales; recursion suggests composing a capability from smaller capabilities; optimization suggests explicit objectives and constraints; convergence suggests testing whether complexity is stabilizing. These are design inspirations, not claims of literal infinite computation or guaranteed optimality.

## Output format for major recommendations

A useful decision brief includes: context, problem, constraints, options, evidence, trade-offs, risks, recommendation, validation plan, rollback or exit path, confidence, and revisit triggers.
