# Principles

These principles guide decisions. They are not a substitute for context or evidence; when principles conflict, document the conflict and explain the chosen trade-off.

## 1. Product autonomy
Each product owns its business logic, customer experience, and operational data. Shared services must not create accidental coupling.

## 2. Explicit composition
Integrations happen through documented contracts: APIs, events, schemas, adapters, and permissions. Avoid hidden shared state.

## 3. Least privilege
Every user, agent, service, and product receives only the access required for a specific task, resource, and duration.

## 4. Secure by design
Secrets stay server-side, are encrypted at rest and in transit, scoped, auditable, and revocable. Never commit credentials or expose them to browser code.

## 5. Evidence before adoption
Evaluate tools against real requirements, not popularity. Record sources, freshness, confidence, constraints, and unknowns.

## 6. Reversibility
Prefer modular choices and migration paths. When a decision is hard to reverse, increase research, testing, and approval requirements.

## 7. Smallest sufficient system
Do not introduce a service, abstraction, agent, database, or workflow unless its benefit justifies its operational and cognitive cost.

## 8. Observable truth
A state must reflect evidence. Distinguish discovered, evaluated, selected, configured, connected, provisioned, operational, degraded, disconnected, and deprecated.

## 9. Human accountability
Agents may research, draft, test, and propose. High-impact changes require explicit human authorization and an auditable record.

## 10. Continuous challenge
Every major design should include assumptions, alternatives, failure modes, and conditions that would invalidate it.

## 11. Data minimization
Share only the data needed for a defined purpose. Prefer metadata, aggregates, and explicit user-approved extracts over copying entire datasets.

## 12. Provider realism
Provider APIs, pricing, quotas, regions, terms, and capabilities differ and change. Adapters must expose differences rather than pretending all providers behave identically.

## 13. Quality is part of delivery
A feature is not complete because it compiles or looks finished. It needs appropriate tests, security review, operational visibility, and documented limitations.

## 14. No fake completeness
A roadmap item, mock UI, placeholder adapter, or architecture document must never be represented as a live capability.
