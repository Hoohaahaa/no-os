# Threat Model and Security Verification

**Status: design baseline.** No control is considered implemented until tested in the running system.

## Security objectives

Protect credentials, source code, product data, production resources, identity, agent authority, audit integrity, and availability. Limit blast radius when any provider, agent, user session, dependency, or webhook is compromised.

## Threat actors and failure sources

- Malicious or compromised user, collaborator, or account.
- Stolen OAuth token, API key, session, or CI credential.
- Prompt injection in repository files, web pages, tickets, logs, or uploaded data.
- Compromised package, GitHub Action, build artifact, model, or MCP/tool server.
- Forged/replayed webhook or confused-deputy integration.
- Misconfigured authorization, tenant boundary, or environment scope.
- Provider outage, quota exhaustion, accidental deletion, or partial provisioning.
- Insider error, stale documentation, and excessive agent permissions.

## Abuse cases

| Threat | Required control |
|---|---|
| Cross-workspace data access | Server-side tenant scoping, deny-by-default authorization, isolation tests |
| Token leakage | Secret manager, redaction, short-lived tokens, rotation and revocation |
| Prompt injection | Treat retrieved content as data; tool allowlists; separate policy from context |
| Agent privilege escalation | Non-self-modifiable permissions; per-tool scopes; approval gates |
| Webhook forgery/replay | Signature verification, timestamp tolerance, replay/idempotency store |
| Duplicate provisioning | Idempotency keys, operation state machine, reconciliation |
| Supply-chain compromise | Pinned dependencies/actions, lockfile, provenance, vulnerability review |
| Destructive mistake | Explicit plan, impact summary, approval, backup/rollback, audit |
| Cost abuse | Quotas, rate limits, budgets, anomaly alerts, provider spend limits |
| Audit tampering | Append-only access pattern, restricted writers, retention and integrity checks |

## Authorization model

Authorization must consider actor + action + target + environment + purpose + context. A role alone is insufficient for sensitive operations.

Separate permissions for:
- read metadata
- read secret reference (not secret value)
- use credential for a specific provider operation
- create/update resource
- deploy
- delete
- manage identity and permissions
- change billing
- export or share data

A provider connection is not a blanket permission grant. Each product, environment, and operation must receive explicit access.

## Agent execution boundary

- Agents receive short-lived, task-scoped capabilities.
- Prefer read-only tools and isolated branches/workspaces.
- Do not place raw secrets in model context.
- Validate tool arguments against schemas and policy.
- Require human approval for production, deletion, billing, credential scopes, identity, and data sharing.
- Log plan, tool, arguments (redacted), decision, result, and correlation ID.
- Apply time, token, operation, and spend budgets.
- Provide cancellation and revoke paths.

## Security tests before first real integration

- Unauthenticated requests are denied.
- User A cannot read or mutate User B's workspace resources.
- A product cannot access another product's resources without a grant.
- Production permissions do not follow from development permissions.
- Expired/revoked credentials fail closed.
- Secrets never appear in UI responses, logs, traces, exceptions, or AI context.
- Replayed or invalid webhook signatures are rejected.
- Duplicate requests do not create duplicate resources.
- An agent cannot invoke a tool outside its allowlist.
- Destructive actions require explicit approval and record the approver.
- Dependency and CI workflow permissions are reviewed.
- Backup restoration is tested before relying on it.

## Incident response minimum

1. Stop or isolate affected integration/agent.
2. Revoke exposed credentials and sessions.
3. Preserve relevant audit evidence without retaining secrets.
4. Determine affected products, environments, resources, and data.
5. Restore or reconcile from known-good state.
6. Notify affected parties where required.
7. Record root causes, corrective actions, and regression tests.

## Release rule

Do not describe the system as secure, compliant, or production-ready based on this document. Report controls as planned, implemented, tested, or independently reviewed, with evidence.
