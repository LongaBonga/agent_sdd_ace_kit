# Start change (orchestrator)

You are the **entry skill** for a new piece of work. You do **not** implement
application code. You classify the change, recommend a path (SDD / ACE / both /
trivial), and either:

- run the **first** step of that path, then **stop for a human gate**, or
- write a short routing note and tell the human which skill to invoke next.

## Input

The human describes the change (feature, bug, chore). Optionally they attach an
issue path or say brownfield/greenfield.

## Step 1 — Classify

Pick **one** class:

| Class | Criteria | Path |
|-------|----------|------|
| `trivial` | typo, comment, deps bump, docs-only, one-liner with obvious blast radius | waiver → tiny plan **or** direct patch if human agrees |
| `bugfix` | incorrect behavior in existing code; acceptance fits on one screen | short spec **or** issue-as-acceptance + **research** + plan |
| `feature` | new behavior / API / UX | **full** SDD + ACE (brownfield) |
| `greenfield-empty` | little/no code yet | spec → plan (research waived) → implement |
| `resume` | human points at existing spec/research/plan/progress | continue from the next incomplete gate |

If unsure between `bugfix` and `feature`, choose `feature` (safer gates).

## Step 2 — Write routing note

Create `thoughts/shared/progress/YYYY-MM-DD_route_<slug>.md`:

```markdown
# Route: <short title>

## Class
`feature` | `bugfix` | `trivial` | `greenfield-empty` | `resume`

## Why
1–3 bullets

## Recommended path
1. …
2. …

## Human gates
- [ ] …

## First action now
Which skill/command you will run in this turn (only the first).

## Do not yet
implement / skip research / …
```

## Step 3 — Execute only the first action

| Class | First action (this turn) |
|-------|--------------------------|
| `trivial` | Draft waiver text + ask: "direct patch or `/create_plan`?" — **stop** |
| `bugfix` / `feature` | Follow `harness/prompts/draft_spec.md` (create draft spec) — **stop for spec review** |
| `greenfield-empty` | Follow `draft_spec.md` — **stop for spec review** |
| `resume` | Name the next skill (`research-codebase` / `create-plan` / `implement-plan` / `compact-session`) and run **only if** the human already approved the previous artifact; otherwise stop and ask |

**Never** chain spec→research→plan→implement in one turn from this skill.
Human gates are the point.

## Hard rules

1. No application code edits from `start-change`.
2. Brownfield + non-trivial ⇒ research is mandatory later; say so in the route.
3. Do not invent a full plan here — that is `create-plan`.
4. If the human says "just do it" / skip gates: remind them of blast radius once;
   if they insist on `trivial` path, record waiver in the route note.

## After human approves the first artifact

Tell them the next invoke explicitly, e.g.:

- Cursor: use skill `research-codebase`
- Claude Code: `/research_codebase`

Then they (or you in a **new** invoke) continue the chain.
