# Operations, Reliability, and Observability

## Operational objective

NO OS should provide an accurate view of what exists, how it behaves, what it costs, and how to recover when something fails. It must not imply reliability from a green icon or an untested connection.

## Resource health

A health state must be derived from a defined check with timestamp, source, and result. Distinguish:
- unknown / not checked
- healthy
- degraded
- unavailable
- misconfigured
- authorization expired
- quota limited
- maintenance
- retired

A successful credential check is not proof that every resource or workflow is healthy.

## Observability

Use logs, metrics, traces, and audit events for different purposes:
- Logs explain discrete events.
- Metrics show aggregated behavior over time.
- Traces connect operations across components.
- Audit events record security- and governance-relevant actions.

Avoid collecting secrets or unnecessary personal data. Define retention and access policies.

## Reliability practices

- Timeouts on external calls.
- Bounded retries and exponential backoff where appropriate.
- Idempotency for repeatable writes.
- Circuit breaking or graceful degradation when justified.
- Backups and tested restore procedures for important data.
- Health checks that test meaningful behavior.
- Incident ownership and post-incident learning.
- Documented recovery and provider exit paths.

## Provisioning operations

Provisioning may partially succeed across multiple providers. Track each step, external resource identifier, and cleanup action. Do not assume distributed operations are atomic. Provide a reconciliation path for resources created externally but not recorded locally.

## Incident learning

An incident record should capture impact, timeline, detection, root causes or contributing factors, recovery, user communication, and follow-up actions. Focus on improving systems rather than assigning blame.

## Status truth

Every displayed status should identify what was checked, when, and by which mechanism. If no check exists, show unknown—not healthy.
