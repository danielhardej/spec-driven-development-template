# /plan prompt pack

Use these prompts to move from an approved story to a reviewable, one-slice plan. Copy the prompt you need and replace its square-bracket placeholders.

| Prompt | Use it when | Output |
| --- | --- | --- |
| [01 Draft spec](01-draft-spec.md) | The story has not become an approved spec. | Criteria, constraints, non-goals, questions and ambiguities. |
| [02 Check context](02-check-context.md) | You need to confirm which repo instructions apply. | Applicable brief, path rules, AGENTS.md files and ADRs. |
| [03 Slice story](03-slice-story.md) | The approved behaviour is too large for one PR. | Ordered, independently shippable behaviour slices. |
| [04 Map impact](04-map-impact.md) | A shared symbol may affect callers. | Classified callers, new files and protected files. |
| [05 Plan slice](05-plan-slice.md) | One slice is ready for technical planning. | A plan in the repo's required format. |
| [06 Score plan](06-score-plan.md) | A human needs evidence before approval. | Six scores, total, red flags and recommendation. |
| [07 Send it back](07-send-it-back.md) | The plan needs specific corrections. | Ready-made feedback grouped by rubric criterion. |
| [08 PR description](08-pr-description.md) | The plan is approved and the slice is implemented. | A completed PR description with evidence and fence changes. |

See [plan mode on each surface](../docs/plan-mode-surfaces.md) before you start. The pack works in Copilot CLI plan mode, in the Plan agent in VS Code, JetBrains IDEs, Eclipse and Xcode, and on GitHub.com by copy and paste.

For a full conversation, run prompts 01 to 05 in order, then use 06 to support the human approval decision.