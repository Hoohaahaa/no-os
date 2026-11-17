# ADR 0001: Foundation and Product Boundaries

- **Status:** Accepted as the initial working baseline
- **Date:** 2026-11-17
- **Scope:** Repository and system direction
- **Revisit when:** The first real product integration exposes a better boundary or the operating model changes materially.

## Context

NO OS is intended to support multiple independent products and reduce repeated infrastructure and engineering work. A single shared application or database for all product data would create unnecessary coupling and a large security blast radius. A rigid list of infrastructure categories would also constrain future discovery.

## Decision

1. Treat NO OS as a control, integration, intelligence, and knowledge layer—not as the owner of every product's business logic.
2. Keep products independently deployable and their operational data isolated by default.
3. Use seven flexible architectural planes as an organizing model, not as mandatory service boundaries.
4. Keep the twelve initial capability areas as an extensible inventory, not a fixed taxonomy.
5. Model providers through adapters and explicit capability contracts while preserving meaningful provider differences.
6. Centralize only the metadata, coordination, and explicitly approved knowledge needed by NO OS.
7. Require scoped credentials, auditable access, and human approval for high-impact actions.
8. Build in four phases, with a testable acceptance gate for each phase.

## Alternatives considered

- **One monolithic platform and shared database for all products:** simpler to begin, but creates coupling and broadens the impact of failure or compromise.
- **Microservices from day one:** offers deployment independence but adds operational overhead before scale or team boundaries justify it.
- **A fixed universal provider abstraction:** appears clean but can hide important differences in capabilities, pricing, permissions, and failure behavior.
- **Build all phases immediately:** increases scope and makes it difficult to validate the foundations.

## Consequences

The initial implementation should favor modular boundaries and a small number of real workflows. Product-specific data remains with products. Some cross-product capabilities will require explicit APIs, event contracts, and permissions. The platform will need careful lifecycle and audit models.

## Validation

Validate this decision by implementing a real project registration and provider connection workflow, then testing isolation, revocation, failure recovery, and the ability to replace a provider without rewriting product business logic.
