---
name: reality-check
description: Plan or execute an evaluation of a proposed solution or working AI application against baselines, failure cases, cost, and business outcomes. Use when a demo or quality claim needs evidence, or release readiness needs assessment.
---

# Reality Check

Determine which claims the available evidence supports and which decisions remain uncertain. Choose a plan-only or execution mode based on the request, available artifacts, and authorization. Never present proposed tests as completed checks.

## Define the evaluation

Start from the user outcome, workflow, and important failure consequences. Establish a credible baseline such as the current manual process, rules, search, or an existing product. Compare on the same cases and operating assumptions where possible.

Turn broad claims into observable criteria. For each, define the population, measurement unit, acceptance threshold or decision rule, and evidence source. Label unapproved thresholds as proposals. Distinguish offline task quality from actual adoption or business impact.

Construct a representative set with typical cases and consequential exceptions. For AI, consider missing information, ambiguity, conflicting or stale sources, unauthorized content, malicious instructions in input, and unsupported answers as applicable. Describe how cases were selected and labeled. Keep a held-out set when tuning would otherwise contaminate the result. Synthetic cases help expose failures but do not establish real-world prevalence.

## Measure what matters

- Match the metric to the task. Extraction may need field-level precision/recall and missing-value handling; a knowledge assistant may need answer support, citation validity, permission isolation, and correct abstention.
- Report denominators, sample sizes, and failure categories. A single average can hide a costly subgroup failure.
- Measure end-to-end latency and recurring cost, including retries, retrieval, failed attempts, and human review. Show actual measurements separately from volume projections.
- Test recovery and integration behavior when those affect the claim: duplicate submissions, timeouts, invalid outputs, and partial failure.
- Treat model-based judges as imperfect measurement tools. Calibrate against human-labeled examples where feasible and inspect disagreements. Do not use an unvalidated judge score as the sole evidence for a consequential release.
- Preserve enough reproducibility context: code revision, configuration/model identifier, dataset version, environment, commands or procedure, and run date. Do not include credentials or sensitive raw records.

Run only checks within the requested scope. Avoid live writes and paid large-scale evaluation unless authorized. For an unavailable integration, report the limitation and what the substitute check actually establishes.

## Output

Produce a plan or results report that clearly separates:

1. Claims, baselines, criteria, and evaluation method.
2. Cases, sampling limitations, and reproducibility details.
3. Checks actually run, measured results, and observed failures.
4. Tests not run, estimates, and unresolved uncertainty.
5. Recommendation to continue, revise, or stop, tied to the evidence and its limits.

If nothing was executed, say so prominently and provide the smallest useful next experiment. Do not claim an unmeasured reduction in business time or cost based on a successful demo.

For explicit interview practice, ask the user to define success and design the evaluation first. Challenge one metric that could look good while users still fail, then give feedback on their reasoning.
