# 03 Slice a story

Split an approved story into behaviours that can ship and be reviewed independently. Use this before planning when the story needs more than one PR.

## Prompt

```text
Propose PR-sized slices for [SPEC_PATH]. Slice by behaviour, not by technical layer.

For each slice, provide:
- one sentence describing the observable behaviour;
- the acceptance criteria it covers;
- the files and tests it is expected to touch; and
- whether it can ship on its own.

Order the slices by dependency and learning value. Flag any slice that spans two services, cannot ship independently or cannot be said in one sentence. Split flagged slices again. Name later slices, but do not plan their implementation in detail.
```

## What good output looks like

Each slice is one sentence, covers named criteria, includes its tests and produces independently reviewable behaviour. It avoids domain-only, API-only or UI-only setup slices that cannot ship.

## Follow-ups

- `Split [SLICE_NUMBER] again so it stays within one service.`
- `Which slice gives us the earliest end-to-end evidence?`