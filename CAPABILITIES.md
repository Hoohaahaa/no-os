# Capability Landscape

**Status: Initial inventory.** The groupings below are provisional. A capability may span more than one plane, and the inventory may be reorganized as evidence accumulates.

## Mapping principles

- Planes organize responsibilities; capabilities describe useful abilities.
- Providers implement capabilities; products consume only what they need.
- One provider may implement several capabilities, and one capability may have several providers.
- Do not build a capability merely because it appears in this inventory.
- Keep provider-specific constraints visible.

## Initial capability map

| Capability area | Primary plane(s) | Example abilities | Notes |
|---|---|---|---|
| AI coding | Development, Intelligence | code assistance, repository analysis, test generation | Keep code changes reviewable and permission-scoped. |
| Version control | Development, Control | repositories, branches, commits, pull requests | Product owns repository and access policy. |
| Frontend and deployment | Development, Runtime, Distribution | build, preview, deploy, domains, edge delivery | Deployment is distinct from source control. |
| Backend and databases | Runtime, Product Services | APIs, relational data, queues, jobs | Product data isolated by default. |
| Authentication and authorization | Product Services, Control | user identity, sessions, roles, service identity | Distinguish end-user auth from provider authorization. |
| AI infrastructure | Intelligence, Runtime | model routing, embeddings, inference, evaluation | Model access, budgets, privacy, and provider terms matter. |
| Storage and media | Runtime, Product Services | object storage, upload, transform, delivery | Separate public assets from private user data. |
| Automation and workflows | Control, Intelligence, Operations | schedules, triggers, retries, approvals | Require idempotency and bounded execution. |
| Payments and commerce | Product Services, Operations | checkout, subscriptions, invoices, entitlements | High-risk; human approval for financial actions. |
| Analytics and monitoring | Operations, Intelligence | product analytics, logs, metrics, traces, alerts | Minimize personal data and define retention. |
| Communication | Product Services, Distribution | email, push, SMS, chat, support | Consent, deliverability, and cost controls. |
| Growth and distribution | Distribution, Intelligence | SEO, campaign integrations, app distribution | Avoid optimizing vanity metrics over product value. |

## Capability lifecycle

A capability moves through evidence-based states such as:
- identified
- researched
- evaluated
- proposed
- approved
- implemented
- verified
- operational
- deprecated

The UI and API must not collapse these into a single “available” state.

## Provider selection record

For each capability adoption, record:
- Product and environment that need it
- User problem and functional requirements
- Candidate providers and primary documentation
- Required permissions and data flows
- Pricing, quotas, regions, and terms checked date
- Reliability and security evidence
- Integration and migration cost
- Recommendation and rejected alternatives
- Validation and rollback plan

## Expansion

New capability areas can be introduced when a real product need or strategic opportunity justifies them. Existing areas can be split, merged, renamed, or retired through a documented change.
