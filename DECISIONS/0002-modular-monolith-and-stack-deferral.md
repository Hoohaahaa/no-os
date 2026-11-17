# ADR 0002: Modular Monolith and Evidence-Based Stack Selection

- **Status:** Accepted as a provisional implementation strategy
- **Date:** 2026-11-17
- **Owners:** NO OS owner
- **Supersedes:** None

## Context

The repository now defines the intended platform, but no running control-plane application exists. Selecting a vendor stack before validating authentication, data boundaries, provider access, deployment constraints, commercial terms, and recovery would create avoidable lock-in.

The system needs a small first slice that can prove identity, authorization, product/environment metadata, provider connection metadata, resource inventory, and auditability.

## Decision

1. Begin implementation as a modular monolith with explicit domain modules and provider ports/adapters.
2. Do not create independently deployed services until scale, isolation, ownership, or reliability evidence requires them.
3. Evaluate concrete hosting, database, identity, and secret-management options before committing. Record commercial eligibility, quotas, data handling, backup/restore, and exit cost.
4. The first provider integration is read-only verification. Production provisioning and agent write access remain disabled.
5. Treat the relational domain model and explicit dependency relationships as the initial source of truth. Do not introduce a graph database or event broker without measured need.
6. Keep provider-specific capabilities and limitations visible; do not promise universal portability.

## Alternatives considered

- **Microservices from day one:** rejected because they add deployment, networking, observability, and consistency costs before independent scaling or ownership needs exist.
- **A large all-in-one automation platform:** rejected because it risks coupling product logic, credentials, workflows, and provider assumptions.
- **A static dashboard backed by manual records:** rejected because it cannot prove authorization, provider verification, lifecycle correctness, or audit behavior.
- **Immediate autonomous provisioning:** rejected because the trust model, recovery path, and policy enforcement have not been implemented or tested.

## Consequences

Positive:
- Fastest route to a verifiable vertical slice.
- Lower operational overhead and easier local testing.
- Clear seams for later extraction or replacement.
- High-risk operations remain disabled until controls exist.

Costs and risks:
- Modular boundaries require discipline inside one codebase.
- The first stack evaluation delays implementation slightly.
- Some future scale requirements remain unknown.

## Revisit when

- A module requires independent scaling or deployment.
- A security boundary requires process isolation.
- Provider operations require durable orchestration beyond a simple state machine.
- Event consumers require independent delivery guarantees.
- Real usage demonstrates bottlenecks or operational risk.

## Evidence required before concrete stack approval

Compare at least two feasible options and record cost at low/expected/growth usage, security controls, data handling, operational burden, commercial restrictions, migration path, and restore evidence.