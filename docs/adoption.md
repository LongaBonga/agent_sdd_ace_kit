# Adoption: brownfield vs greenfield

## Brownfield — встроить в существующий репо

```bash
/path/to/ace-sdd-kit/bin/ace-sdd install /path/to/your-service
```

Если уже есть `AGENTS.md`:

```bash
# безопасный режим (по умолчанию): рядом появится AGENTS.md.ace-sdd — смержите вручную
ace-sdd install ~/repo/svc

# или дописать блок в конец существующего AGENTS.md
ace-sdd install ~/repo/svc --merge-agents

# или перезаписать harness-файлы с бэкапом *.bak.<ts>
ace-sdd install ~/repo/svc --force --merge-agents
```

Что появляется:

- `docs/specs/` — SDD
- `thoughts/shared/{research,plans,progress}/` — ACE session artifacts
- `harness/prompts|checklists`
- `.cursor/skills/*`, `.claude/commands/*`
- `CLAUDE.md`, `ACE-SDD.md`, правки `.gitignore`

Первый цикл на brownfield: маленький баг → spec (короткий) → research → plan → implement.  
Не начинайте с «переписать сервис».

## Greenfield — новый проект

```bash
/path/to/ace-sdd-kit/bin/ace-sdd init ~/repo/my-app --lang go \
  --module github.com/you/my-app
```

`--lang none` — только harness, без кода.

Дальше: `/draft_spec` → (research waiver пока пусто) → plan → implement.  
Как только код есть — research обязателен для non-trivial изменений.

## Совместный поток (напоминание)

Вход: **`start-change`** / `/start_change` (классификация + первый шаг).  
Полный граф и примеры: [workflow.md](workflow.md).

```text
start_change
  → spec (SDD, durable)
    → research (ACE, as-is code)   # brownfield
      → plan (ACE, phases + verify)
        → implement
          → update spec if behavior drifted
```

## Уже ставили kit раньше?

Чтобы подтянуть `start-change` и новые prompts:

```bash
ace-sdd install /path/to/repo --force
# AGENTS.md: --merge-agents или смержить AGENTS.md.ace-sdd вручную
```

## Синхронизация промптов

Источник правды: `harness/prompts/`. Зеркала Cursor/Claude — тонкие обёртки; после правок prompt обновите skills/commands.
