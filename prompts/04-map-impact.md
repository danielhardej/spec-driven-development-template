# 04 Map file impact

Find the callers and protected behaviour around a proposed symbol change. Use this before writing steps for a slice that changes shared code.

## Prompt

```text
Show me the incoming calls for [SYMBOL], then propose the change required by [SLICE_NUMBER] in [SPEC_PATH].

Classify every caller as:
- edit in this slice;
- later slice; or
- protect.

For each caller, name its file and symbol, explain the classification, and state the expected change or unchanged behaviour. Also list:
- files and tests that must be created;
- existing files and tests that change; and
- files that must not change.

Use the language server for incoming calls. Do not substitute a text search when .github/lsp.json provides the language server. Do not write code.
```

With `.github/lsp.json` in place, Copilot CLI gets callers from the language server, not a text search.

## What good output looks like

Every incoming caller has one classification. Shared callers are not hidden under "anything else", test locations are named, and protected files have an explicit unchanged behaviour.

## Follow-ups

- `Why is [CALLER] classified as protect rather than edit?`
- `Add [FILE] to files that must not change and preserve its current tests.`