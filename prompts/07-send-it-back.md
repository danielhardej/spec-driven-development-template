# 07 Send a plan back

Give precise feedback tied to the rubric instead of asking for a generally better plan. Use the lines that match the failed criteria or red flags.

## Prompt

```text
Revise [PLAN] using the feedback below. Keep approved decisions unchanged, answer no open business question on my behalf, and do not write code.

Traceable
- Add a test for AC-3.
- Map every step to the acceptance criterion it serves.

Grounded
- Name the files: "update the backend" isn't a step.
- List every incoming caller of [SYMBOL] and classify it as edit, later slice or protect.

Constrained
- Apply [INSTRUCTION_OR_ADR] to the paths in this slice and show the resulting plan decision.
- [FILE] is out of scope: keep its behaviour and tests unchanged.

Bounded
- [FILE] is out of scope: keep its behaviour and tests unchanged.
- Stop for review after the [STEP] step.
- Add stop conditions and a definition of done.

Verifiable
- Add a test for AC-3.
- Give every step the test or check that proves it.

Sliced
- Split this into slices and plan slice 1 only.
- Name later slices without planning them in detail.
```

## What good output looks like

The revised plan fixes the named criterion without widening another part of the scope. It preserves protected files, adds missing evidence and remains a plan for one slice only.

## Follow-ups

- `Rescore the revised plan and cite only evidence now present.`
- `Show exactly how the revised fence prevents [RED_FLAG].`