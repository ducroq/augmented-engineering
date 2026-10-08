# Knowledge

What we know or have observed about AI, LLMs, agent tooling and the wider landscape. It is not yet
claim-worthy, or will never be. Internal working notes, per [ADR-009](../docs/decisions/ADR-009-knowledge-layer-separate-from-claims.md).

## How this differs from claims, examples and the watch list

| Layer | Holds | Bar |
|-------|-------|-----|
| `claims/claim-registry.md` | What we claim publicly | High: confidence-tiered, evidence-mapped |
| `examples/` | Published evidence that maps to a pattern | High: sourced, pattern-first |
| `knowledge/watch-list.md` | Early items that might become an example | Medium: has a promotion trigger |
| `knowledge/` (everything else) | What we know or have observed | Low: sourced and dated, nothing more |

Knowledge feeds claims through the registry's normal process. Never cite `knowledge/` directly in
public content (site, podcast, articles). Check the registry first.

## Areas

| Directory | Scope |
|-----------|-------|
| [`models/`](models/) | Behavioural properties of models and model generations: what they do well, what they get wrong, what changed. Feeds *Learn the Material*. |
| [`tooling/`](tooling/) | Agent harnesses, MCP, skills, hooks, IDE integrations: what works, what broke, cost and latency. Feeds *Context Is Architecture* and *Layer Your Verification*. |
| [`landscape/`](landscape/) | Broader perspectives: economics, labour, education, regulation, and positions we disagree with. Context for framing, not evidence. |
| [`watch-list.md`](watch-list.md) | Research and tooling that might be promoted to `examples/`. Has its own rules. |

## Entry format

One topic per file, kebab-case filename. Start with frontmatter:

```markdown
---
title: <short title>
added: YYYY-MM-DD
last_verified: YYYY-MM-DD
shelf_life: durable | 12-24m | 6m
sources:
  - <URL, paper, or "observed: <repo>, <date>">
feeds: <pattern name and/or claim ID, or "none">
---

<What we know, in a few paragraphs. Numbers over narrative. Say what is observed vs. reported vs. guessed.>

## Counter-evidence / open questions
<What would make this wrong. Leave it in even when empty.>
```

**Shelf life guide:**
- `durable`: structural, not model-dependent (for example, how context loading works in a harness).
- `12-24m`: tied to a model generation or tool version.
- `6m`: fast-moving (pricing, benchmarks, release-specific behaviour).

## Maintenance

- **Expiry.** At each `/curate`, entries past `last_verified + shelf_life` get re-verified (bump
  `last_verified`) or deleted. Deleting is fine. Knowing something went stale is knowledge too, so
  record it in one line in the area's index if it matters.
- **Promotion.** When an entry has enough evidence for a claim, open a registry entry and link back.
  The knowledge entry stays as the working notes.
- **Negative results count.** "Tried X with model Y, it did not work, here is why" is a valid entry.
- **No dumping.** If you cannot say what an entry is for (`feeds:`) or where it came from (`sources:`),
  it does not go in.

## Index

<!-- One line per entry: - [title](path) — one-line hook (shelf_life, last_verified) -->

- [Cognitive surrender vs. cognitive offloading](landscape/cognitive-surrender.md) — Shaw & Nave preprint: people follow wrong AI 80% of the time, feedback helps (12-24m, 2026-10-08)
- [AI sovereignty is decided per layer](landscape/ai-sovereignty-per-layer.md) — Rikap/Stikker via De Groene: sovereign-washing, public AI, per-layer control (12-24m, 2026-10-08)
