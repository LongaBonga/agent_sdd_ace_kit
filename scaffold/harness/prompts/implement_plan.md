# Implement plan (ACE)

## Preconditions

- Path to approved plan under `thoughts/shared/plans/`
- Spec still accurate (if not, stop and update spec first)

## Method

1. Execute **one phase at a time**.
2. Run that phase's verification command.
3. On failure: short diagnosis + fix; if plan is wrong, propose amendment — do not silently redesign.
4. Final full test suite for the project.
5. If shipped behavior differs from spec, update `docs/specs/…` status/acceptance.

## Compaction

If context is noisy, write `thoughts/shared/progress/…` and continue in a fresh session.
