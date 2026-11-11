# 02 Check repo context

Check that the story will receive the right repository instructions before planning. Use this after you know the likely paths and before you approve the spec.

## Prompt

```text
For [STORY], inspect [LIKELY_PATHS].

Which instruction files, AGENTS.md files and ADRs apply to the paths this story touches?

Return a table with the instruction or decision path, the paths it applies to, and the constraint it contributes. Confirm whether you found:
- the brief at .github/copilot-instructions.md;
- the right path rule under .github/instructions/NAME.instructions.md, including its applyTo globs;
- the nearest AGENTS.md in the directory tree; and
- any applicable ADRs.

Reference the files; do not copy their full contents. If any expected context is missing or does not reach [LIKELY_PATHS], identify the gap and stop before planning.
```

## What good output looks like

It lists the brief, the right path rule and the nearest AGENTS.md for each affected path. If one is absent, it makes the Module 1 context gap explicit instead of guessing a rule.

## Follow-ups

- `Show which [PATH] is not covered by the expected path rule.`
- `What repo-context gap must we fix before this spec is Ready for plan?`