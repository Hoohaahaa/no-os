# Provider and Capability Model

## Purpose

Providers are replaceable implementations of capabilities. NO OS should make it possible to compare and operate providers without pretending their APIs, pricing, limits, or semantics are identical.

## Provider adapter responsibilities

An adapter may expose, where supported:
- Identity and account discovery
- Authentication and authorization flow
- Capability declarations
- Resource discovery and provisioning
- Resource inspection and lifecycle operations
- Webhook registration and verification
- Usage, pricing, and quota metadata
- Health checks and diagnostics
- Documentation and support references

An adapter must declare unsupported operations explicitly. A placeholder adapter is not a connected integration.

## Capability contract

For each capability, document:
- Stable capability identifier and version
- Inputs and outputs
- Required scopes and permissions
- Idempotency behavior
- Timeouts, retries, and rate limits
- Provider-specific constraints
- Data sensitivity
- Cost model and quota considerations
- Failure modes and recovery strategy
- Test coverage and conformance status

## Provider evaluation

Evaluate providers using product-specific needs: functional fit, reliability evidence, security, compliance, regions, developer experience, pricing, quotas, portability, support, and exit cost. Do not rank providers with a universal score detached from context.

## Connection lifecycle

1. Discover provider and available connection methods.
2. Explain requested permissions and data access.
3. Obtain explicit authorization.
4. Store credentials in an appropriate secret manager.
5. Validate connection with a minimal non-destructive check.
6. Record granted scopes, owner, timestamps, and status.
7. Monitor expiry, revocation, quota, and failures.
8. Support revocation and safe resource cleanup.

## Credential rules

- Never store raw secrets in source control, logs, browser storage, or ordinary project metadata.
- Prefer OAuth or short-lived credentials where available.
- Encrypt stored credentials and restrict decryption to narrowly scoped server-side operations.
- Separate credentials by provider account, product, environment, and purpose when practical.
- Support rotation and revocation.
- Redact secrets from logs and error messages.
- Do not assume connecting a provider once grants every product or operation access.
- Provider billing, account approval, organization policy, and API terms remain authoritative.

## Provider neutrality without false abstraction

A common interface should standardize orchestration, not erase differences. Expose provider-specific options and constraints where they affect correctness, cost, or security. Avoid lowest-common-denominator interfaces that prevent useful capabilities.

## Current integration truth

A provider is only **connected** after authorization and a successful validation. A resource is only **provisioned** after the provider confirms creation and NO OS records the external identifier. An integration is only **operational** when a defined health or functional check succeeds.
