# 08 Draft a PR description

Turn an approved plan and completed slice into a reviewable PR description. Use this after implementation and verification, before requesting review.

## Prompt

```text
Draft the PR description for [SLICE_NUMBER] from [APPROVED_PLAN] and [SPEC_PATH] using .github/pull_request_template.md.

Include:
- links to the story and spec;
- the slice number, total and one-sentence behaviour;
- every criterion covered by this slice, mapped to the test that proves it and its actual result;
- the approved plan inside the collapsed details block;
- the approved plan score out of 12 and confirmation that it has no zeros;
- every file changed outside the agreed fence, with who approved it, or "None";
- confirmation that no non-goal was touched; and
- the actual result of the repo's verify command.

Do not claim a test or check that was not run. Do not include criteria assigned to another slice. Preserve the reviewer line from the template.
```

## What good output looks like

The reviewer can compare the diff with the approved behaviour, see evidence for every criterion, and identify any approved fence exception without opening another artefact.

## Follow-ups

- `Check that this PR covers no criterion assigned to another slice.`
- `List any changed file that the approved plan did not name.`