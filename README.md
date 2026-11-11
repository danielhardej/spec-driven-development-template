# Spec-Driven /plan Delivery Template & Rubric

Turn a user story into a spec, a scored plan and PR-sized slices before any code is written. Use this kit when you want a shared path from a story to verified delivery.

## What's inside

| Take-away | Location or form | What it contains |
| --- | --- | --- |
| 01 Spec template | [docs/specs/TEMPLATE.md](docs/specs/TEMPLATE.md) | Story, criteria, constraints, non-goals and questions. |
| 02 Story issue form | [.github/ISSUE_TEMPLATE/](.github/ISSUE_TEMPLATE/) | Captures spec-ready stories in GitHub Issues. |
| 03 /plan prompt pack | [prompts/](prompts/) | Starter prompts for CLI plan mode and IDE plan agents. |
| 04 Plan review rubric | 6 criteria, 0 to 2 | Score before you approve; red flags included. |
| 05 Slicing guide | one behaviour per PR | How to cut a story into PR-sized slices. |
| 06 Worked example | feed-in credit | Story to spec to plan to three PRs on meter-platform. |

Also included: the [plan format](docs/plan-format.md), the [PR template](.github/pull_request_template.md), [plan mode on each surface](docs/plan-mode-surfaces.md), the [guided exercise](exercises/bill-so-far-this-month.md) and the [30-day champion plan](docs/champion-30-days.md).

## The loop

1. **Story:** capture the need in the user's words.
2. **Spec:** agree what done looks like and why. **Gate: approve the spec.**
3. **Plan:** name the files, steps, constraints and tests. **Gate: approve the plan.**
4. **Build:** implement one approved slice at a time.
5. **Verify:** run the tests and review the diff against the criteria.

This is not waterfall. Keep one page per story, and change the spec as you learn.

## Quick start (about 15 minutes)

1. Copy [docs/specs/TEMPLATE.md](docs/specs/TEMPLATE.md), [.github/ISSUE_TEMPLATE/story.yml](.github/ISSUE_TEMPLATE/story.yml) and [.github/pull_request_template.md](.github/pull_request_template.md) into your repo as individual files. Do not overwrite an existing `.github/` folder or PR template; merge the content instead.
2. Create the `story` and `needs-plan` labels. Labels named by an issue form must already exist.
3. Pick one real story.
4. Work through prompts [01 to 05](prompts/README.md).
5. Score the plan with the [rubric](docs/plan-review-rubric.md).
6. Approve it, or send it back with [prompt 07](prompts/07-send-it-back.md).
7. Put the approved plan in the PR with [prompt 08](prompts/08-pr-description.md).

Prompts 01 to 05 can also run as one plan-mode conversation, like the demo prompt in the [worked example](examples/feed-in-credit/README.md).

## Where things live

Put the spec in the issue or in `docs/specs/` next to the code. Put the approved plan in the PR description. Neither belongs in always-on instruction files: if it is only true for this task, it does not belong in the brief.

## How it builds on Module 1

The spec references the brief at `.github/copilot-instructions.md`, path rules at `.github/instructions/NAME.instructions.md` and the nearest `AGENTS.md` instead of repeating them. The impact map uses incoming calls from the language server configured in `.github/lsp.json`.

## Next in the series

- Module 3 · Agentic TDD & Verification Loops: implement an approved slice tests first.
- Module 4 · Advanced Copilot CLI & Autopilot: back the fence with tool permissions and autopilot seatbelts.
- Module 5 · Safe Parallel Orchestration (`/fleet`).
- Module 6 · Custom Agents, Skills & MCP Tools.

## Contributing

Open an issue or PR with a before-and-after example. Keep templates to one page.

Licensed under the [MIT licence](LICENSE).