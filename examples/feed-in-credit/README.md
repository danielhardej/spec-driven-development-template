# Feed-in credit worked example

This illustrative example shows the two approval gates without implementing code. Use it to replay the Module 2 demonstration in meter-platform, a fictional energy-retail TypeScript monorepo with the `main`, `layered-context` and `with-lsp` branches, Vitest tests and the `npm run verify` repo check.

## The journey

| Artefact | File | Gate |
| --- | --- | --- |
| Approved behaviour | [spec.md](spec.md) | Approve the spec before planning. |
| First plan | [plan-v1.md](plan-v1.md) | Score it and send it back. |
| One-slice plan | [plan-v2-slice-1.md](plan-v2-slice-1.md) | Approve the plan, then stop before code. |
| Planned delivery | [pull-requests.md](pull-requests.md) | Build and verify one PR at a time. |

## Replay the live demo

1. In meter-platform, create a `module-2-demo` branch from `with-lsp`.
2. Add `docs/specs/TEMPLATE.md` from this kit.
3. Open Copilot CLI at the repo root and confirm the TypeScript language server is configured.
4. Press Shift+Tab to enter plan mode.
5. Paste the demo prompt below.
6. Answer its questions with the suggested answers below.
7. Send the feedback prompt.
8. Score the revised plan aloud with the [rubric](../../docs/plan-review-rubric.md).
9. Approve slice 1 and stop before any code. Implementing it tests first is Module 3.

### Demo prompt

```text
Plan this story for meter-platform. Story: As a solar customer, I want my quote to show a feed-in credit for the energy I export, so that I can compare plans fairly. First draft a spec using docs/specs/TEMPLATE.md: Given/When/Then acceptance criteria, constraints, non-goals and open questions. Then propose PR-sized slices and plan slice 1 only: files to change, callers to protect, steps, and the test for each criterion.
```

### Suggested answers

```text
the feed-in rate comes from the plan configuration; the credit can't exceed the usage charge; billing runs are out of scope.
```

### Feedback prompt

```text
Plan slice 1 only. services/billing/src/billingRun.ts is out of scope: keep its behaviour and tests unchanged. Stop for review after the domain step.
```

All repository names, paths and behaviours in this example are illustrative. Do not use real customer data, NMIs or secrets when replaying it.