# Plan format

Use this format after the spec is approved and you are planning one slice. It makes the plan reviewable against the [plan review rubric](plan-review-rubric.md).

## What a reviewable plan contains

### 1. Summary and slice (Sliced)

- **Story:** [Story or spec link]
- **Slice:** [Number of total]
- **Behaviour:** [One sentence describing the behaviour delivered]
- **Why this slice stands alone:** [How it can ship and be verified on its own]

### 2. Criteria covered (Traceable)

| Criterion | Behaviour in this slice |
| --- | --- |
| [AC-N] | [Observable result] |

### 3. File impact map (Grounded)

**Files that change**

| File and symbol | Change | Why |
| --- | --- | --- |
| [path and symbol] | [Specific change] | [Criterion served] |

**Files that depend on what changes**

<!-- Use incoming calls to find callers. Mark each caller as edit, later slice or protect. -->

| Caller | Classification | Treatment |
| --- | --- | --- |
| [path and symbol] | [Edit / Later slice / Protect] | [Expected action or unchanged behaviour] |

**New files, including tests**

- [Path and purpose]

**Files that must not change**

- [Path and protected behaviour]

### 4. Constraints applied (Constrained)

| Constraint | Source | Effect on this plan |
| --- | --- | --- |
| [Applicable rule] | [.github/copilot-instructions.md, path rule, nearest AGENTS.md or ADR] | [Planning decision] |

### 5. Fence (Bounded)

**In scope**

- [Allowed file, symbol or behaviour]

**Ask first**

- [Change that needs human approval]

**Never**

- [File, system or behaviour that must not be touched]

### 6. Steps (Traceable, Verifiable)

1. **[Specific outcome]**
   - Files: [Exact paths and symbols]
   - Criterion: [AC-N]
   - Test or check: [Exact test or check that proves the step]

### 7. Stop conditions and definition of done (Bounded, Verifiable)

**Stop and ask when**

- [A file outside the fence is needed or another named condition occurs]

**Stop for review when**

- [Named step or slice boundary]

**Done means**

- [Repo verification passes and every covered criterion has a passing test]

### 8. Open decisions and risks

| Decision or risk | Owner | Required action |
| --- | --- | --- |
| [Unresolved item] | [Name or role] | [Answer before implementation or mitigation] |

A plan that says "and update anything else that needs it" is not a plan yet. Plans are task-specific: put the approved plan in the PR description, never in always-on instruction files.