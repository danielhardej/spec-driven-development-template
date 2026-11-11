# Feed-in credit plan v2: slice 1

This illustrative plan is the tightened response to the v1 feedback. It is approved for planning evidence only; stop before writing code.

## 1. Summary and slice (Sliced)

- **Story:** [Feed-in credit specification](spec.md)
- **Slice:** 1 of 3
- **Behaviour:** Quote API returns the credit.
- **Why this slice stands alone:** The quote can return and verify the calculated credit before validation and preview behaviour are added.

## 2. Criteria covered (Traceable)

| Criterion | Behaviour in this slice |
| --- | --- |
| AC-1 | A 120 kWh export at 5c/kWh with a $10.00 usage charge produces a $6.00 credit line. |
| AC-2 | A missing `exportKwh` preserves today's quote and existing callers. |
| AC-5 | A credit larger than the usage charge is capped at that charge. |

## 3. File impact map (Grounded)

**Files that change**

| File and symbol | Change | Why |
| --- | --- | --- |
| `packages/domain/src/calculateTariff.ts` · `calculateTariff` | Accept optional export input, calculate the credit from plan configuration, round it to the nearest cent and cap it at the usage charge. | AC-1, AC-2, AC-5 |
| `packages/domain/src/calculateTariff.test.ts` | Add calculation, compatibility and cap cases. | AC-1, AC-2, AC-5 |
| `services/billing/routes/quote.ts` · quote route | Pass optional `exportKwh` to the domain without changing existing response fields. | AC-1, AC-2, AC-5 |
| `services/billing/routes/quote.test.ts` | Verify the route response for the three covered criteria. | AC-1, AC-2, AC-5 |

**Files that depend on what changes**

| Caller | Classification | Treatment |
| --- | --- | --- |
| `services/billing/routes/quote.ts` | Edit in this slice | Pass optional `exportKwh` through to `calculateTariff`. |
| `web/src/tariffPreview.ts` | Later slice | Keep unchanged until slice 3 adds the preview line. |
| `services/billing/src/billingRun.ts` | Protect | Make the export input optional so this caller compiles and behaves unchanged under AC-2. |

**New files, including tests:** none; the co-located Vitest files above change.

**Files that must not change**

- `services/billing/src/billingRun.ts` and its current behaviour and tests.
- `web/src/tariffPreview.ts` and `web/src/tariffPreview.test.ts` until slice 3.
- `generated/`.

## 4. Constraints applied (Constrained)

| Constraint | Source | Effect on this plan |
| --- | --- | --- |
| The domain stays pure, with no I/O. | Root `AGENTS.md` | Calculate, round and cap in `calculateTariff` using supplied values only. |
| Validate input with zod at the edge. | API path rule under `.github/instructions/NAME.instructions.md` | Leave negative-input validation to slice 2 in the quote route. |
| Errors are RFC 7807 problem details. | API path rule under `.github/instructions/NAME.instructions.md` | Slice 1 adds no new error path; slice 2 owns AC-3. |
| Never log NMIs or customer PII. | Brief at `.github/copilot-instructions.md` | Add no customer logging. |

## 5. Fence (Bounded)

**In scope**

- `packages/domain/src/calculateTariff.ts` and `packages/domain/src/calculateTariff.test.ts`.
- `services/billing/routes/quote.ts` and `services/billing/routes/quote.test.ts`.

**Ask first**

- `services/billing/src/billingRun.ts`.
- Any new dependency.
- Any change to existing response fields.

**Never**

- `generated/`.
- `infra/`.
- Secrets.
- Logging NMIs or customer PII.

## 6. Steps (Traceable, Verifiable)

1. **Add the optional, capped domain calculation.**
   - Files: `packages/domain/src/calculateTariff.ts` · `calculateTariff`; `packages/domain/src/calculateTariff.test.ts`
   - Criteria: AC-1, AC-2, AC-5
   - Test: `calculateTariff.test.ts` proves 120 kWh × 5c/kWh = $6.00 with a $10.00 usage charge, no export preserves today's result, and a larger credit is capped at the usage charge.
   - Review point: stop for human diff review after this domain step.
2. **Pass optional export input through the quote route.**
   - Files: `services/billing/routes/quote.ts` · quote route; `services/billing/routes/quote.test.ts`
   - Criteria: AC-1, AC-2, AC-5
   - Test: `quote.test.ts` proves the credit response, unchanged response when export is absent, and the capped credit without changing existing response fields.

## 7. Stop conditions and definition of done (Bounded, Verifiable)

**Stop and ask when**

- A step needs a file outside the fence.
- `services/billing/src/billingRun.ts` would need to change rather than compile and behave unchanged.
- A new dependency or change to an existing response field appears necessary.

**Stop for review when**

- The domain step is complete.
- Slice 1 is complete, before any work on slice 2 or 3.

**Done means**

- `npm run verify` passes.
- AC-1, AC-2 and AC-5 each have passing tests in the named files.
- Protected callers, later-slice files and `generated/` are unchanged.

## 8. Open decisions and risks

| Decision or risk | Owner | Required action |
| --- | --- | --- |
| No open business decisions for slice 1; the spec records their answers. | Product owner | Keep those answers unchanged. |
| An optional domain input could affect existing callers. | Implementer | Preserve the optional default, protect `billingRun.ts`, and confirm with `npm run verify`. |

## Rubric score

| Criterion | Score | Evidence |
| --- | ---: | --- |
| Traceable | 2 | Both steps name AC-1, AC-2 and AC-5 and their proving tests. |
| Grounded | 2 | It names the changed symbols, co-located tests and all three supplied callers. |
| Constrained | 2 | It applies the brief, API path rule and root AGENTS.md to concrete decisions. |
| Bounded | 2 | In scope, Ask first, Never, protected files and stop conditions are explicit. |
| Verifiable | 2 | Each step names its test, and done requires `npm run verify`. |
| Sliced | 2 | It plans slice 1 only and names later behaviour without planning it. |
| **Total** | **12/12** | **No zeros.** |

**Red flags:** none.

**Decision:** Approved. Stop before code; tests-first implementation is Module 3.