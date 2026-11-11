# Plan mode on each surface

Use this guide to start planning on the Copilot surface available to you. Keep the same approved spec, one-slice scope and [plan format](plan-format.md) on every surface.

| Surface | How to start | What happens next |
| --- | --- | --- |
| Copilot CLI | Press Shift+Tab to cycle into plan mode, or type `/plan`. | Copilot analyses the request, asks clarifying questions, and builds a plan before writing code. |
| VS Code | Type `/plan`, or pick Plan from the agents dropdown. | The Plan agent researches the project, asks questions, and presents files, steps and verification without changing code. |
| JetBrains IDEs, Eclipse and Xcode | Choose Plan from the agents dropdown. | Review the plan, open it as Markdown or hand it to agent mode. |
| GitHub.com cloud agent | Give it a well-scoped issue as its prompt. | It can research the repository, create a plan and iterate on a branch before you open a PR. |
| Spec Kit | Use its specify, plan, tasks, implement and converge phases. | Each phase produces a Markdown artefact, with optional quality gates. |

## Copilot CLI

Press Shift+Tab to cycle into plan mode, or type `/plan`. In plan mode, Copilot analyses the request, asks clarifying questions about scope and requirements, and builds a plan before writing any code. Review the plan, then tell it to implement.

## VS Code

Type `/plan`, or pick Plan from the agents dropdown. The Plan agent researches the project, asks clarifying questions and presents a plan with steps, relevant files and verification steps. It makes no code changes until you approve.

In the Review Plan card, Open Full Plan opens the plan as Markdown so you can edit it or comment inline. Submit Feedback sends your comments without approving. Pending feedback disables approval until you submit or clear it. Review Scope, Project fit, Decisions and Verification.

Approving a plan is a separate decision from approving the tools the agent then runs, so check your permissions before you implement. Module 4 covers this.

## JetBrains IDEs, Eclipse and Xcode

Choose Plan from the agents dropdown. Start Implementation hands the plan to agent mode. Open in Editor writes the plan as Markdown you can save.

Plan mode is not currently available in Visual Studio. Visual Studio users should use Copilot CLI or VS Code for plan mode.

## GitHub.com cloud agent

The cloud agent can research a repository, create an implementation plan and iterate on a branch before you open a pull request. It works best with well-scoped issues: a clear description, complete acceptance criteria and directions about which files need to change. Treat the issue as a prompt.

## Spec Kit

Spec Kit is an open-source GitHub project. Its core process is specify → plan → tasks → implement → converge, with optional quality gates: clarify, checklist and analyze. Each phase produces a Markdown artefact. Specify covers the what and why; plan covers the tech stack and architecture.

Its documentation writes commands as `/speckit.specify`, `/speckit.plan` and so on. In GitHub Copilot's default skills mode, they are `/speckit-specify`, `/speckit-plan` and so on. Use `/plan` for most stories; reach for Spec Kit when a feature needs the extra structure.

## Model choice

Plan with a capable reasoning model, then implement the reviewed, well-scoped plan with a lower-cost model. Compare total cost, because retries and rework can outweigh the savings.

## Source links

- [Copilot CLI](https://docs.github.com/en/copilot/concepts/copilot-surfaces/copilot-cli)
- [Use plan mode in an IDE](https://docs.github.com/en/copilot/how-tos/copilot-in-your-ide/use-copilot-agents/use-plan-mode)
- [VS Code planning](https://code.visualstudio.com/docs/agents/run/planning)
- [Get the best results from the cloud agent](https://docs.github.com/copilot/tutorials/cloud-agent/get-the-best-results)
- [Issue form syntax](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/syntax-for-issue-forms)
- [Spec Kit](https://github.github.com/spec-kit/)
- [Agentic spec-driven development](https://github.github.com/spec-kit/reference/agentic-sdd.html)