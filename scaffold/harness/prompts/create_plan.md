# Create implementation plan (ACE)

**Planning only.** No application code edits.

## Preconditions

- Approved (or explicitly accepted) spec — link it
- Reviewed research for brownfield (or waiver)

## Output

`thoughts/shared/plans/YYYY-MM-DD_<slug>.md`:

```markdown
# Plan: <title>

## Spec
Link + one-line intent. Do not paste full acceptance.

## Research basis
Link + takeaway

## Goal / acceptance (pointers)
- Spec §… → will verify with: `<command>`

## Non-goals
From spec + any extra

## Phases
### Phase 1 — …
- Files:
- Changes:
- Verification:
  ```bash
  <exact command>
  ```

## Risks
…
```

## Rules

1. Every phase has a concrete verification command.
2. Smallest change that satisfies the spec.
3. Stop for human plan review (`harness/checklists/plan-review.md`).
