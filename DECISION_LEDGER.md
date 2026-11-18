# Decision & Alternatives Ledger

**Status: Required governance capability — design baseline.**
**Scope: Every NO OS-managed product, connected conversation, agent workflow, and consequential operating decision.**

## Purpose
NO OS must preserve not only what was chosen, but also the meaningful paths considered and not taken, together with the reasons, evidence, assumptions, and conditions behind those choices. This prevents repeated analysis, preserves institutional memory, exposes stale assumptions, and allows future teams and agents to revisit paths when circumstances change.

This is a first-class capability of the Knowledge & Decisions layer. It applies to product strategy, UX, research, architecture, technology, providers, business models, prioritization, and operations.

## Capture rule
For every material decision made in a NO OS-managed product or connected conversation, capture the decision context and meaningful alternatives to the extent they were actually discussed or investigated. A material decision meaningfully affects product direction, user experience, architecture, technology, provider choice, data, security, cost, roadmap, business model, resource allocation, or a consequential workflow.

Do not create ceremony for trivial, reversible choices. Capture depth scales with impact, uncertainty, and irreversibility.

## Required record
- Context: product, project, conversation/workflow, date, owner, and decision scope.
- Problem and objective: what was being optimized or solved.
- Constraints: requirements, budget, time, technical limits, policy, and dependencies.
- Options considered: materially different paths actually discussed or investigated.
- Selected path: what was chosen, by whom, and when.
- Alternatives not selected: each meaningful path not taken.
- Disposition: rejected, deferred, not investigated, blocked, or superseded.
- Reason: the actual stated rationale, not a reconstructed story.
- Evidence and provenance: sources, experiments, links, data, and supporting conversation/artifact.
- Assumptions and confidence: what must be true and how certain that is.
- Trade-offs: benefits sacrificed, costs accepted, risks, and opportunity cost.
- Revisit triggers: events, thresholds, new evidence, or dates that should reopen the decision.
- Outcome: what happened after implementation or validation.
- Status and history: proposed, accepted, experimental, rejected, deferred, superseded, or revisited, with timestamps.

## Disposition semantics
- **Rejected:** explicitly evaluated and intentionally not selected.
- **Deferred:** intentionally postponed; may be reconsidered later.
- **Not investigated:** a plausible option that was not meaningfully evaluated.
- **Blocked:** could not proceed because of an external dependency, missing permission, resource, or constraint.
- **Superseded:** once selected, later replaced by a new decision.
- **Unknown:** available evidence does not establish why the path was not taken.

An option is not rejected merely because it is absent from the final plan.

## Evidence integrity
- Never invent an alternative, discussion, decision-maker, or reason.
- Distinguish direct statements from agent inference and later reconstruction.
- Mark reconstructed historical records as **retrospective**, include source and confidence, and preserve uncertainty.
- If the reason is unavailable, record **reason unknown** and create a follow-up task when the answer is recoverable.
- Preserve stable references to original conversations, commits, research, issues, and artifacts where access and retention policies permit.
- A summary must not replace the source record.
- Correct records through versioned amendments; do not silently rewrite history.

## Conversation and agent protocol
Every product-connected chat, agent, and workflow must:
1. Identify the product and decision scope when known.
2. Detect material decisions and meaningful alternatives during the work, not only at the end.
3. Ask a concise clarification when a missing rationale is important and cannot safely be inferred.
4. At task completion, summarize selected and non-selected paths, reasons, unknowns, and revisit triggers.
5. Create or update a durable ledger record through an authorized integration.
6. Link the record to the source conversation and relevant product entities.
7. If durable write access is unavailable, provide a clearly marked capture-ready record and create/raise a follow-up task; never claim it was saved.
8. Avoid recording sensitive content beyond the approved purpose and access scope.

A connected chat is not automatically authorized to read every other product or conversation. Context sharing must remain explicit, scoped, auditable, and revocable.

## Retrospective backfill
1. Inventory accessible repositories, product documents, decision notes, issues, design artifacts, and connected conversation history.
2. Extract material decisions and alternatives evidenced by those sources.
3. Record selected paths, non-selected paths, and stated reasons.
4. Mark each entry retrospective and attach source references and confidence.
5. Where a reason or option is missing, record the gap rather than guessing.
6. Create follow-up tasks to recover missing rationale from the owner or original participants when practical.
7. Prioritize high-impact, costly, security-sensitive, irreversible, and repeatedly revisited decisions first.
8. Track coverage and unresolved gaps per product; do not label a product backfilled until its scope and limitations are documented.

Backfill is best-effort and bounded by available access, retention, and time. NO OS must not claim access to chats or systems it cannot actually inspect.

## Review and learning
The ledger should answer: What alternatives did we reject and why? Which decisions rely on assumptions that are now false? Which deferred paths are now feasible? Which decisions repeatedly caused rework? What did we learn from a rejected approach? Which products made similar decisions and can share evidence without sharing private product data?

Periodically review high-impact and stale decisions. Reopening a decision does not erase its history.

## Acceptance criteria
- A material decision can be recorded with selected and non-selected options.
- The system distinguishes rejected, deferred, not investigated, blocked, superseded, and unknown.
- Source provenance, confidence, and retrospective status are queryable.
- Product and conversation links respect access boundaries.
- Agents and connected workflows can create capture-ready records and authorized durable writes.
- Missing historical rationale creates a visible follow-up task rather than fabricated certainty.
- A user can inspect, correct, revisit, and export decision history.
- Tests verify permission isolation, provenance preservation, and that unknown reasons are never auto-filled as facts.
