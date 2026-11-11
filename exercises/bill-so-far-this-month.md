# Bill so far this month: seven-minute exercise

Use this guided exercise to practise moving from a story to a scored, one-slice plan. Work from observable behaviour and leave unanswered business decisions visible.

## Story

> As a customer, I want to see my bill so far this month, so I'm not surprised at the end of the billing cycle.

## Your four steps

1. Write three acceptance criteria in Given, When, Then.
2. Add two constraints and two non-goals.
3. Slice the story into PR-sized pieces using the [slicing guide](../docs/slicing-guide.md).
4. Run `/plan` on slice 1 and score it with the [rubric](../docs/plan-review-rubric.md).

Use the [spec template](../docs/specs/TEMPLATE.md) if you need a structure.

## Hint

The interesting decisions hide in the edges: estimated reads, missing days, time zones at the end of the month, and whether the amount includes GST.

## Facilitator timing

- **0:00 to 1:00:** brief the task and post the story, template and rubric in the chat.
- **1:00 to 6:00:** work time, with a 2-minute warning.
- **6:00 to 7:00:** debrief.

## Debrief questions

- What was your hardest acceptance criterion?
- Which non-goal did you need?
- What did your plan score, and why?

## Facilitator sample

<details>
<summary>Show one possible answer, not the answer</summary>

### Acceptance criteria

- **AC-1:** Given complete daily usage through 10 May and an amount of $42.35 including GST in the account's time zone, When the customer views bill so far, Then it shows $42.35 for 1 to 10 May and marks it as including GST.
- **AC-2:** Given the latest daily read is missing and an approved estimate is available, When the customer views bill so far, Then the amount includes the estimate and identifies the estimated day.
- **AC-3:** Given a missing day has no actual read or approved estimate, When the customer views bill so far, Then no amount is shown and the missing period is identified.

### Constraints

- Use the existing billing calculation rather than creating a second calculation. Source: applicable pricing ADR.
- Apply the account's existing time-zone rule at the billing boundary. Source: nearest `AGENTS.md` or path rule.

### Non-goals

- No end-of-cycle bill forecast.
- No change to bill generation, payment or stored bills.

### Slices

1. **Complete reads show bill so far:** AC-1; calculation, read path and tests; ships on its own.
2. **An approved estimate fills one missing day:** AC-2; estimate handling and tests; ships after slice 1.
3. **An unfillable gap shows no amount:** AC-3; missing-data behaviour and tests; ships after slice 1.

### Plan review

A plan for slice 1 should name the real calculation, caller and test files in the exercise repo. Score it with all six criteria; approve only at 10 or more out of 12 with no zeros.

</details>