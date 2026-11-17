# Data Governance and Knowledge Provenance

**Status: baseline policy.** Product-specific legal, regulatory, and contractual obligations must be assessed before handling real user data.

## Ownership boundaries

- Each product owns its customer data, product-specific business logic, and operational records.
- NO OS owns its own control-plane metadata, audit history, provider catalog, and approved shared knowledge.
- A product integration grants only the explicitly defined purpose and fields; it does not transfer ownership.
- Central aggregation does not authorize access to underlying records.

## Data classification

Use a small, understandable classification system:
- Public
- Internal
- Confidential
- Restricted (credentials, sensitive personal data, regulated or high-impact data)

Classification determines storage, access, logging, retention, export, and AI processing rules. Unknown classification must not default to public.

## Knowledge record requirements

Every durable knowledge item should carry:
- Type: fact, observation, inference, hypothesis, decision, preference, or lesson.
- Source and provenance.
- Scope: global, workspace, product, environment, or task.
- Owner and access policy.
- Observed/created/updated timestamps.
- Confidence and evidence.
- Sensitivity and permitted uses.
- Review/expiry date where relevant.
- Status: proposed, accepted, disputed, superseded, expired, or rejected.

Contradictions should be preserved as competing claims until resolved. Newer does not automatically mean more correct.

## Cross-product learning

Allowed patterns, subject to explicit approval:
- Reusable engineering patterns with no customer data.
- Aggregated operational metrics that cannot reasonably identify users or products.
- Sanitized incident lessons.
- Provider capability and reliability observations.
- Shared templates and evaluation fixtures.

Not allowed by default:
- Raw customer records or conversations.
- Product secrets, tokens, private source, or proprietary business data.
- Inferences about an individual moved between products.
- Model training or external AI processing beyond the original purpose.

## Retention and deletion

Define retention per data class and purpose. Support deletion, export, and revocation where required. Deletion must consider derived indexes, caches, backups, embeddings, logs, and downstream copies; document unavoidable retention windows and legal holds. A tombstone or deletion request must propagate to authorized consumers.

## AI processing

Before sending data to a model provider, record:
- Data classification and purpose.
- Provider/model and region where known.
- Retention/training settings and contractual basis.
- Minimization/redaction applied.
- Whether the use is permitted for this product and user context.

Never assume a ChatGPT subscription includes API usage or that a provider's default data handling is appropriate.

## Governance review

Any new cross-product data flow, new AI processing purpose, or material retention change requires an owner, data-flow description, risk assessment, and approval. Keep a data inventory and review it when integrations change.
