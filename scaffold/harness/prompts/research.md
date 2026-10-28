# Research codebase (ACE)

**Research only.** Do not edit application code. Do not rewrite the spec.

## Preconditions

- Linked spec under `docs/specs/` (or explicit `waiver: no-spec`)
- Or: human named a bug/issue with acceptance inline

## Goal

Map *how the system works today* so a wrong assumption is caught before the plan.

## Method

1. Prefer a fresh subagent/explore task for search; return a structured summary.
2. Name dual/legacy paths, naming traps, tests that give false confidence.
3. Tie findings back to spec acceptance (which criteria touch which code).

## Output

`thoughts/shared/research/YYYY-MM-DD_HH-MM_<slug>.md`:

```markdown
# Research: <title>

## Spec / question
Link + restated acceptance

## Relevant files
- path — why

## How it works today
…

## Likely root cause / approach options
…

## Open questions
…

## Suggested verification after change
- <exact project test command>
```

Stop for human review (`harness/checklists/research-review.md`).
