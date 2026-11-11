# Story specification

<!-- Use this page to agree what done looks like before you plan implementation. Keep a filled-in copy to one printed page and update it as you learn. -->

| Story link | Owner | Status | Last updated |
| --- | --- | --- | --- |
| [Issue or story URL] | [Name or role] | Draft | [YYYY-MM-DD] |

<!-- Status must be one of: Draft, Ready for plan, Planned, Done. -->

## Story

As a [person or role], I want [capability], so that [outcome].

## Acceptance criteria

<!--
Each criterion becomes a test. Make it observable: a test or reviewer must be able to see it.
Use one behaviour per criterion and concrete values. Always include the unhappy path.
Describe behaviour, not implementation. "Shows a credit line" is a criterion;
"adds a field to the result type" is a plan decision.

Weak: "Handles bad input"
Strong: "Given a negative export, When I POST /quotes, Then 400 with problem details"
-->

- **AC-1:** Given [context], When [action], Then [observable result].
- **AC-2:** Given [unhappy-path context], When [action], Then [observable result].

## Constraints

<!--
Reference the brief (.github/copilot-instructions.md), path rules
(.github/instructions/*.instructions.md), the nearest AGENTS.md and ADRs. Do not repeat them.
A constraint that is not written down anywhere is a gap in your repo context, not just in this spec.
-->

| Constraint | Source |
| --- | --- |
| [Constraint that applies] | [File and section] |

## Scope and non-goals

<!-- If it is not excluded, an agent may treat it as in scope. -->

**In scope**

- [Behaviour or outcome included]

**Non-goals**

- [Behaviour, system or artefact that must not change]

## Open questions

<!-- These are business decisions. Answer them before planning, or the agent will answer them for you. -->

| Question | Owner | Answer | Decided on |
| --- | --- | --- | --- |
| [Decision the agent must not guess] | [Name or role] | [Answer or Pending] | [YYYY-MM-DD or Pending] |

## Verification

<!-- Map every criterion to a test or check. Add repo-level checks such as your verify script. -->

| Criterion | Test or check |
| --- | --- |
| AC-1 | [Test or observable check] |
| Repo | [Repo-level verification command or check] |

## Slices

<!-- Slice by behaviour. See the [slicing guide](../slicing-guide.md). -->

| Slice | Behaviour (one sentence) | Covers | PR |
| --- | --- | --- | --- |
| 1 | [Independently shippable behaviour] | [AC-1] | [Link or Pending] |

## Ready for /plan

- [ ] Every criterion is testable.
- [ ] At least one unhappy path is included.
- [ ] Constraints are referenced.
- [ ] Non-goals are listed.
- [ ] Open questions are answered or owned.
- [ ] Slices are named.
- [ ] Could a new team member build the right thing from this page without asking you anything?

<!-- Once this checklist is complete, set the status to Ready for plan and use the [plan format](../plan-format.md). -->