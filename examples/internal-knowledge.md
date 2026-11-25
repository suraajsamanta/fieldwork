# Internal knowledge assistant

This is a fictional worked example with assumed scenario details. It describes a design and evaluation approach, not an implemented assistant or measured result.

## The request

“People keep asking the same questions. Build a chatbot for our internal docs.”

## Groundwork: identify the underlying task

Assume a support team searches policy documents to answer customer questions. The useful outcome is finding the current, authorized answer quickly. Message volume alone is a poor success metric: a chatbot can attract usage while increasing incorrect responses.

Measure time to a correct supported answer, unsupported-answer rate, appropriate abstention, and any unauthorized disclosure. Establish a baseline with existing search on representative support tasks. Investigate whether outdated documents or weak ownership explain more of the problem than retrieval.

## Follow the friction: examine the sources

Inventory source owners, access rules, update frequency, duplicate documents, and supersession metadata. Trace searches that succeed and searches that fail. Determine whether an authoritative answer exists for the difficult questions.

Assume, for illustration, that current documents exist but employees struggle to combine relevant passages. If the content instead lacks an owner or is internally contradictory, source maintenance becomes the first intervention.

## First mile: constrain the audience and corpus

Compare better navigation and search with a source-backed answering assistant. Select a pilot for one support group and a bounded set of owned documents. The assistant answers with source references or explains why evidence is insufficient. It does not send customer responses or modify policies.

## System blueprint: enforce access before generation

Core records: `SourceDocument`, `DocumentVersion`, `AccessPolicy`, `IndexedChunk`, and `AnswerTrace`. Preserve document version and source location through indexing and retrieval.

Authenticate the requester and apply their access policy to retrieval before constructing model context. Authorization changes must propagate to indexed content or be checked against an authoritative access layer at query time. A citation is not an access control.

Generate an answer from authorized retrieved passages, validate that its source references resolve to those passages, and expose document dates. If current sources conflict, explain the conflict and route to the document owner. If evidence is absent, abstain. Retrieved instructions cannot authorize tool calls or alter application rules.

If search is unavailable, show a recoverable error rather than generating an answer from model memory as if it came from company sources. Store only the trace information needed for evaluation under the applicable data retention rules.

## Reality check: evaluate separate failure modes

Use held-out questions with known supporting passages, missing answers, obsolete policies, conflicts, misleading source instructions, and documents a test identity cannot access. Compare against existing search on the same tasks.

Assess retrieval coverage, answer correctness, claim support, citation validity, correct abstention, and permission isolation separately. A working citation does not prove the cited passage supports the answer. Inspect a human-labeled subset before relying on automated judging.

Report sample sizes, failure categories, latency, and cost. A small test with no observed access failures does not prove universal isolation; verify the authorization path in code and test representative identities and access changes.

## Last mile: define the demonstration

Demonstrate a supported answer, an absent answer, conflicting sources, and the same question from two identities with different access. Include an update or revocation scenario. Handoff identifies source ownership, indexing failure signals, evaluation steps, and recovery behavior.

All checks in this example are proposed. The next concrete step would be inspecting an authorized sample corpus and testing the current search baseline.
