# Customer onboarding

This is a fictional worked example. All scenario details below are assumed for illustration. No application has been implemented, no client engagement is represented, and no performance improvement has been measured.

## The request

“Customers take too long to get onboarded. Can AI help?”

## Groundwork: define the outcome

Assume the operations team receives onboarding documents through a shared inbox and records progress in a CRM. An operations reviewer decides when a case is ready for activation.

The objective is to reduce elapsed time from submission to readiness without increasing incorrect approvals. Measure median and upper-tail elapsed time, incomplete-case age, reviewer handling time, and incorrect readiness decisions. A baseline is not available yet. Collect case status histories and review a sample of completed and open cases before setting a target.

The first question is which delay dominates: waiting for missing customer information, queueing for a reviewer, or resolving unclear requirements. These causes imply different interventions.

## Follow the friction: distinguish explanations

Request submission, document receipt, review start, missing-information request, resubmission, and readiness timestamps. Establish whether each timestamp reflects the actual event or a later CRM update. Include reopened and unfinished cases.

Compare simple and complex case types. Trace a normal case and a case returned for corrections. If missing requirements dominate, inspect whether the requirements were clear at submission. Better intake instructions may outperform document automation.

For the rest of this example, assume the investigation finds repeated manual checks for missing fields to be a useful intervention point. This is a scenario assumption, not an observed finding.

## First mile: choose the slice

Compare three options:

| Option | Why consider it | Main limitation |
| --- | --- | --- |
| Clearer checklist at intake | Cheap way to prevent omissions | Does not inspect existing free-form documents |
| Rules over structured form fields | Predictable missing-field detection | Depends on collecting structured inputs |
| Assisted extraction with deterministic validation | Can process varied document layouts | Extraction errors and reviewer workload need evaluation |

Select assisted extraction only for the assumed mix of existing unstructured documents. The first slice lets a reviewer upload a document, inspect extracted values beside source evidence, correct them, and save a reviewed checklist. It excludes automatic activation and automatic customer messages.

## System blueprint: preserve the decision boundary

Core records: `Case`, `Requirement`, `DocumentVersion`, `ExtractionAttempt`, and `ReviewDecision`. The CRM remains the source of truth for case ownership. Each review refers to the exact document and checklist versions it evaluated.

An extraction job proposes structured fields with source locations. Deterministic validation checks required fields and formats. Missing or unreadable values remain missing; the system must not invent them. The reviewer can correct proposals and explicitly save the reviewed result.

A new document version invalidates an outdated pending review. Retried jobs must not create duplicate decisions. If extraction fails, the case stays reviewable manually and the failure is visible to the operator. Permissions follow case access, including access to stored documents.

## Reality check: test before claiming impact

Construct held-out documents with absent fields, contradictory values, unusual layouts, and unreadable sections. Compare extraction with reviewer labels. Measure per-field errors, false completeness, correction effort, end-to-end latency, and recurring cost. Then compare reviewer handling time on equivalent cases with and without assistance.

Proposed release condition: no automatic readiness decisions, all supported fields traceable to source evidence, and observed review effort that justifies operating cost under agreed error tolerances. Exact thresholds require the workflow owner's agreement.

Offline extraction accuracy cannot establish shorter end-to-end onboarding time. A pilot must measure the workflow outcome and account for case mix and concurrent process changes.

## Last mile: define the demonstration

Demonstrate a complete review, a document with missing information, and a failed extraction recovered through manual review. Verify access boundaries and document-version handling. Handoff includes setup, evaluation procedure, retry behavior, and an operations owner.

This walkthrough is a specification for a possible implementation. All proposed checks and demonstrations remain unexecuted.
