# Architecture — Current Working Hypothesis

**Status: Proposed baseline.** This document is a model to test and refine, not a frozen target architecture.

## Architectural intent

NO OS coordinates capabilities and knowledge across independent products. It should not require every capability to run in one process or every product to adopt one stack.

## Seven flexible planes

### 1. Control Plane
Project and environment catalog, provider registry, resource inventory, policies, permissions, provisioning requests, lifecycle state, and audit history.

### 2. Development Plane
Repositories, code generation, templates, CI/CD, development environments, review workflows, testing, and release coordination.

### 3. Runtime Plane
Application hosting, compute, backend services, databases, queues, scheduled jobs, and runtime configuration.

### 4. Intelligence Plane
Research, model routing, agent orchestration, context retrieval, evaluation, planning, and bounded tool execution.

### 5. Product Services
Reusable but optional capabilities such as authentication, storage, messaging, payments, search, and other product-facing services.

### 6. Operations Plane
Observability, logs, metrics, traces, alerts, incident workflows, security posture, backups, cost visibility, and reliability practices.

### 7. Distribution Plane
Domains, edge delivery, app stores, SEO, analytics activation, communication channels, and growth tooling.

These planes are organizational lenses. They do not prescribe seven deployable services. A capability may span planes or be moved when implementation evidence supports it.

## Capability landscape

The initial inventory covers twelve areas:
1. AI coding
2. Version control
3. Frontend and deployment
4. Backend and databases
5. Authentication and authorization
6. AI infrastructure and model providers
7. Storage and media
8. Automation and workflows
9. Payments and commerce
10. Analytics and monitoring
11. Communication
12. Growth and distribution

This list is intentionally extensible. It is not a fixed taxonomy and does not imply all capabilities are needed by every product.

## Major logical components

- **Project Registry:** source of truth for product identity, ownership, environments, dependencies, and lifecycle.
- **Provider Registry:** provider metadata, adapter version, capabilities, limitations, health evidence, and terms/pricing references.
- **Integration & Credential Layer:** OAuth grants, secret references, scopes, rotation, revocation, and audit.
- **Resource Manager:** desired state, provisioning plans, provider operations, reconciliation, and teardown.
- **Product Factory:** templates and repeatable workflows that assemble project-specific resources.
- **AI Orchestrator:** task routing, agent roles, context boundaries, tool permissions, verification, and approvals.
- **Knowledge Layer:** decisions, evidence, discoveries, incidents, experiments, and explicitly approved cross-product knowledge.
- **Operations Layer:** health, costs, events, alerts, audit, and incident response.

These are logical responsibilities. Do not split them into microservices until independent scaling, security, ownership, or deployment needs justify it.

## Cross-cutting contracts

- Stable project and resource identifiers.
- Versioned schemas and APIs.
- Explicit ownership and environment boundaries.
- Idempotent provisioning operations where possible.
- Retry, timeout, and compensation behavior for workflows.
- Audit records for sensitive actions.
- Correlation IDs across requests and events.
- Clear data classification and retention.
- Provider-specific capability declarations.

## Data ownership and isolation

Each product owns its operational database and customer data by default. NO OS stores central metadata and only the minimum data required to coordinate services. Cross-product insights require an explicit purpose, permission, and suitable data minimization or aggregation.

## Deployment posture

Start with the simplest architecture that can support the first real vertical slice. A modular monolith may be appropriate initially; do not adopt distributed services, event streaming, or complex agent infrastructure without demonstrated need.

## Open questions to resolve with evidence

- Which components need to run in the control plane versus remain external?
- Which resources should be provisioned automatically versus through guided workflows?
- What is the minimum viable credential broker and audit model?
- Which event transport is justified by actual integration needs?
- What knowledge belongs centrally, and what should remain product-local?
- What is the smallest useful agent runtime and evaluation harness?
