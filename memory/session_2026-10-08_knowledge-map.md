# Session 2026-10-08: knowledge layer, then the estate-wide AI-knowledge map

**Opening ask:** "should this repo also track our knowledge on AI, LLMs, tooling etc., and broader perspectives?"
Later asks: use material from seven infographics, the Shaw & Nave preprint and a De Groene article; inventory
where AI knowledge lives across the estate ("preferably in a single place"); commit, push, anonymise.

## Outcome
- ADR-009: `knowledge/` added, then amended the same day. It is narrowed to lessons, perspectives (`landscape/`)
  and the watch list. `WATCH-LIST.md` moved to `knowledge/watch-list.md`.
- Two landscape entries: `cognitive-surrender.md` (Shaw & Nave 2026, SSRN preprint, not peer-reviewed) and
  `ai-sovereignty-per-layer.md` (Rikap/Stikker; defers to infra for the axes).
- An inventory of ~20 repos made `~/repos/veen-systems/infra/ai-tooling/README.md` the single estate-wide map of AI
  knowledge, with `models.md` there as the model-behaviour index (infra commit `e0335b8`, local only, no remote).
- Personal and local-path details removed after a push to the public repo.
- FyE/core pulled (`effde38`). FyE is institutional work and was kept out of the map.

## Threads
- Track AI knowledge here: **closed**. The scope is narrowed, and facts live in infra.
- Use the infographics: **closed**. Only the System 3 / Shaw & Nave one was used; the Fowler one awaits a primary
  source, not taken further.
- Inventory and single place: **closed** (map + seed). Follow-ups are in infra's memory, `ai-knowledge-map-followups.md`.
- Shaw & Nave card in agent-ready-papers `literature/`: **open** (other repo).
- *Learn the Material* list hand-copied 5× (PROPOSITION, CHEATSHEET, README, site ×2): **open**, GH #48.
- Site landscape page is the March edition: **open**, blocked by the ADR-008 site freeze.
- Framework drift, v1.10.0 pinned vs v1.49.2: **not yours**, the engineer's call (`/update-drift`).
- Whether to rewrite public history: **not yours**, the engineer's call.
- `.claude/skills/curate/SKILL.md`: the project-local copy was deleted in the working tree (not by this session); committed at wrap-up on the engineer's "clean up the repo". The user-level `~/.claude/skills/curate` is the live one.
