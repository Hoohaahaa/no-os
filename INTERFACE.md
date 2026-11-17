# Interface and Experience Direction

## Product character

NO OS should feel like a precise engineering instrument: calm, minimal, structured, and trustworthy. It should prioritize comprehension and control over visual spectacle.

## Visual direction

- Restrained neutral palette; dark mode may be a first-class option.
- Strong typographic hierarchy without oversized decoration.
- Generous whitespace and consistent spacing.
- Cards only where they clarify grouping or action.
- Clear alignment, grid, and responsive behavior.
- Subtle borders and restrained status colors.
- Avoid unnecessary gradients, glow, ornamental charts, and generic SaaS decoration.

## Information architecture — initial hypothesis

Potential navigation:
- Overview
- Products
- Infrastructure
- Providers
- Resources
- Workflows
- Agents
- Knowledge & Research
- Operations
- Costs
- Settings

Do not expose every future module in the first release. Navigation should reflect implemented capabilities and user tasks.

## Truthful states

The interface must distinguish:
- documented vs implemented
- configured vs connected
- connected vs provisioned
- provisioned vs operational
- estimated vs measured
- simulated vs live
- pending approval vs executed

Never display fake metrics, sample provider connections, or fictional uptime as real data. Demo data must be clearly labelled.

## Core interaction principles

- Explain the impact and permissions of actions before execution.
- Make destructive actions deliberate and recoverable where possible.
- Show provenance and last-checked time for provider status.
- Surface errors with actionable recovery guidance.
- Use progressive disclosure for advanced configuration.
- Support keyboard access, readable contrast, semantic controls, and mobile layouts.

## First useful interface

The initial UI should focus on a small set of real jobs:
1. Understand NO OS status and current implementation stage.
2. Register and inspect products.
3. Discover and evaluate providers.
4. Track connections and resources.
5. Review decisions, approvals, and recent activity.

A polished dashboard is not a substitute for working underlying operations.
