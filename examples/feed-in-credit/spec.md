# Feed-in credit specification

This illustrative spec defines the feed-in credit story for the fictional meter-platform repository. In meter-platform, it lives at `docs/specs/feed-in-credit.md`.

| Story link | Owner | Status | Last updated |
| --- | --- | --- | --- |
| Illustrative feed-in credit story | Product owner | Planned | 2026-11-11 |

## Story

As a solar customer, I want my quote to show a feed-in credit for the energy I export, so that I can compare plans fairly.

## Acceptance criteria

- **AC-1:** Given `exportKwh = 120`, a feed-in rate of 5c/kWh and a usage charge of $10.00, When a quote is calculated, Then it shows a $6.00 credit as its own line.
- **AC-2:** Given no `exportKwh`, When a quote is calculated, Then it matches today's quote.
- **AC-3:** Given `exportKwh` is negative, When I POST `/quotes`, Then it returns 400 with problem details.
- **AC-4:** Given a quote that includes a feed-in credit, When the tariff preview is shown, Then the credit appears as its own line.
- **AC-5 (added after the open questions were answered):** Given a feed-in credit larger than the usage charge, When a quote is calculated, Then the credit is capped at the usage charge.

## Constraints

| Constraint | Source |
| --- | --- |
| The domain stays pure, with no I/O. | Root `AGENTS.md` |
| Validate input with zod at the edge. | API path rule under `.github/instructions/NAME.instructions.md` |
| Errors are RFC 7807 problem details. | API path rule under `.github/instructions/NAME.instructions.md` |
| Never log NMIs or customer PII. | Brief at `.github/copilot-instructions.md` |

## Scope and non-goals

**In scope:** quote calculation and response, negative export validation, and the tariff preview credit line.

**Non-goals:** no change to billing runs or real bills; no database changes; `generated/` is untouched; no redesign of the preview.

## Open questions

| Question | Owner | Answer | Decided on |
| --- | --- | --- | --- |
| Where does the feed-in rate come from, the plan or the request? | Product owner | The tariff plan configuration. | Before planning |
| Can the credit exceed the usage charge? | Product owner | No: it is capped (AC-5). | Before planning |
| Who signs off rounding? | Pricing owner | The pricing owner; round the credit to the nearest cent. | Before planning |
| Does GST apply to the credit? | Product owner | Out of scope for this story: GST handling is unchanged, and it is raised as a follow-up. | Before planning |

## Verification

| Criterion | Test or check |
| --- | --- |
| AC-1, AC-2, AC-5 | Co-located Vitest `packages/domain/src/calculateTariff.test.ts` and `services/billing/routes/quote.test.ts` |
| AC-3 | Co-located Vitest `services/billing/routes/quote.test.ts` |
| AC-4 | Co-located Vitest `web/src/tariffPreview.test.ts` |
| Repo | `npm run verify` |

## Slices

| Slice | Behaviour (one sentence) | Covers | PR |
| --- | --- | --- | --- |
| 1 | Quote API returns the credit. | AC-1, AC-2, AC-5 | PR 1 |
| 2 | Bad export input is rejected. | AC-3 | PR 2 |
| 3 | Preview shows the credit line. | AC-4 | PR 3 |

## Ready for /plan

- [x] Every criterion is testable.
- [x] At least one unhappy path is included.
- [x] Constraints are referenced.
- [x] Non-goals are listed.
- [x] Open questions are answered or owned.
- [x] Slices are named.
- [x] Could a new team member build the right thing from this page without asking you anything?