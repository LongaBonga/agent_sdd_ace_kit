# Specs (SDD)

Durable product/engineering intent. Agents and humans treat these as the
**source of truth for acceptance**.

## Conventions

- One changeable unit per file: `YYYY-MM-DD_short-slug.md` or `FEATURE-name.md`
- Use [_TEMPLATE.md](_TEMPLATE.md) for new specs
- Link specs from plans; do not copy acceptance verbatim into plans
- After merge, update the spec if behavior drifted

## Waiver

Tiny changes may skip a full spec if the issue contains:

```text
waiver: no-spec — typo|deps-bump|docs-only
```
