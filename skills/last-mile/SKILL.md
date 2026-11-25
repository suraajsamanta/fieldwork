---
name: last-mile
description: Implement and verify a complete scoped user journey, then prepare its operational handoff. Use when a selected solution needs a working end-to-end slice, acceptance evidence, and clear setup and recovery instructions.
---

# Last Mile

Turn the selected scope into a usable result with evidence that the intended journey works. Reuse the existing problem brief, design, and evaluation criteria when available; these documents are not prerequisites for a small task.

## Establish the delivery boundary

Inspect the project instructions, current implementation, local changes, and available runtime. Confirm the intended actor, outcome, acceptance criteria, and deployment target from context. Resolve ordinary implementation choices yourself. Ask only when missing information changes the result or required authorization is absent.

Distinguish a local prototype, a deployed pilot, and a production release. Match the implementation and verification to the requested level. Do not silently replace a required integration with a mock or describe a local success as a deployed result.

## Implement a complete slice

- Build the path from user input through persistence or dependencies to the visible outcome. Include the common exception and recovery path relevant to the scope.
- Preserve existing contracts and conventions. Keep unrelated refactors out of the change.
- Enforce permissions and important state invariants at the appropriate boundary. Validate external and model outputs before using them for state changes.
- Use actual integrations when available and authorized. Mark fixtures, synthetic data, and stubs in code and the handoff. Explain the remaining integration work.
- Add or update tests where they protect meaningful behavior. Verify the acceptance criteria through the smallest set of checks that covers the changed path and its material failures.

For AI behavior, reuse representative evaluation cases and a baseline if available. Verify that unsupported or invalid output follows the designed fallback. Do not infer business impact from a single successful interaction.

## Verify and hand over

Run the relevant checks and inspect the result. Record what ran, what passed or failed, and what could not be tested. Fix failures within scope before handing back; if a required dependency is inaccessible, finish independent work and explain the precise blocker.

For a service or deployed pilot, document setup, required configuration names without secret values, operating ownership, observable failure signals, and recovery or rollback steps appropriate to the change. Explain data migration implications if any. Publishing, sending messages, changing production data, and deploying follow the user's actual authorization; this skill does not grant it.

Finish with:

- What changed and which user outcome it enables.
- How to run or use it, with links to real artifacts.
- Acceptance evidence and material verification limits.
- Remaining work, dependencies, and the next decision.

For explicit mock interview practice, have the user describe the delivery sequence and demonstration first. Probe how they would prove the slice works and recover from a failed release. Provide critique rather than modifying a repository unless implementation is requested.
