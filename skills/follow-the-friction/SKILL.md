---
name: follow-the-friction
description: Diagnose bottlenecks in an existing business or operational workflow using process evidence and available data. Use when delays, rework, errors, or poor adoption need investigation before selecting an intervention.
---

# Follow the Friction

Find where work gets stuck, why, and what evidence would distinguish the competing explanations. A workflow diagram alone is not a diagnosis.

## Establish the workflow

Start from the requested outcome and unit of work. Reuse an existing problem brief when available; otherwise state the minimum necessary framing. Trace a representative case from arrival to completion, including systems, actors, handoffs, decisions, queues, and exceptions.

Inspect accessible artifacts such as event logs, status histories, support tickets, spreadsheets, and code. Respect existing data access boundaries. Use references or aggregate summaries rather than copying sensitive records into output.

## Investigate

- Separate active handling time from waiting time and repeated work. A step with the most manual effort may not explain the longest elapsed delay.
- Check event semantics before computing durations: timestamp meaning, time zones, missing events, duplicates, reopened cases, and cases still in progress. Do not silently exclude incomplete cases and report the result as the whole population.
- Segment by factors that could explain differences, such as case type, complexity, channel, or ownership. Show sample size and time window alongside any reported rate or duration.
- Trace at least a normal case and an exception when evidence permits. If only aggregate data exists, explain which causal claims it cannot support.
- Examine ownership and incentives. A missing decision owner, unclear requirement, or inconsistent upstream input can matter more than a missing tool.
- Compare competing hypotheses. Identify evidence that supports or weakens each, and the least expensive next observation that could distinguish them.

Do not infer causation from a correlation or extrapolate an anecdote into a population claim. When useful data is unavailable, provide a concrete collection plan with fields, source, sampling approach, owner, and intended decision.

For explicit interview practice, have the user choose what to investigate and explain why. Reveal fictional evidence incrementally, label it as scenario material, and give feedback after their diagnosis rather than solving it upfront.

## Output

Provide:

1. A workflow map in prose, a table, or a diagram appropriate to the environment.
2. An evidence ledger: observation, source/window, interpretation, and limitations.
3. Ranked bottleneck hypotheses with confidence tied to evidence, not arbitrary numeric scores.
4. The next investigation and the decision it could change.
5. Candidate intervention points, distinguishing process, data, software, and AI opportunities without prematurely committing to one.

Report measured values only when actually calculated from accessible evidence. Mark illustrative numbers and estimated impacts explicitly.
