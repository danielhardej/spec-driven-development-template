# 06 Score a plan

Assess whether a plan is ready for human approval. Use this after the plan is complete and whenever feedback changes it.

## Prompt

```text
Score [PLAN] against docs/plan-review-rubric.md.

For each criterion — Traceable, Grounded, Constrained, Bounded, Verifiable and Sliced — give:
- a score of 0, 1 or 2; and
- one line of evidence from the plan.

Then give:
- the total out of 12;
- every red flag found; and
- a recommendation.

Recommend approval only at 10 or more with no zeros. Otherwise, write the specific feedback to send back. Do not improve the score by assuming details that are absent from [PLAN]. The agent's score is a helper; the human owns the decision.
```

## What good output looks like

All six scores cite visible evidence and add up correctly. The recommendation follows the threshold and treats any red flag as a reason to send the plan back.

## Follow-ups

- `Turn the weakest criterion into one specific feedback reply.`
- `Rescore [PLAN] after the feedback, without carrying forward evidence that is no longer present.`