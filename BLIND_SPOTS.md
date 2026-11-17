# Blind Spots and Forward Design

**Status: living risk register.** This document identifies concerns that are easy to miss while building the first version. It is not a mandate to implement every capability now.

## The central test

For every proposed capability, ask: does it reduce product delivery time, operational risk, cognitive load, or long-term lock-in enough to justify its complexity?

## Blind spots to actively manage

### 1. Dependency and impact graph
A registry of isolated projects and resources is insufficient. Model relationships: product uses resource; environment deploys artifact; workflow calls provider; agent may access tool; domain routes to deployment. Every edge needs owner, scope, environment, source, confidence, and last verification. Use this graph for impact analysis, not decorative visualization.

### 2. Lifecycle and reconciliation
External operations are not atomic. A provider may create a resource while the local write fails. Model requested, planned, applying, partially_applied, active, degraded, deleting, retired, and unknown states. Record external identifiers and reconcile periodically. Never equate a successful API response with durable desired state.

### 3. Portability and exit cost
Track provider-specific features, data export formats, migration constraints, egress costs, DNS ownership, identity coupling, and replacement options. Prefer portable interfaces only where they preserve useful semantics. Keep a provider exit note for every critical dependency.

### 4. Knowledge provenance and decay
Knowledge must carry source, observed_at, scope, confidence, owner, sensitivity, expiry/review date, and status. Distinguish fact, inference, hypothesis, decision, and preference. Stale or contradicted records must be superseded, not silently treated as truth.

### 5. Agent evaluation and regression
Every consequential agent workflow needs a versioned evaluation set, expected invariants, adversarial cases, and cost/latency measurements. Evaluate tool discipline, permission compliance, evidence quality, calibration, and recovery—not just answer quality. Model or prompt upgrades must pass regression tests.

### 6. Software and AI supply chain
Track dependency manifests, lockfiles, build provenance, artifact identity, workflow permissions, model/provider versions, tool schemas, and license/privacy constraints. Build and release evidence should be reproducible where practical. Treat third-party actions and retrieved instructions as untrusted.

### 7. Recovery, not just prevention
Define backup scope, recovery point/time objectives where justified, restore tests, credential revocation, incident ownership, and provider outage procedures. A backup that has never been restored is an assumption, not a recovery capability.

### 8. Cost and human attention
Attribute spend to product, environment, provider, workflow, and capability. Include free-tier limits, overage behavior, idle resources, egress, support burden, and human review time. Alert on budget risk before execution where possible.

### 9. Data boundaries and derived knowledge
Shared learning must not become a covert path for customer data. Define purpose, lawful basis where applicable, minimization, aggregation, retention, access, deletion propagation, and provenance for derived insights. Product owners remain accountable for product data.

### 10. Change impact and architecture drift
Before a change, identify affected products, resources, contracts, agents, data schemas, and operational runbooks. Compare documented desired state with observed state. Record exceptions and expiry dates.

### 11. Human attention as a scarce resource
Do not make every operation require approval. Use risk classification, reversibility, blast radius, and confidence to determine autonomy. Batch low-risk reviews; interrupt only for material decisions or uncertainty.

### 12. Accessibility, localization, and device realities
The control surface must remain usable on mobile, keyboard-only navigation, low bandwidth, and different locales. Critical operations need clear consequences, confirmation, and recoverable error states.

### 13. Product value and adoption
A platform can become technically impressive but economically irrelevant. Track whether it shortens time-to-first-deploy, reduces repeated setup, prevents incidents, improves cost visibility, or preserves useful knowledge. Retire capabilities nobody uses.

## Design response

- Model relationships and evidence before building a graph database.
- Start with relational tables and explicit foreign keys; introduce graph infrastructure only if query needs prove it.
- Start with append-only audit events and transactional state changes; add event infrastructure only when independent consumers or delivery requirements justify it.
- Use policy checks at boundaries; do not build a generic policy engine before concrete policies exist.
- Use small deterministic workflows before autonomous multi-agent loops.
- Keep provider-specific limitations visible rather than hiding them behind false portability.

## Review cadence

Review this register at each phase gate, after a security or reliability incident, and whenever a new provider or agent gains write access. Mark items accepted, mitigated, deferred with an owner, or not applicable with rationale.
