# Feed-in credit plan v1

This illustrative first plan is deliberately too ambitious. Use its score to practise sending back a plan that looks detailed but is not bounded or sliced.

## 1. Summary and slice (Sliced)

- **Story:** [Feed-in credit specification](spec.md)
- **Slice:** All three slices in one plan and one PR.
- **Behaviour:** Calculate a feed-in credit, reject bad export input and show the credit in the preview.
- **Why this slice stands alone:** It delivers the whole story at once.

## 2. Criteria covered (Traceable)

| Criterion | Behaviour in this plan |
| --- | --- |
| AC-1 | A 120 kWh export at 5c/kWh produces a $6.00 credit line. |
| AC-2 | A missing `exportKwh` preserves today's quote. |
| AC-3 | A negative `exportKwh` returns 400 with problem details. |
| AC-4 | The tariff preview shows the credit line. |
| AC-5 | The credit is capped at the usage charge. |

## 3. File impact map (Grounded)

**Files that change**

| File and symbol | Change | Why |
| --- | --- | --- |
| `packages/domain/src/calculateTariff.ts` · `calculateTariff` | Calculate and cap the export credit. | AC-1, AC-2, AC-5 |
| `packages/domain/src/calculateTariff.test.ts` | Add credit, compatibility and cap cases. | AC-1, AC-2, AC-5 |
| `services/billing/routes/quote.ts` · quote route | Pass export input and reject negative values. | AC-1, AC-2, AC-3, AC-5 |
| `services/billing/routes/quote.test.ts` | Add response and validation cases. | AC-1, AC-2, AC-3, AC-5 |
| `services/billing/src/billingRun.ts` | Update the caller for the changed domain function. | AC-2 |
| `web/src/tariffPreview.ts` | Render the credit line. | AC-4 |
| `web/src/tariffPreview.test.ts` | Add the preview case. | AC-4 |

**Files that depend on what changes**

| Caller | Classification | Treatment |
| --- | --- | --- |
| `services/billing/routes/quote.ts` | Edit | Complete all API work now. |
| `web/src/tariffPreview.ts` | Edit | Complete the UI work now. |
| `services/billing/src/billingRun.ts` | Edit | Change the real-bill caller in this PR. |

**New files, including tests:** none.

**Files that must not change:** `generated/`.

## 4. Constraints applied (Constrained)

| Constraint | Source | Effect on this plan |
| --- | --- | --- |
| Keep the domain pure. | Root `AGENTS.md` | Calculate the credit in the domain function. |
| Validate with zod and return problem details. | API path rule under `.github/instructions/NAME.instructions.md` | Validate in the quote route. |
| Never log NMIs or customer PII. | `.github/copilot-instructions.md` | Add no customer logging. |

## 5. Fence (Bounded)

**In scope:** all domain, quote API, billing run and preview changes needed for the story.

**Ask first:** a new dependency or a change to an existing response field.

**Never:** `generated/`, `infra/`, secrets or logging NMIs.

## 6. Steps (Traceable, Verifiable)

1. **Add the credit calculation and update its billing caller.**
   - Files: `packages/domain/src/calculateTariff.ts`, `packages/domain/src/calculateTariff.test.ts`, `services/billing/src/billingRun.ts`
   - Criteria: AC-1, AC-2, AC-5
   - Test: `calculateTariff.test.ts` covers $6.00, missing export and the cap; `npm run verify` checks the billing caller.
2. **Update the quote API and validation.**
   - Files: `services/billing/routes/quote.ts`, `services/billing/routes/quote.test.ts`
   - Criteria: AC-1, AC-2, AC-3, AC-5
   - Test: `quote.test.ts` covers the credit response, compatibility, cap and negative-input problem details.
3. **Show the credit in the tariff preview.**
   - Files: `web/src/tariffPreview.ts`, `web/src/tariffPreview.test.ts`
   - Criterion: AC-4
   - Test: `tariffPreview.test.ts` covers the separate credit line.

## 7. Stop conditions and definition of done (Bounded, Verifiable)

No stop conditions or human review points are provided. Done means `npm run verify` passes.

## 8. Open decisions and risks

No open decisions or risks are listed.

## Rubric score

| Criterion | Score | Evidence |
| --- | ---: | --- |
| Traceable | 2 | Every step names its criteria. |
| Grounded | 1 | It names real files and tests, but treats every caller as an edit and identifies nothing to protect. |
| Constrained | 1 | It references repo rules but contradicts the billing-run non-goal. |
| Bounded | 0 | It puts a protected non-goal in scope and gives no stop conditions. |
| Verifiable | 2 | Every step names a test or repo check. |
| Sliced | 0 | It plans all three behaviours and later slices in one PR. |
| **Total** | **6/12** | **Below 10 and contains zeros.** |

**Red flags:** touches a non-goal; changes a shared function without a protected-caller classification; plans later slices in detail; has no stop conditions.

**Decision:** Send it back. Plan slice 1 only, protect `services/billing/src/billingRun.ts`, and stop for review after the domain step.