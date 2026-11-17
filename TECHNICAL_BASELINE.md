# Technical Baseline — Provisional

**Status: evaluation baseline, not an approved stack decision.** This document prevents accidental commitment through convenience. Revisit after the first runnable slice and actual provider tests.

## Recommendation

Begin with a **modular monolith and explicit ports/adapters**, not microservices. Keep the UI, application services, domain model, provider adapters, policy checks, and persistence as separable modules in one deployable unit until operational evidence justifies extraction.

The first system should be a control-plane application, not an autonomous infrastructure operator.

## Initial vertical slice

1. Human identity and a single owner workspace.
2. Product registry with environments and lifecycle.
3. Provider catalog (descriptive metadata only).
4. Provider connection records containing status and secret references, never secret values.
5. Resource inventory with ownership, provider identity, environment, lifecycle, and dependency edges.
6. Append-only audit history for sensitive changes.
7. Read-only connection verification for one real provider.
8. A small test suite and a deployment with truthful health state.

No automated production provisioning, billing changes, cross-product data access, or autonomous deployment in this slice.

## Stack selection criteria

Score candidates against: security maturity, operational burden, free-tier and commercial terms, portability, ecosystem support, developer experience, testability, deployment constraints, data residency, recovery, and exit cost.

| Concern | Candidate direction | What must be verified |
|---|---|---|
| Web/control UI | TypeScript web application | Server/client boundary, accessibility, deployment terms |
| Persistence | PostgreSQL | Backups, restore, migrations, connection limits, branching semantics |
| Identity | Managed OIDC/OAuth-compatible identity | Session security, MFA, account recovery, tenant isolation, export |
| Secrets | Dedicated secret manager or KMS-backed envelope encryption | Rotation, access logs, key ownership, recovery |
| Hosting | Managed application platform | Commercial eligibility, build limits, functions/runtime limits, region |
| Provider access | Server-side adapters | OAuth scopes, token refresh, rate limits, idempotency, API versions |
| Observability | OpenTelemetry-compatible signals | Data minimization, retention, cost, export |
| Workflows | Deterministic state machine first | Durable execution and compensation needs before adopting a workflow engine |
| AI | Model gateway abstraction with explicit provider metadata | Separate API billing, data retention, model availability, rate limits, evals |

These are categories, not selected vendors. Existing user accounts or integrations do not imply permission, quota, API access, or commercial eligibility.

## Architectural contracts

- Domain logic must not depend directly on vendor SDK types.
- Each provider adapter declares capabilities, unsupported operations, scopes, rate limits, and version.
- Persist provider external IDs and local IDs separately.
- Every write operation has an idempotency strategy or is explicitly marked non-idempotent.
- Every external call has timeout, bounded retry policy, and structured error classification.
- Use transactional outbox only when reliable event publication is required; do not introduce a broker by default.
- Version API and event schemas. Define compatibility and deprecation rules.
- Keep audit records separate from mutable display state.
- Use UTC timestamps and explicit timezone conversion at UI boundaries.
- Store money as integer minor units plus currency, not floating point.
- Use opaque IDs; do not expose sequential database IDs as authorization.
- Enforce authorization server-side on every request and resource boundary.

## Data model v0

Core entities and minimum relationships:

- Workspace: owns users, projects, policies, and provider connections.
- Membership: user, workspace, role, status.
- Product: workspace, owner, slug, lifecycle, repository reference.
- Environment: product, name, risk tier, lifecycle.
- Provider: catalog identity, adapter version, capabilities, documentation and terms references.
- ProviderConnection: workspace, provider, account reference, granted scopes, secret reference, verification state, verified_at.
- Resource: product/environment, provider connection, external ID, type, lifecycle, observed state.
- Dependency: source resource/product, target resource/provider, relation type, scope, provenance.
- Operation: requested action, actor, plan, state, idempotency key, timestamps, result reference.
- AuditEvent: actor, action, target, decision, timestamp, correlation ID, redacted metadata.
- KnowledgeRecord: content reference, type, source, confidence, scope, sensitivity, review date, status.

Do not create every table before the slice requires it. This is a conceptual model to guide migrations.

## What not to build yet

- Kubernetes, service mesh, or microservices.
- A universal provider abstraction that erases differences.
- A graph database, event broker, or vector database without measured need.
- Autonomous agents with write access.
- A custom identity provider or homemade cryptography.
- A generic workflow designer.
- A multi-tenant billing engine.
- A central store for product customer data.

## Decision gate

Before selecting a concrete stack, record:
1. Requirements and constraints.
2. At least two viable alternatives.
3. Total monthly cost at low, expected, and growth usage.
4. Security and operational trade-offs.
5. Migration and exit path.
6. What evidence would cause us to reverse the choice.

The first deployment should prove the full path: authenticated user → authorized request → validated domain operation → database transaction → audit record → observable result.
