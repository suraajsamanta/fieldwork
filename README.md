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

Example requests after installing the relevant skills:

```text
Use $groundwork on this request: customer onboarding takes too long.
What do we need to understand before choosing a solution?

Use $first-mile to compare a process change, a rules-based tool,
and an AI assistant for this onboarding workflow.

Use $system-blueprint to design the selected approach.
We have a CRM, a document store, and two operations reviewers.

Use $reality-check to evaluate this prototype against the manual baseline.
Separate measured results from assumptions and proposed tests.
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
