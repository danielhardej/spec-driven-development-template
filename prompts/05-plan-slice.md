# 05 Plan one slice

Build the technical plan for one approved behaviour slice without writing code. Use this only after the spec, slices and impact map are ready.

## Start plan mode

- Copilot CLI: press Shift+Tab to cycle into plan mode, or type `/plan`.
- VS Code: type `/plan`, or pick Plan from the agents dropdown.
- JetBrains IDEs, Eclipse and Xcode: choose Plan from the agents dropdown.
- GitHub.com cloud agent: give it a well-scoped issue as its prompt.
- Spec Kit: use `/speckit.plan` as documented, or `/speckit-plan` in GitHub Copilot's default skills mode.
- Visual Studio: plan mode is not currently available; use Copilot CLI or VS Code.

## Prompt

```text
Plan slice [SLICE_NUMBER] of [SPEC_PATH] only. Follow docs/plan-format.md exactly.

Ground the plan in the repository:
- map every covered criterion to the steps and tests that prove it;
- name the exact files, symbols, callers and test files involved;
- apply the brief, path rules, nearest AGENTS.md and ADRs by reference;
- define In scope, Ask first and Never;
- classify affected callers as edit, later slice or protect;
- give every numbered step its files, criterion and test or check;
- add stop conditions, a human review point and a definition of done; and
- list unresolved decisions and risks.

Ask before assuming the answer to any open question. Name later slices but do not plan them in detail. Do not write or edit code.
```

## What good output looks like

The result follows all eight sections of [the plan format](../docs/plan-format.md), stays inside one slice, and is specific enough to score without inferring missing files, decisions or tests.

## Follow-ups

- `Show the evidence for classifying [CALLER] as [CLASSIFICATION].`
- `Tighten the fence so [FILE_OR_PATH] requires approval before any change.`