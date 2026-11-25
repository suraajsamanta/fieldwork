---
name: system-blueprint
description: Design an implementable system for a scoped workflow, including data models, interfaces, permissions, integrations, and failure recovery. Use for system design and AI application architecture, rather than implementation alone.
---

# System Blueprint

Translate a selected workflow into a design that someone can implement and operate. Make the consequential boundaries and tradeoffs explicit; do not produce an inventory of fashionable services.

## Establish the design inputs

Read the scoped user journey, acceptance criteria, and existing architecture. Inspect relevant code, schemas, and integration contracts when accessible. Preserve the established stack unless there is a concrete reason to change it. Label unverified provider capabilities and verify current documentation when the design depends on them.

Ask for missing scale, availability, tenancy, or integration requirements only when they change the design. Otherwise state assumptions and how the design would change outside them.

## Design the complete path

1. Trace a request or job from user input through authorization, state changes, dependencies, and the visible result.
2. Define core entities, identifiers, relationships, invariants, and lifecycle transitions. Name the source of truth and ownership for important fields. Include concurrency where simultaneous changes could break an invariant.
3. Specify interfaces using representative inputs, outputs, errors, and authorization rules. For external writes, cover retries, idempotency, duplicates, and partial completion where relevant.
4. Define failure behavior: detection, user-visible state, retry or recovery ownership, and escalation. Explain what happens when a dependency is unavailable or a job is interrupted.
5. Cover access boundaries and observability at the points where they matter. Name the events or metrics needed to evaluate the acceptance criteria and diagnose failure; exclude raw secrets and unnecessary sensitive payloads.
6. Sequence implementation so the first slice exercises the riskiest integration or invariant. Identify decisions that can wait.

## When AI is part of the system

Define the model's narrow responsibility and the deterministic checks around it. Specify structured output contracts, invalid-output handling, context sources, and version information needed to reproduce an evaluation.

For retrieval, apply document permissions before content reaches the model and validate source references. Describe behavior for stale, conflicting, missing, or malicious source content. Treat retrieved text as data, not authority to execute instructions.

For actions, separate a proposed action from an authorized execution. State which actor can approve, what the approval binds to, and how duplicate or outdated execution is prevented. Use abstention or review when evidence is insufficient; a model's self-reported confidence alone is not a reliability guarantee.

Account for latency, request volume, token or inference cost, and reviewer capacity using explicit assumptions. Describe a simpler fallback where it meaningfully preserves service.

## Output

Provide a design with a workflow trace, component boundaries, data model, important interface contracts, failure/recovery behavior, tradeoffs, and implementation sequence. Include a diagram only when it clarifies relationships or state transitions. Tie each major component to a requirement and mark open decisions.

For explicit interview practice, let the user sketch first. Probe a failure path and a scale or requirement change, then assess their design. Do not fill in the architecture before they have tried.
