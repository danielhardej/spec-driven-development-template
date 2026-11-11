# Feed-in credit pull requests

These three illustrative descriptions show how the story would be delivered one behaviour at a time. Use them as completed examples of the [PR template](../../.github/pull_request_template.md), not as evidence that code was run in this kit.

## PR 1: Quote API returns the credit

### Story and spec

[Feed-in credit specification](spec.md)

### Slice

**1 of 3:** Quote API returns the credit.

### Acceptance criteria → tests

| Criterion | Test | Passing? |
| --- | --- | --- |
| AC-1 | `calculateTariff.test.ts` and `quote.test.ts`: 120 kWh × 5c/kWh produces a $6.00 credit line with a $10.00 usage charge. | Yes (illustrative) |
| AC-2 | `calculateTariff.test.ts` and `quote.test.ts`: no `exportKwh` preserves today's quote. | Yes (illustrative) |
| AC-5 | `calculateTariff.test.ts` and `quote.test.ts`: the credit is capped at the usage charge. | Yes (illustrative) |

### Approved plan

<details>
<summary>Show approved plan</summary>

Plan slice 1 only. Change `calculateTariff` and the quote route, with their co-located Vitest files. Make export input optional so `services/billing/src/billingRun.ts` compiles and behaves unchanged. Protect `generated/`, `infra/`, secrets and existing response fields. Stop after the domain step for review, and stop if any file outside the fence is needed. Done means the three criteria have passing tests and `npm run verify` passes.

</details>

### Plan score

**12/12, no zeros**

### Fence check

Files changed outside the agreed fence: **None**

### Non-goals

- [x] No change to billing runs or real bills.
- [x] No database change.
- [x] `generated/` is untouched.
- [x] No preview redesign.

### Verification

**Command:** `npm run verify`  
**Result:** Pass (illustrative worked-example result)

### Reviewer

Review the diff against the acceptance criteria, not just the code.

## PR 2: Bad export input is rejected

### Story and spec

[Feed-in credit specification](spec.md)

### Slice

**2 of 3:** Bad export input is rejected.

### Acceptance criteria → tests

| Criterion | Test | Passing? |
| --- | --- | --- |
| AC-3 | `quote.test.ts`: negative `exportKwh` returns 400 with RFC 7807 problem details. | Yes (illustrative) |

### Approved plan

<details>
<summary>Show approved plan</summary>

Plan slice 2 only. Change `services/billing/routes/quote.ts` and `services/billing/routes/quote.test.ts`. Validate negative export input with zod at the edge and preserve all valid quote behaviour. Do not change the domain, billing runs, preview, `generated/`, infrastructure, dependencies or secrets. Stop if another file or response-field change is needed. Done means AC-3 has a passing route test and `npm run verify` passes.

</details>

### Plan score

**12/12, no zeros**

### Fence check

Files changed outside the agreed fence: **None**

### Non-goals

- [x] No change to billing runs or real bills.
- [x] No database change.
- [x] `generated/` is untouched.
- [x] No preview redesign.

### Verification

**Command:** `npm run verify`  
**Result:** Pass (illustrative worked-example result)

### Reviewer

Review the diff against the acceptance criteria, not just the code.

## PR 3: Preview shows the credit line

### Story and spec

[Feed-in credit specification](spec.md)

### Slice

**3 of 3:** Preview shows the credit line.

### Acceptance criteria → tests

| Criterion | Test | Passing? |
| --- | --- | --- |
| AC-4 | `tariffPreview.test.ts`: a quote with a feed-in credit shows the credit as its own line. | Yes (illustrative) |

### Approved plan

<details>
<summary>Show approved plan</summary>

Plan slice 3 only. Change `web/src/tariffPreview.ts` and `web/src/tariffPreview.test.ts` to show the existing credit as its own line. Do not redesign the preview or change quote calculation, validation, billing runs, `generated/`, infrastructure, dependencies or secrets. Stop if the API shape must change. Done means AC-4 has a passing preview test and `npm run verify` passes.

</details>

### Plan score

**12/12, no zeros**

### Fence check

Files changed outside the agreed fence: **None**

### Non-goals

- [x] No change to billing runs or real bills.
- [x] No database change.
- [x] `generated/` is untouched.
- [x] No preview redesign.

### Verification

**Command:** `npm run verify`  
**Result:** Pass (illustrative worked-example result)

### Reviewer

Review the diff against the acceptance criteria, not just the code.