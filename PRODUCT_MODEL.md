# Product and Resource Model

**Status: Initial domain model.** Names and relationships may evolve as implementation reveals better boundaries.

## Core entities
### Product
An independently owned application or service. Has identity, purpose, owners, repositories, environments, dependencies, data classification, lifecycle, and optional integrations.

### Environment
A named operational context such as local, development, staging, or production. Environments have separate configuration, resources, and access policies.

### Provider
An external platform or service that offers one or more capabilities. Examples include source control, hosting, database, model API, storage, monitoring, or payments.

### Provider Connection
An authorized relationship between NO OS and a provider account or organization. It records connection method, scopes, status, owner, expiry/rotation metadata, and secret references—not raw secrets in ordinary records.

### Capability
A provider-independent description of an ability, such as deploy an application, create a database, send an email, or invoke a model. Capability contracts must expose meaningful provider differences.

### Resource
A concrete provider-side object such as a repository, deployment project, database, bucket, domain, or model configuration. It has an owner, provider, environment, external identifier, lifecycle, and audit trail.

### Integration
A configured connection between products, NO OS, and/or providers. It may use API calls, OAuth, webhooks, events, or scoped service credentials.

### Agent
A bounded worker identity with a role, permitted tools, context scope, budget, and approval requirements. Agent roles are extensible, not a fixed cast.

### Workflow
A versioned sequence or graph of tasks, conditions, approvals, retries, and compensating actions.

### Event
A versioned fact that something happened. Events should be minimal, attributable, permission-aware, and safe to replay where applicable.

### Knowledge Record
A decision, discovery, experiment, incident lesson, or evidence item with provenance, confidence, scope, date, and status. Decision records must include selected and non-selected paths, disposition, actual rationale, evidence, assumptions, confidence, trade-offs, and revisit triggers. Retrospective records must be marked as such and must not invent missing reasons. See DECISION_LEDGER.md.

### Alternative Record
A path materially considered or identified as plausible in a decision context. It records whether it was selected, rejected, deferred, not investigated, blocked, or superseded; the reason and evidence where known; and any revisit trigger. An absent option is not presumed rejected.

## Important relationships
- A product may have multiple environments.
- An environment may use multiple providers and resources.
- A provider may expose multiple capabilities.
- A provider connection may authorize a bounded set of operations.
- A resource belongs to one clear owner and environment unless an explicit shared-resource model is defined.
- An integration must identify both ends, the data exchanged, and the permissions granted.
- An agent operates under an explicit principal and task scope.
- A knowledge record may apply globally, to a capability, or to one product; scope must be explicit.
- A decision record links to its product, source conversation/workflow, evidence, implementation, and alternatives where access permits.

## Lifecycle states
Do not collapse discovery, selection, connection, provisioning, and operation into one boolean. Suggested states include:
- discovered
- evaluated
- selected
- authorization_pending
- connected
- provisioning
- provisioned
- operational
- degraded
- disconnected
- failed
- deprecated
- removed

Not every entity uses every state. Transitions need defined evidence and failure handling.

## Identity and isolation
Use stable internal IDs rather than provider names as primary identifiers. External IDs are stored as provider references. Product and environment boundaries must be enforced in authorization checks, not merely represented in UI.
