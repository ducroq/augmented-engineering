# Memory

## Next session — what "continue" means (savepoint 2026-10-29)

Re-verify each item before acting (`git status`, `gh issue view`). In order:

1. **Framework drift**: this repo pins agent-ready-projects **v1.10.0**; latest release is **v1.50.0** (2026-10-27). Run
   `/update-drift` first. It may change CLAUDE.md, the curate skill and verify annotations, so do it before content work.
2. **Right-leg bet: unpark the V-model proposition** (engineer's bet, 2026-10-29). Agents make the left leg
   (specify/design/implement) cheap, so value moves to the right leg (verify/integrate/validate). Add a
   "Why the right leg, why now" section to `PROPOSITION-vmodel-reposition.md`, built on: (a) the verification vs
   validation split (agents take verification against spec and model; humans own validation: model fidelity,
   right problem), which answers "verification gets automated too"; (b) simulation as oracle, from MathWorks' MCP
   tooling (watch-list entry 2026-10-29), where a wrong model costs hardware; (c) cognitive surrender extended to
   "the simulation passed". Evidence: E-1, Seifert et al. 2025. Calibrate as EMERGING ("may"). Then run
   `review-devil` alone, not the full battery. Tracked: GH #51, H-1 in `docs/hypothesis-log.md`.
3. **Learn the Material single source** (GH #48): the property list is hand-copied in
   PROPOSITION.md §1, CHEATSHEET.md, README.md, `site/src/pages/patterns/learn-the-material.astro` and
   `site/src/components/IllustrationMaterial.astro`. Make PROPOSITION.md canonical; source the evidence from
   `~/repos/veen-systems/infra/ai-tooling/models.md`. Site edits wait on the ADR-008 freeze.
4. **Evidence-issue backlog**: open "Evidence:" issues (#7–#50) filed from source repos, untriaged into
   claims/knowledge. Triage, don't bulk-close. While triaging, classify each for H-1 (verification vs validation,
   agent- vs human-caught). Open issues: <!-- verify: n=$(gh issue list -L 300 --json number -q length 2>/dev/null) || { echo "CANNOT VERIFY: gh unavailable"; exit 0; }; echo "$n open issues"; [ "$n" -ge 1 ] -->50 on 2026-10-29.
4b. **Keep shrinking the read surface** (engineer, 2026-10-29: prune, thin, mechanize, retire). Done: archive pass
   (`memory/archive/`). Next: CLAUDE.md (10.6k chars) duplicates the Related Repos table and carries counts that
   decay ("17 claims, 59% coverage"): turn counts into probes or drop them; retire `memory/reference_tandemize.md`
   if the partnership is dead; consider closing evidence issues once folded into claims.
5. **Not this repo, listed so they don't get lost**: a Shaw & Nave card in `~/repos/agent-ready-papers/literature/`;
   infra-side follow-ups live in infra's memory (`ai-knowledge-map-followups.md`).
6. **Engineer decisions pending**: the ADR-008 merge terms (blocks site work); whether a history rewrite is wanted
   (gotcha-log 2026-10-08, public push).

Context: `memory/session_2026-10-29_matlab-right-leg.md`; earlier threads `memory/session_2026-10-08_knowledge-map.md`.

## Topic Files

| File | When to load | Key insight |
|------|-------------|-------------|
| `memory/gotcha-log.md` | Stuck or debugging | Open gotchas + Promoted table; resolved ones in `memory/archive/` |
| `claims/claim-registry.md` | Writing any content with factual claims | Confidence tiers per claim |
| `memory/project_aug_podcast_marketing.md` | Working on podcast | Series identity, competitive landscape, growth path |
| `memory/feedback_echo_chamber.md` | Adding new evidence | Circular evidence risk — case studies verifying themselves |
| `memory/reference_tandemize.md` | Discussing external partnerships | Tandemize.ai potential synergy |
| `memory/session_2026-10-29_matlab-right-leg.md` | Context on the right-leg bet and the archive pass | Ask + thread list |
| `memory/session_2026-10-08_knowledge-map.md` | Context on knowledge/ scope, the infra AI-knowledge map, open threads | Ask + thread list; follow-ups in infra memory |
| `memory/archive/` | Only when history is needed | Retired state history, resolved gotchas, old sessions |
| `docs/decisions/README.md` | Making an architectural decision | ADR index — 9 decisions (podcast, site reframe, umbrella pivot, tandemize merge, knowledge layer) |
| `knowledge/README.md` | Recording lessons or perspectives on AI | Low-bar dated layer; never cite directly in public content (ADR-009, amended) |
| `~/repos/veen-systems/infra/ai-tooling/README.md` | Looking up any model/tooling/sovereignty fact | Estate-wide map of AI knowledge; `models.md` there indexes model behaviour |
| `docs/VIBE.md` | Working on site design | Visual identity: engineered, honest, practitioner-first |
| `docs/writing-guide.md` | Writing or reviewing prose | Nine-component writing system: voice, logic, tension, dialogue |

## Recently Promoted

<!-- Gotchas promoted to topic files or CLAUDE.md. Format:
     "if [situation], then [what to do]" — promoted from gotcha-log YYYY-MM-DD -->

- If memory accumulates in auto-memory (~/.claude/projects/), move it in-repo to `memory/` — promoted from gotcha-log 2026-03-19
- If adding a home for AI/model/tooling knowledge, read the map in `~/repos/veen-systems/infra/ai-tooling/README.md` first; before moving a file, grep sibling repos for pointers; before pushing this PUBLIC repo, read every commit in `origin/master..HEAD` — from session 2026-10-08 (gotcha-log)
- If embedding non-HTML DSLs (Mermaid, diagrams) in Astro, never place them in template markup — use JS strings with `set:html` or `textContent`, and prefix links with `import.meta.env.BASE_URL` — promoted from gotcha-log 2026-04-03

## Current State (2026-10-29)

- **Position**: tool umbrella (ADR-005/006/007); flagship agent-ready-projects. Site is a pattern library (ADR-004), deployed by `.github/workflows/deploy.yml` on every push to master; site edits frozen pending ADR-008.
- **Content**: PROPOSITION.md (four patterns), 5 case studies, 5 examples, claim registry (17 claims), writing guide, `knowledge/` layer (ADR-009), podcast eps 00-01 scripted.
- **Open bet**: the right leg of the V-model (H-1 in `docs/hypothesis-log.md` <!-- verify: grep -c '^### \[2026-10-29\] H-1' docs/hypothesis-log.md -->, GH #51).
- **Read surface pruned** (2026-10-29): changelog-style Current State, resolved gotchas and the 2026-03-19 session file moved to `memory/archive/` (not read by default).
- History before 2026-10-29: `memory/archive/current-state-history-2026.md`.

## Related Repos — Quick Reference

| Repo | Key file to read first |
|------|----------------------|
| agent-ready-projects | `README.md` (the full guide) |
| agent-ready-papers | `README.md` + `papers/perspective/` (Paper 1) |
| driven-pendulum | `docs/theory/00_index.md` + `claims/claim_registry.md` |
| vmodel.eu | `CLAUDE.md` + `docs/adr/README.md` |
| OPAL (BR head) | `design_review_checklists/00_INDEX.md` |
| llm-distillery | `CLAUDE.md` + `docs/adr/` |
| RenkumSpot | `CLAUDE.md` + `docs/decisions/` |
| ese_bot | `docs/ARCHITECTURE.md` + `docs/decisions/` |
| ovr.news | `CLAUDE.md` + `docs/decisions/` |

## Podcast

Strategy: `memory/project_aug_podcast_marketing.md`. Scripts `podcast/dialogen/` (ep 00, 01), show notes `podcast/shownotes/`, review agents `.claude/agents/ae-review-*.md`. Dialogue-style ADR-001 lives in podcast-generator. Stats source: Digital Engineers research (local, outside this repo).

## Active Decisions

- **Framing**: "SE is necessary but insufficient" (not "augmented engineering IS systems engineering") — per review feedback
- **Case study style**: Pattern-first, loosely coupled to claim registry — not thesis chapters
- **Material properties split**: Persistent (confidence inflation, observation-calibration gap) vs. transient (scoring regression, plausible-but-wrong severity)
- **Personal project**: No institutional references (HAN removed from all public-facing docs)
- **Framework**: agent-ready-projects, version pinned in CLAUDE.md header (drift: savepoint item 1)
- **Adopted agent-ready-papers claim registry**: Typed verification with confidence tiers
- **Feedback loop framing adopted** (2026-03-17): "agent generates → agent reviews → agent validates → engineer decides" — borrowed from practitioner discourse, grounded in our evidence
- **In-repo memory by default**: Memory files live in `memory/` inside the repo, not in tool auto-memory. Exception only for content that should never be committed. Per ADR-001 in agent-ready-projects.
- **Site is a pattern library, not research portfolio** (ADR-004): Lead with the reader's problem, not the research journey. Evidence supports but doesn't lead. Nine projects are attribution, not content.
- **Augmented Engineering is a tool umbrella** (ADR-005): The proposition becomes backstory. Tools are the point.
- **Only durable patterns are core** (ADR-006): Context Is Architecture and Layer Your Verification are core (structural). Learn the Material and Reproduce Don't Assess are advisory (model-dependent, 12-24 month shelf life).
- **Don't build umbrella ahead of tools** (ADR-007): Minimal umbrella until second flagship exists. agent-ready-projects is the flagship. Layered verification tooling is the candidate second tool (issue #4).
