# Integration and Data Exchange Model

## Purpose

Define how products, NO OS, providers, and agents communicate without creating uncontrolled coupling or data exposure.

## Integration patterns

### Synchronous API
Use for request/response operations where the caller needs an immediate result. Define authentication, authorization, schema version, timeout, rate limit, and error contract.

### Webhooks
Use when an external provider notifies NO OS or a product. Verify signatures, reject replays where possible, validate payloads, and process asynchronously. Never trust a webhook merely because it reached the endpoint.

### Events
Use for facts that other authorized components may consume. Events should have stable IDs, schema versions, timestamps, producer identity, tenant/product scope, and correlation IDs. Consumers must tolerate duplicates and out-of-order delivery where relevant.

### Shared service
A product may consume a centrally operated capability through a narrow API. The service must define ownership, availability expectations, cost attribution, data handling, and exit path.

### Explicit data export
Use for controlled transfer of selected records or aggregates. Define purpose, fields, retention, destination, and authorization before transfer.

## Product connection contract

A product integration should declare:
- Product and environment identity
- Owning team or principal
- Integration purpose
- Source and destination
- Data categories and classification
- Allowed operations and scopes
- Authentication method
- Schema/API version
- Rate and budget limits
- Revocation and failure behavior

## Cross-product knowledge

Central knowledge should default to technical metadata, reusable patterns, architecture decisions, provider evaluations, and anonymized or aggregated learnings. Customer-level data must not be copied centrally by default.

Before enabling cross-product insight, define:
1. The question or purpose.
2. The minimum fields required.
3. The legal and product permissions.
4. Whether aggregation or anonymization is sufficient.
5. Who can query the result.
6. Retention and deletion behavior.

## Reliability requirements

- Idempotency for retryable writes.
- Bounded retries with backoff.
- Dead-letter or manual recovery path for failed asynchronous work.
- Schema compatibility policy.
- Correlation IDs and auditability.
- Explicit timeout and partial-failure behavior.
- Revocation that actually prevents future access.

## Anti-patterns

- Directly querying another product's production database without a defined contract.
- Sharing one all-powerful service token across products.
- Treating event delivery as exactly-once without proof.
- Copying entire customer datasets “for future AI.”
- Hiding provider errors behind generic success responses.
