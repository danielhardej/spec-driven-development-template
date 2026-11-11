# Slicing guide

Use this guide after the spec is approved and before planning implementation. It helps you turn a story into PR-sized behaviours that can ship and be reviewed independently.

## Principle

Slice by behaviour, not by layer. A slice is one behaviour, its tests and one PR a reviewer can read in one sitting, and it ships on its own.

If you cannot describe a slice in one sentence, or it spans two services, split it again. A small slice means a small plan, a small context and a small diff.

## Behaviour versus layer

For the illustrative feed-in credit story, behaviour slices are:

1. **Quote API returns the credit:** AC-1, AC-2 and AC-5; domain, quote route and tests.
2. **Bad export input is rejected:** AC-3; quote route validation and tests.
3. **Preview shows the credit line:** AC-4; tariff preview and tests.

Layer slices would do all domain work, then all API work, then all UI work. Those slices cannot ship on their own and cannot be tested end to end until the last one lands.

See the completed [feed-in credit example](../examples/feed-in-credit/README.md).

## Common splitting patterns

These are common delivery practices, not Copilot product features.

| Pattern | Illustrative energy-retail example |
| --- | --- |
| Happy path first, then validation and unhappy paths | Return a valid feed-in credit first; reject a negative export in the next slice. |
| One business-rule variation at a time | Add the standard credit calculation, then add the cap at the usage charge. |
| API before UI | Return the credit from the quote API before showing it in the tariff preview. |
| One consumer at a time | Update the quote route while protecting billing runs, then update the preview separately. |
| Read before write | Show an existing tariff value before adding a separate change flow. |
| Defer performance and polish | Deliver the observable quote behaviour before optional optimisation or preview polish. |

## Anti-patterns

- Setup-only slices with no observable behaviour.
- A refactor and a feature in one PR.
- Any slice that touches a non-goal.

## Slicing checklist

- [ ] The slice describes one behaviour in one sentence.
- [ ] It covers named acceptance criteria.
- [ ] It includes the tests for that behaviour.
- [ ] It can ship on its own.
- [ ] It stays within one service, or has been split again.
- [ ] A reviewer can read the PR in one sitting.
- [ ] It does not touch a non-goal.
- [ ] Later slices are named but not planned in detail.

Record the result in the [spec slices table](specs/TEMPLATE.md), then plan one slice with the [plan format](plan-format.md).