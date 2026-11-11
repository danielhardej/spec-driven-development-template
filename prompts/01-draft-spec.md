# 01 Draft a spec

Draft what done looks like without choosing how to implement it. Use this when a story needs an approved spec before planning.

## Prompt

```text
Draft a spec for [STORY] using docs/specs/TEMPLATE.md.

Include:
- Given / When / Then acceptance criteria with concrete values, one observable behaviour per criterion and at least one unhappy path.
- Constraints by reference to the instruction files and ADRs that apply to the paths this story touches. Do not repeat their content.
- Clear in-scope behaviour and non-goals.
- Open business questions that you must not guess.
- A separate list of everything that remains ambiguous.

Describe behaviour, not implementation. Do not write code, choose files or make implementation decisions. Ask before filling any business decision that is not stated in [STORY].
```

## What good output looks like

The criteria are observable and use concrete examples. Constraints name their source, non-goals close obvious scope gaps, and unanswered business decisions remain visible.

## Follow-ups

- `Which open questions block spec approval, and who should own each one?`
- `Revise [AC-N] so one test can prove it without prescribing implementation.`