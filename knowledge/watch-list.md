# Watch List

Things worth tracking that are **not yet** evidence for the four patterns — research results, early tooling, single-paper claims, or industry moves that *might* mature into examples or shift a pattern.

## How this differs from `examples/`

- **`examples/`** — published evidence already supporting one of the four patterns. Pattern-first, practitioner-accessible, sourced.
- **Watch list (here)** — items that are too early, too narrow, or too speculative to file as evidence. Promotion happens when (a) the work is replicated or adopted, and (b) a practitioner can actually use it.

## Promotion / drop criteria

An item graduates to `examples/` when **all** of:
- A working engineer can apply or observe it today (not lab-only)
- At least one independent replication or production adoption exists
- It clearly maps to one of the four patterns

An item gets dropped when:
- Six months pass with no replication or adoption
- The result fails to reproduce
- A better example covering the same ground enters `examples/`

## Currently watching

| Added | Item | Source | Candidate pattern | Promotion trigger |
|-------|------|--------|-------------------|-------------------|
| 2026-05-18 | **RecursiveMAS** — multi-agent framework where agents share information via embedding space rather than text. Claims 1.2–2.4× faster inference, ~76% token reduction by round 3, 0.31% of params trained. Apache 2.0, tested on Qwen + Llama-3 across code-gen / medical / search. | [VentureBeat via ovr.news](https://ovr.news/en/artikel/us_media_venturebeat_a5971e00aaf7/) (UIUC + Stanford, 2026-05-15) | *Learn the Material* (advisory) — embedding-space coordination as a behavioral property worth knowing | Adoption in mainstream agent tooling (Claude Code, Cursor, LangGraph) OR independent replication beyond the original paper |
