# ace-sdd-kit

Переносимый harness: **SDD** (долгоживущие спеки) + **ACE** (research → plan → implement + compaction).

Два режима:

| Команда | Зачем |
|---------|--------|
| `ace-sdd install <dir>` | Встроить в **существующий brownfield**-репозиторий |
| `ace-sdd init <path>` | Создать **greenfield**-проект с harness (+ опционально Go stub) |

Основано на [Advanced Context Engineering](https://www.youtube.com/watch?v=IS_y40zY-hc) + Spec-Driven Development.

## Установка CLI

```bash
# из клона
export PATH="$PATH:/Users/i.dobryaev/repo/ace-sdd-kit/bin"
# или
alias ace-sdd=/Users/i.dobryaev/repo/ace-sdd-kit/bin/ace-sdd
```

## Brownfield

```bash
ace-sdd install /path/to/existing-repo
# конфликт AGENTS.md → см. docs/adoption.md (--merge-agents / --force)
```

## Greenfield

```bash
ace-sdd init ~/repo/my-app --lang go --module github.com/you/my-app
cd ~/repo/my-app && make test
```

Только harness без кода:

```bash
ace-sdd init ~/repo/my-app --lang none
```

## Что кладётся в целевой репо

```text
AGENTS.md          # gates: spec → research → plan → implement
CLAUDE.md
ACE-SDD.md
docs/specs/        # SDD
thoughts/shared/   # ACE session notes (gitignore contents)
harness/prompts/
harness/checklists/
.cursor/skills/    # start-change, draft-spec, research-codebase, …
.claude/commands/  # /start_change, /draft_spec, /research_codebase, …
```

**С чего начинать работу:** skill `start-change` / `/start_change` — сам предложит
полный SDD+ACE или урезанный путь и сделает только первый шаг.

Граф решений и игрушечные примеры: [docs/workflow.md](docs/workflow.md).  
Установка в репо: [docs/adoption.md](docs/adoption.md).

## Связь с ace-harness-lab

[ace-harness-lab](../ace-harness-lab) — тренажёр с учебным Go Issue Tracker.  
**ace-sdd-kit** — тонкий kit для переноса в реальные проекты (без учебного app).

## Лицензия

MIT
