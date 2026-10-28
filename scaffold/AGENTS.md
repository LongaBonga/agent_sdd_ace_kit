# Agent harness: SDD + ACE

This project uses **Spec-Driven Development** (durable intent) and
**Advanced Context Engineering** (research → plan → implement + compaction)
together.

Talk / essay: https://www.youtube.com/watch?v=IS_y40zY-hc

## Artifact roles

| Artifact | Path | Lifespan | Purpose |
|----------|------|----------|---------|
| Spec | `docs/specs/*.md` | durable | *What* / *why* / acceptance (SDD) |
| Research | `thoughts/shared/research/` | usually ephemeral | *How code works today* (ACE) |
| Plan | `thoughts/shared/plans/` | usually ephemeral | *How we change it* + verify cmds |
| Progress | `thoughts/shared/progress/` | ephemeral | Compaction handoff |

Do **not** duplicate full acceptance into the plan — link the spec section.

## Hard gates

1. **Spec required** before non-trivial work (or explicit waiver in the issue:
   `waiver: no-spec — typo|deps-bump|docs-only`).
2. **Research required** for brownfield / non-trivial changes (map real code paths).
   Skip only when greenfield with no code yet, or human waived.
3. **Plan required** with phased verification commands before implementation.
4. After each implement phase: run the plan's verification; on failure compact the error.
5. Keep context focused (~40–60%). Noise → `/compact_session` (or skill) + fresh chat.
6. Human review order: **spec ≥ research ≥ plan > tests/diff**.

## Commands / skills

| Step | Cursor skill | Claude Code |
|------|--------------|-------------|
| **Entry / route** | `start-change` | `/start_change` |
| Draft / update spec | `draft-spec` | `/draft_spec` |
| Research codebase | `research-codebase` | `/research_codebase` |
| Create plan | `create-plan` | `/create_plan` |
| Implement plan | `implement-plan` | `/implement_plan` |
| Compact session | `compact-session` | `/compact_session` |

Default entry for new work: **`start-change`**. It classifies the change, writes
a route note under `thoughts/shared/progress/`, runs **only the first** step,
then stops for a human gate. It never implements app code.

Canonical prompts: `harness/prompts/`. Keep Cursor and Claude mirrors in sync.

Diagram + toy examples: [docs/workflow.md](docs/workflow.md).

## Flow

```text
start_change → draft_spec (SDD) → research (ACE, brownfield) → create_plan → implement
                    ↑__________________________________________________|
                         update spec if shipped behavior diverged
```

## Verification

Prefer project-native commands (examples):

```bash
# Go
go test ./...

# Node
npm test

# make
make test
```

Put the **exact** commands in each plan phase.
