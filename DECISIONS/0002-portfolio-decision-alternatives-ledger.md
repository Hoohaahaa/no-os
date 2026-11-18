# ADR 0002: Portfolio-wide Decision & Alternatives Ledger

- **Status:** Accepted as a governance requirement; implementation pending.
- **Date:** 2026-11-18
- **Scope:** NO OS and every product, connected conversation, agent, and workflow governed by NO OS.

## Context
Product and architecture work repeatedly explores multiple directions. If only the final choice is preserved, future work loses the trade-offs, rejected paths, deferred opportunities, and assumptions that shaped the decision. This creates repeated research, avoidable reversals, and false certainty about why a path was not taken.

## Decision
Establish a portfolio-wide Decision & Alternatives Ledger as a first-class part of the Knowledge & Decisions layer. All NO OS-managed products, connected conversations, agents, and workflows must capture material decisions and meaningful paths not taken, with actual reasons, evidence, provenance, confidence, disposition, and revisit triggers.

The ledger must distinguish rejected, deferred, not investigated, blocked, superseded, and unknown. Historical entries must be marked retrospective. Missing reasons must remain unknown and generate follow-up work when recoverable.

## Alternatives considered
1. **Only record selected decisions in ordinary ADRs.** Rejected because it omits deferred and rejected alternatives and makes it difficult to understand why the current path won.
2. **Keep separate, unlinked decision notes inside each product.** Not selected because it fragments portfolio learning and makes cross-product retrieval and comparison difficult. Product-scoped records remain valid, but they should follow a common schema and permission model.
3. **Store every brainstormed possibility and every minor preference.** Rejected because it creates noise, excessive maintenance, and misleading records. Capture is limited to material decisions and meaningful alternatives.
4. **Reconstruct missing historical reasons automatically.** Rejected because inferred explanations can be mistaken for facts. Historical reconstruction must preserve provenance and uncertainty.
5. **Do nothing until the full application exists.** Rejected because the policy should govern new work immediately, even before durable application-level automation is implemented.

## Consequences
- The ledger schema and capture protocol become cross-product requirements.
- Product and conversation integrations need authorized write paths and source references.
- Agents must return a capture-ready record when persistence is unavailable.
- Retrospective backfill is required for accessible legacy material, prioritized by impact and risk.
- Cross-product retrieval remains subject to explicit access scopes; this decision does not grant blanket access to private chats or product data.
- Implementation requires durable storage, audit history, permission tests, and a review interface.

## Revisit triggers
Revisit the storage and integration design when the first persistent product registry and conversation integration are implemented, or if the shared ledger creates unacceptable coupling or privacy risk.
