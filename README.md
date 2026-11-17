# NO OS

**An evolving control and intelligence system for building, operating, and connecting independent products.**

NO OS is intended to become the shared operating layer behind a portfolio of products. It brings together infrastructure management, provider integrations, product provisioning, AI-assisted engineering, operational visibility, and reusable knowledge—without forcing every product into one codebase, database, vendor, or architecture.

> NO OS is not a fixed blueprint. It is a system for discovering, evaluating, composing, and improving the infrastructure and capabilities that products need.

## What it is

- A **Control Plane** for projects, providers, resources, policies, and environments.
- A **Product Factory** for repeatable, permissioned product setup and provisioning.
- An **Integration Layer** for APIs, OAuth, webhooks, credentials, and events.
- An **AI Orchestration Layer** for specialized agents that research, reason, implement, and verify within bounded permissions.
- A **Knowledge System** that preserves decisions, evidence, discoveries, and lessons across products.
- An **Operations Layer** for health, costs, security, quality, and lifecycle management.

## Architectural map

The current working model uses seven flexible planes:

1. Control Plane
2. Development Plane
3. Runtime Plane
4. Intelligence Plane
5. Product Services
6. Operations Plane
7. Distribution Plane

These are provisional organizing concepts, not mandatory deployment boundaries. Capabilities may move, split, merge, or be replaced when evidence supports doing so.

The initial capability landscape includes AI coding, version control, frontend and deployment, backend and databases, authentication, AI infrastructure, storage and media, automation and workflows, payments and commerce, analytics and monitoring, communication, and growth and distribution.

## Current status

**Stage: Foundation / Phase 1.** This repository begins as a living specification and decision record. A documented capability is not necessarily implemented, connected, tested, or operational. NO OS must report those states separately and never imply a working integration where none exists.

## Development phases

- **Phase 1 — Foundation:** principles, architecture, domain model, security model, provider model, engineering standards, decision and evolution process.
- **Phase 2 — Product Factory:** project registry, provider connections, templates, resource provisioning, environment setup, and repeatable workflows.
- **Phase 3 — AI Orchestration:** specialized agents, tool permissions, research and evaluation loops, verification, and governed execution.
- **Phase 4 — Ecosystem:** controlled product-to-platform integrations, events, shared knowledge, cross-product insights, and portfolio operations.

Each phase must produce testable, useful increments. Later phases are not assumed to exist merely because they appear on the roadmap.

## Non-goals

NO OS should not become:
- A monolith that owns every product's business logic or customer data.
- A universal abstraction that hides important provider differences.
- An autonomous agent with unrestricted production or financial authority.
- A dashboard full of invented metrics, fake health states, or decorative integrations.
- A rigid framework that prevents products from choosing the right tools for their needs.

## Working principles

- Evidence before certainty.
- Explicit trade-offs over fashionable defaults.
- Least privilege and isolation by default.
- Reversible decisions where practical.
- Small, composable capabilities.
- Human approval for high-impact changes.
- Real tests and observable outcomes.
- Continuous revision without uncontrolled self-modification.

## Repository guide

- `SOUL.md` — identity and enduring intent.
- `VISION.md` — desired outcomes and boundaries.
- `PRINCIPLES.md` — engineering and governance principles.
- `THINKING.md` — reasoning, research, challenge, and synthesis method.
- `ARCHITECTURE.md` — current architectural hypothesis.
- `PRODUCT_MODEL.md` — concepts and relationships.
- `PROVIDERS.md` — provider adapter and capability model.
- `SECURITY.md` — trust boundaries, secrets, permissions, and approval.
- `ENGINEERING.md` — implementation and quality standards.
- `EVOLUTION.md` — how the system learns and changes.
- `ROADMAP.md` — phased outcomes and acceptance gates.
- `CAPABILITIES.md` — initial capability inventory and plane mapping.
- `INTEGRATION_MODEL.md` — API, webhook, event, and cross-product exchange rules.
- `AGENTS.md` — agent roles, permissions, orchestration, and evaluation.
- `OPERATIONS.md` — health, observability, reliability, and incident learning.
- `COSTS.md` — cost attribution, budgets, and provider economics.
- `INTERFACE.md` — product experience and truthful UI states.
- `BLIND_SPOTS.md` — forward-looking risks and design safeguards.
- `TECHNICAL_BASELINE.md` — provisional stack criteria, first vertical slice, and domain contracts.
- `THREAT_MODEL.md` — abuse cases and security verification requirements.
- `EVALUATION.md` — workflow and agent evaluation standards.
- `DATA_GOVERNANCE.md` — ownership, provenance, retention, and cross-product data rules.
- `DELIVERY_SYSTEM.md` — change, release, dependency, and recovery practices.
- `DECISIONS/` — durable architectural decision records.

## How to read this repository

Documents have different authority. Identity and principles express intent; architecture and provider documents describe the current best model; roadmap items express planned work; decision records explain accepted choices. A proposal is not an implementation. A decision can be superseded with a new record.

When changing a document, explain what changed, why, what evidence supports it, what alternatives were considered, and what would cause the decision to be revisited.
