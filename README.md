# Fieldwork

Agent skills for investigating business problems, designing systems, and delivering useful AI.

Fieldwork starts with an unclear request and helps turn it into a scoped solution with evidence behind it. Use the skills for decomposition interview practice, client discovery, system design, or implementation work. They are independent: start where the uncertainty is, and reuse existing evidence instead of repeating earlier stages.

## Skills

| Skill | Use it to | Leave with |
| --- | --- | --- |
| [groundwork](skills/groundwork/SKILL.md) | Define the problem, users, constraints, and success criteria | A problem brief with explicit assumptions |
| [follow-the-friction](skills/follow-the-friction/SKILL.md) | Investigate workflows, data, and bottlenecks | An evidence-backed diagnosis |
| [first-mile](skills/first-mile/SKILL.md) | Choose the smallest useful intervention | An MVP scope and decision rationale |
| [system-blueprint](skills/system-blueprint/SKILL.md) | Design data models, interfaces, and failure behavior | An implementable system design |
| [reality-check](skills/reality-check/SKILL.md) | Evaluate quality, cost, failures, and business outcomes | An evaluation plan or measured report |
| [last-mile](skills/last-mile/SKILL.md) | Implement and verify a complete user journey | A working slice and operational handoff |

## Install

Clone the repository:

```bash
git clone https://github.com/suraajsamanta/fieldwork.git
cd fieldwork
```

For Codex, link the skills you want into its personal skills directory. This example installs `groundwork` and refuses to replace an existing installation:

```bash
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
ln -s "$PWD/skills/groundwork" "${CODEX_HOME:-$HOME/.codex}/skills/groundwork"
```

Repeat with the other skill names as needed. Reload skill discovery or start a new session if your agent does not see a newly installed skill. For another agent that supports `SKILL.md`, use its documented skills directory; the instructions do not require proprietary tools or a particular model.

You can also ask an agent to read a skill directly from this checkout without installing it.

## Use

The examples below follow a customer onboarding project from an unclear request to a working tool. You can use any skill independently. Sample prompts assume the relevant skill is installed.

### groundwork: when the request is vague

A client says, "We need AI to speed up customer onboarding." You need to understand who is affected, what "faster" means, and which constraints matter before choosing a solution.

```text
Use $groundwork on this client request: "We need AI to speed up customer
onboarding." Help me define the problem, identify the questions that could
change our approach, and write a brief with proposed success criteria.
```

### follow-the-friction: when you need to find the cause

You have CRM status histories and operations notes, but you do not know whether delays come from missing documents, reviewer queues, or repeated corrections. Use this skill to investigate before deciding what to automate.

```text
Use $follow-the-friction to examine these onboarding status histories
and operations notes. Separate waiting time from handling time, compare
normal and reopened cases, and identify the strongest bottleneck hypotheses.
Explain what the evidence cannot tell us yet.
```

### first-mile: when you need to choose what to build

Suppose your investigation finds that reviewers repeatedly check documents for missing information. You could improve the intake checklist, require structured forms, or build an AI extraction assistant. You need a defensible choice and a manageable first version.

```text
Use $first-mile to compare a process change, a rules-based tool,
and an AI document assistant using this workflow evidence. Recommend
the smallest useful pilot, including exclusions, dependencies, and
the conditions under which we should stop or change direction.
```

### system-blueprint: when the scope is clear but the design is not

You have selected an assistant that extracts document fields for a reviewer to approve. Now you need to decide how uploads, extraction jobs, CRM records, permissions, and review decisions fit together, including what happens when a document changes or extraction fails.

```text
Use $system-blueprint to design our document review assistant.
We have a CRM, a document store, and two operations reviewers.
Define the data model, integration contracts, access rules, and recovery
paths for failed extraction and documents replaced during review.
```

### reality-check: when a demo looks good but you need evidence

The prototype extracts fields successfully in a few demonstrations. Before proposing a pilot, you need to know how it handles missing or contradictory information, whether reviewers save time, and what each reviewed case costs.

```text
Use $reality-check to evaluate this prototype against manual review.
Use the supplied labeled documents to assess extraction errors, false
completeness, reviewer effort, latency, and cost. Separate checks you
actually run from proposed tests and unmeasured business impact.
```

### last-mile: when you are ready to deliver a working slice

The scope and design are agreed, but the application still needs a complete reviewer journey. Use this skill to implement upload, extraction, correction, and saving a reviewed result, then verify the journey and prepare a handoff.

```text
Use $last-mile to implement the agreed document review workflow in this
repository. Include manual review when extraction fails, verify the
acceptance criteria, and document setup and recovery steps. The target
for this task is a locally runnable pilot.
```

**Interview practice:** say you want a mock interview and specify a time budget if you have one. The agent asks one high-value question at a time, leaves the reasoning to you, then gives feedback. Ask for a worked solution when you want a demonstration instead. These are independent practice tools, not official materials or representations of any employer's interview process. Follow the rules of any actual assessment.

**Project work:** provide the available notes, code, data, and constraints. The agent investigates accessible evidence, asks questions that change decisions, and produces an artifact appropriate to the stage. Using a planning skill does not authorize production changes or external communications.

## Examples and templates

- [Customer onboarding](examples/customer-onboarding.md): a business workflow with document extraction and human review.
- [Internal knowledge](examples/internal-knowledge.md): a source-backed assistant with permissions and abstention.
- [Problem brief](templates/problem-brief.md), [decision record](templates/decision-record.md), and [evaluation report](templates/evaluation-report.md): optional starting points for project artifacts.

Both examples are fictional walkthroughs. They show decisions and proposed tests, not implemented applications, measured improvements, or client engagements.

## Design principles

- Trace technical decisions back to a user need or constraint.
- Distinguish observations, assumptions, estimates, and measurements.
- Compare AI with a credible simpler alternative.
- Design around exceptions and recovery as well as the happy path.
- Match the depth of the work to the decision being made.

The skills are authored for this collection. [astack](https://github.com/not-ani/astack) inspired the idea of keeping reusable agent workflows in a repository; its skill text and installer are not included here.

## License

[MIT](LICENSE).
