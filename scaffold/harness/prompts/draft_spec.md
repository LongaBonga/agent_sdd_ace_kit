# Draft / update spec (SDD)

You are writing a **durable spec**, not code and not a session plan.

## Goal

Capture *what* and *why* so acceptance is reviewable before research/plan.

## Output

Create or update a file under `docs/specs/` using `docs/specs/_TEMPLATE.md`.

Suggested name: `docs/specs/YYYY-MM-DD_<slug>.md`

## Rules

1. Clear goals, non-goals, and checklist acceptance.
2. Prefer precise, testable acceptance over prose.
3. Do not invent large API surfaces the human did not ask for — mark open questions.
4. Do **not** edit application code.
5. Stop and ask for human approval (`Status: approved`) before research/plan
   unless the human said "draft then continue".

## Afterward

Brownfield / non-trivial → `/research_codebase` (or skill) with link to this spec.  
Greenfield empty tree → may go to `/create_plan` with research waived.
