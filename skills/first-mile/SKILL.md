---
name: first-mile
description: Choose and scope the smallest useful intervention for a defined business problem. Use to compare process changes, conventional software, and AI approaches and produce an MVP decision with explicit tradeoffs.
---

# First Mile

Choose a useful first slice that can test a consequential assumption. Optimize for an observable user outcome and learning, not the shortest feature list.

## Build a fair comparison

Reuse the problem, workflow evidence, constraints, and success criteria supplied. If a missing fact could reverse the choice, identify it and either investigate or make the recommendation conditional.

Compare a small set of plausible interventions, including a credible simpler alternative. Consider changing the process, improving input quality, deterministic software, and AI where they plausibly address the cause. Do not manufacture weak alternatives to justify a preferred technology. If the user has fixed the approach, respect that constraint and compare scope or implementation choices within it.

Assess each option against:

- Expected user benefit and connection to the observed bottleneck.
- Required data, access, integrations, and operational ownership.
- Time to a useful test and reversibility if it fails.
- Failure consequences and ability to detect and recover from mistakes.
- Implementation and recurring operating costs, including human review.

Use a qualitative comparison when estimates are weak. For numerical estimates, show the inputs, units, range, and sensitivity. Do not turn guesses into a precise weighted score.

## Select the slice

Define one actor completing one meaningful workflow, including a common exception and a recovery path. Identify the hypothesis being tested and the acceptance criteria that would support continuing, revising, or stopping.

For AI, explain what uncertainty or unstructured input requires it. Specify the human decision boundary and fallback. A human review step needs an owner and a plausible workload; it is not free capacity.

Make the critical dependency visible. If access to a system or data is missing, say whether the next deliverable is an integration spike, an offline experiment, or a usable product. A mock integration cannot establish production feasibility.

For explicit mock interviews, let the user compare options and defend their choice. Probe their most consequential assumption and ask what would change the recommendation. Finish with feedback rather than automatically implementing anything.

## Output

Write a decision record containing:

- Objective and evidence used.
- Options and material tradeoffs.
- Selected approach and why it wins under current assumptions.
- User journey, included capabilities, and explicit exclusions.
- Dependencies, unresolved assumptions, and the cheapest tests for them.
- Acceptance criteria, balancing metrics, and stop/revise/continue conditions.
- The next implementation or investigation step.

Do not invent delivery dates, prices, or commitments on behalf of the user. Distinguish proposed targets from agreed requirements.
