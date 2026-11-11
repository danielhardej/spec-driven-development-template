# Plan review rubric

Use this rubric before approving an implementation plan. It gives reviewers shared language for specific, actionable feedback.

## Criteria

1. **Traceable:** every step maps to an acceptance criterion.
2. **Grounded:** names real files and symbols, not generic tasks.
3. **Constrained:** respects the brief, path rules and ADRs.
4. **Bounded:** in scope, out of scope and stop conditions are explicit.
5. **Verifiable:** every step has a test or a check.
6. **Sliced:** small, ordered steps; one PR per slice.

## Scoring descriptors

| Criterion | 0 | 1 | 2 |
| --- | --- | --- | --- |
| Traceable | Steps do not reference acceptance criteria. | Some steps map to criteria, but there are gaps or unmatched criteria. | Every step names its criterion, and every criterion in the slice is covered. |
| Grounded | Uses generic tasks without real paths or symbols. | Names some files, but misses symbols, callers or test locations. | Names the files, symbols, callers and tests affected by the slice. |
| Constrained | Ignores or conflicts with applicable repo rules. | Mentions constraints without showing how they affect the plan. | Identifies the applicable brief, path rules, nearest AGENTS.md and ADRs, then applies them. |
| Bounded | Has no clear fence or stop conditions. | Gives partial scope or a stop point, but leaves room for unapproved work. | States In scope, Ask first and Never, with explicit stop conditions and done. |
| Verifiable | Gives no test or check for the work. | Defers tests to the end or uses broad verification without step-level evidence. | Every step names the test or check that proves its result. |
| Sliced | Plans the whole story or mixes several behaviours in one PR. | Divides the story, but a slice is still broad, layered or cannot ship alone. | Plans one independently shippable behaviour with small, ordered steps and one PR. |

## Decision rule

Approve at **10 or more out of 12 with no zeros**. Otherwise, send it back with specific feedback from [prompt 07](../prompts/07-send-it-back.md). In plan mode, that is just a reply.

The agent's score can help, but the human owns the decision.

## Red flags

Any one of these means send the plan back:

- Generic steps such as "update the backend".
- "And update anything else that needs it".
- Tests left to a final "add tests" step.
- A shared function changing without its callers listed.
- Anything touching a non-goal.
- A new dependency without asking.
- Generated code, infrastructure or secrets in scope.
- Logging customer identifiers such as NMIs, or PII.
- Later slices planned in detail.
- Open questions quietly assumed.
- Task-specific content written into always-on instruction files.
- No stop conditions.

Use shared language. "This plan is grounded but not bounded" beats "looks a bit big".

## How it maps to other review guidance

| VS Code plan review check | Rubric focus |
| --- | --- |
| Scope | Bounded and Sliced |
| Project fit | Grounded and Constrained |
| Decisions | Traceable and Bounded |
| Verification | Verifiable |

Well-scoped GitHub.com cloud agent tasks need a clear description, complete acceptance criteria and directions about which files need to change. In this rubric, those map to Traceable, Grounded and Bounded. See [plan mode on each surface](plan-mode-surfaces.md).

## Copy-paste scorecard

| Criterion | Score (0–2) | Evidence or feedback |
| --- | ---: | --- |
| Traceable |  |  |
| Grounded |  |  |
| Constrained |  |  |
| Bounded |  |  |
| Verifiable |  |  |
| Sliced |  |  |
| **Total** | **/12** | **Approve at 10 or more with no zeros.** |

**Red flags:** [None, or list them]  
**Recommendation:** [Approve / Send it back with specific feedback]