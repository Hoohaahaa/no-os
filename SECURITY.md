# Security and Trust Model

**Security posture: conservative by default.** This document is a baseline for design and implementation, not a certification or claim that the current repository is secure software.

## Assets to protect

- Provider credentials and OAuth grants
- Product source code and deployment configuration
- Customer and end-user data
- Databases, backups, storage objects, and logs
- Production environments and domains
- Payment and billing operations
- AI prompts, context, tool access, and generated artifacts
- Audit records and account ownership

## Trust boundaries

Treat each product, environment, provider, agent, user, and external webhook as a distinct security boundary. Trust must be explicit and enforced server-side.

## Least-privilege authorization

- Use scoped, revocable permissions.
- Separate read, write, deploy, delete, billing, and administrative capabilities.
- Separate development, staging, and production access.
- Prefer short-lived credentials for automation.
- Require explicit approval for destructive or high-impact operations.
- Never let an agent inherit broad user credentials by default.

## Secrets

- Do not commit secrets, tokens, private keys, or populated environment files.
- Keep secret values in a dedicated secret manager or encrypted server-side store.
- Store references and metadata in application records, not plaintext values.
- Redact secrets from logs, traces, error reports, and AI context.
- Rotate and revoke credentials when exposed or no longer needed.
- Use separate credentials for separate products and environments when feasible.

## Agent safety

Agents must have:
- A named role and accountable owner
- Explicit task and context scope
- An allowlist of tools and operations
- Resource and time budgets where possible
- Read-only defaults for exploration
- Approval gates for writes, deployment, deletion, payments, permission changes, and production changes
- Traceable action logs and verifiable outputs

Untrusted repository content, web pages, issue comments, logs, and user-generated data must be treated as data, never as higher-priority instructions.

## High-impact action policy

Require human approval before:
- Changing production infrastructure or routing
- Deleting or migrating data/resources
- Changing authentication, authorization, or secret policies
- Making purchases, payments, or billing changes
- Granting new provider scopes or cross-product access
- Publishing releases or changing domains
- Modifying NO OS governance or agent permissions

## Data handling

Classify data by sensitivity and purpose. Minimize collection, define retention, encrypt in transit and at rest, restrict access, and support deletion where required. Cross-product sharing is opt-in and purpose-bound.

## Operational controls

Plan for dependency updates, vulnerability scanning, backups, restore tests, incident response, audit review, rate limiting, input validation, webhook signature verification, and secure error handling.

## Threat modeling prompts

For each new capability, ask: what assets are exposed, who can invoke it, what can be forged, what happens if credentials leak, how can privileges escalate, what is the blast radius, and how do we detect and recover?

## Current status

This file defines required design intent. It does not mean any runtime control, vault, audit pipeline, or security test has already been implemented.
