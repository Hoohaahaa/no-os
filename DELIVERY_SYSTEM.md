# Delivery and Change Management

**Status: engineering baseline.** Apply proportionately; avoid heavyweight ceremony for isolated low-risk changes.

## Change record

Every meaningful change should state:
- User or operational problem.
- Expected outcome and non-goals.
- Affected products, environments, resources, data, and contracts.
- Risk class and blast radius.
- Alternatives considered.
- Tests and evidence required.
- Rollout, monitoring, rollback, and recovery plan.
- Owner and approval where required.

## Delivery path

1. Make the smallest change that tests the hypothesis.
2. Work in a branch or isolated environment when practical.
3. Run formatting, type checks, unit tests, and security checks.
4. Review dependency and permission changes.
5. Run integration/evaluation tests relevant to the change.
6. Produce a clear diff and evidence summary.
7. Obtain required human approval.
8. Deploy progressively when risk warrants it.
9. Verify actual behavior after deployment.
10. Record outcome and update docs/decisions.

## Environments

Keep development, test/staging, and production logically separated. Credentials, data, and permissions must not be silently reused across environments. Production data should not be copied to lower environments without approved minimization and protection.

## Rollback and forward recovery

Rollback is not always safe for database migrations or external side effects. For each risky operation, choose:
- rollback to prior version/state;
- forward-fix;
- compensating action;
- restore from backup;
- manual recovery with explicit owner.

Schema changes should prefer expand → migrate → contract when compatibility requires it. Never assume an external provider action can be transactionally rolled back.

## Dependency hygiene

- Commit lockfiles.
- Prefer maintained dependencies and minimal transitive footprint.
- Review licenses and security advisories.
- Pin high-risk CI actions and external build inputs.
- Document exceptional or abandoned dependencies.
- Update regularly with automated tests.
- Keep an inventory of runtime, build, and agent/tool dependencies.

## Release evidence

A release record should include source commit, build identity, environment, deployment result, test summary, dependency/security findings, approver, and rollback reference. Do not equate a successful build with a healthy release.

## Change classes

- Low: docs, isolated tests, non-production reversible changes.
- Medium: shared modules, schema changes, provider adapters, multi-product contracts.
- High: production, secrets, identity, billing, deletion, cross-product access, or governance.
  
High-risk changes require explicit approval and a tested recovery plan.