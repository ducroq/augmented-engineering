# ADR-009: A Knowledge Layer, Separate from the Claim Layer

**Date:** 2026-10-08
**Status:** Accepted, amended 2026-10-08 (scope narrowed, see Amendment)

## Context

This repo only has places for things that already have strong evidence behind them: the claim registry
(confidence-tiered), case studies (own projects, pattern-first), and `examples/` (published evidence
that maps to a pattern). `WATCH-LIST.md` (2026-05-18) was a first attempt at a lower-bar staging area,
but it is narrow on purpose: it only holds items that might later be promoted to `examples/`.

Much of what we actually learn never meets that bar and has nowhere to go:

- **Model behaviour** — quirks, regressions and improvements per model generation. ADR-006 says the
  durable insight in *Learn the Material* is "LLMs are a material with properties" while the specific
  property list goes out of date. Nothing keeps that list current.
- **Tooling** — agent harnesses, MCP, skills, hooks, cost and latency observations from the nine
  source projects. Lessons from these get lost unless they turn into a gotcha or a case study.
- **Broader perspectives** — economics, labour, education, regulation, and positions held by people
  we disagree with. This context shapes how we frame the patterns but is not evidence *for* them.

Putting this material into the existing artifacts would either lower the evidence bar for claims or
get blocked by it. The hard constraints (evidence-based, confidence-calibrated) protect public-facing
content and should stay strict.

## Decision

Add a `knowledge/` directory as a **low-bar, dated** knowledge layer, not published on the site,, kept separate from the
claim layer.

1. **Two tiers.** `knowledge/` holds what we *know or have observed* (sourced and dated, low bar to
   add). `claims/claim-registry.md` holds what we *claim publicly* (high bar). Knowledge can feed claims
   through the registry's normal process, never the other way round. Nothing in `knowledge/` is cited
   as evidence in public content directly.
2. **Every entry expires.** Each entry has `added`, `last_verified`, and `shelf_life` fields
   (`durable` / `12-24m` / `6m`). Entries past their shelf life are re-verified or deleted. `/curate`
   step 0 (freshness check) is the natural place to surface them.
3. **Not site content.** `knowledge/` is working notes. It is not published on the site (the repo
   itself is public, so entries must be fit to be read by anyone) and
   is not brand investment, so it does not conflict with ADR-007 (don't build the umbrella ahead of the
   tools) or the ADR-008 freeze on brand-specific investment.
4. **Watch list moves in.** `WATCH-LIST.md` becomes `knowledge/watch-list.md`. Its promotion and drop
   rules are unchanged.
5. **Four areas.** `models/`, `tooling/`, `landscape/`, plus `watch-list.md`. Add areas only when an
   existing one has clearly outgrown its scope.

## Consequences

**Positive:**
- Observations have somewhere to go before they are claim-worthy, so they stop getting lost.
- *Learn the Material* gets a maintained, dated property list, which is what ADR-006 implied it needed.
- The claim registry stays strict, because the pressure to file half-evidence there drops.
- Cross-repo learnings from the nine source projects have a home short of a full case study.

**Negative:**
- Another place to maintain. Without the expiry discipline it turns into a dumping ground and rots
  faster than anything else in the repo.
- Risk of the line between "knowledge" and "claim" blurring in prose. Writers must check the registry,
  not `knowledge/`, before stating something publicly.
- If the ADR-008 merge moves this repo's content under another brand, `knowledge/` moves with it, even
  though it is arguably Jeroen's personal asset rather than the brand's. See Revisit If.

## Alternatives Considered

- **Separate repo** — rejected. See the Amendment: the model and tooling facts already have an
  estate-level home in `infra/ai-tooling/`, which is not tied to this brand.
- **Widen `WATCH-LIST.md`** — rejected: one flat table cannot hold model properties, tooling notes and
  landscape views, and it would dilute the watch list's clear promotion purpose.
- **Lower the claim registry bar** — rejected: breaks the confidence-calibration constraint that
  public content depends on.
- **Keep it in `memory/`** — rejected: `memory/` is for session continuity and project state, not
  domain knowledge. Mixing them bloats the memory index loaded every session.

## Revisit If

- The ADR-008 merge terms mean this repo is absorbed into another brand: consider moving `knowledge/`
  to a personal repo.
- `knowledge/` is used fewer than about once a month across two `/curate` cycles: fold it back into the
  watch list.
- More than a third of entries are past their shelf life at a `/curate` run: the expiry discipline
  is failing and the format needs to change.

## Amendment (2026-10-08, same day)

The original decision was written without checking the rest of the estate. An inventory of about 20
repos the same day showed that `infra/ai-tooling/` already owns model, tooling and sovereignty
knowledge. Its README records "what we *run* and *decided*" there and "what it *teaches*" here,
and SovereignStack owns the development track. Two `knowledge/` areas (`models/`, `tooling/`)
would have been second copies, which breaks this repo's own ground-truth rule.

**Narrowed scope.** `knowledge/` holds only:
- what working with agents **teaches** (synthesis that may later feed claims);
- **perspectives**: cognition, policy, economics, society (`landscape/`);
- the **watch list**.

Model behaviour, comparisons, eval method and cost live in `infra/ai-tooling/models.md`. The
estate-wide map of where each kind of AI knowledge lives is the table in
`infra/ai-tooling/README.md`, and there is no second map here. `knowledge/models/` and
`knowledge/tooling/` were removed (both empty).

The two-tier rule (knowledge ≠ claims), the entry format and the expiry rules are unchanged.
