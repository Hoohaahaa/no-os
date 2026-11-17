# Engineering Standards

## Delivery standard

A feature is complete only when its behavior is defined, implemented, tested at the appropriate levels, observable, documented, and safe to operate. A UI mockup or successful build alone is not completion.

## Architecture

- Prefer clear module boundaries and explicit interfaces.
- Start with the simplest architecture that supports the current validated use cases.
- Avoid premature microservices and generalized frameworks.
- Keep provider-specific behavior inside adapters where practical.
- Version public contracts and data schemas.
- Make provisioning operations idempotent where possible.
- Design workflows with timeouts, retries, and compensation.

## Code quality

- Use strict typing where the language supports it.
- Validate untrusted input at boundaries.
- Handle errors explicitly; do not silently swallow failures.
- Keep modules cohesive and dependencies directional.
- Avoid hidden global state and implicit cross-product coupling.
- Keep configuration separate from code and secrets separate from configuration.
- Add comments for non-obvious constraints and decisions, not to narrate obvious code.

## Testing

Use a proportionate test pyramid:
- Unit tests for domain logic and policy.
- Contract tests for provider adapters and APIs.
- Integration tests for real boundaries, using safe test resources.
- End-to-end tests for critical user workflows.
- Security tests for authorization, isolation, secret handling, and injection boundaries.
- Failure tests for timeouts, retries, duplicate events, partial provisioning, and rollback.

Mocked tests must be labelled as mocked. Do not report them as proof that a real provider integration works.

## Reliability

Define timeouts, retry limits, idempotency keys, rate-limit handling, and failure states. Avoid unbounded retries. Record correlation IDs. Design for partial failure rather than assuming multi-provider operations are atomic.

## User interface

The interface should feel like a precise engineering instrument:
- Minimal, restrained, clear hierarchy and generous whitespace.
- Responsive across mobile and desktop.
- Real status and provenance; no fabricated metrics.
- Distinguish configuration from live operational state.
- Make permissions, costs, and destructive actions understandable.
- Prefer progressive disclosure over dense control panels.

## Documentation

Keep documentation close to the implementation. Mark status (hypothesis, proposed, accepted, experimental, deprecated), owner, date, evidence, and revisit conditions for consequential decisions. Update docs when implementation diverges.

## Pull requests and changes

For meaningful changes, include purpose, scope, design notes, tests, risks, security implications, migration/rollback plan, and screenshots for UI changes. Prefer small reviewable changes over broad rewrites.
