# ADR-008: Merge to One Front with tandemize.ai (Brand Overlap)

**Date:** 2026-07-03
**Status:** Proposed — direction chosen, terms pending an ownership conversation with Arian

## Context

The same "augmented engineering" thesis is fronted by **two brands owned by two people**, covering
roughly the same ground:

- **`augmented-engineering.com`** — Jeroen's. This repo is its content body: the four patterns,
  `agent-ready-projects` (flagship tool), case studies, Astro site, podcast.
- **`tandemize.ai`** — Arian's. A consulting business around augmented engineering.

The overlap was never resolved. [ADR-001](ADR-001-podcast-as-dissemination.md) already points this
repo's podcast funnel at `tandemize.ai` ("top-of-funnel for tandemize.ai, a planned consulting
business") — so Jeroen's content is being routed to Arian's front, while Jeroen also runs his own brand.
The result is two similar brands, one message, and no boundary: a confused market signal and a split
funnel, with credit/revenue ownership undefined.

This surfaced during an umbrella-level triage of whether `augmented-engineering` still has an undeclared
commercial model (`../../brainstorm/IDEA_TRIAGE.md`, worked example dated 2026-07-03). The finding: the
commercial-model question (product vs. services vs. distribution — cf.
[ADR-005](ADR-005-umbrella-not-proposition.md)) is **downstream** of, and blocked by, the two-brand
ownership question. You can't declare this brand's model while it might be absorbed into the other.

## Decision

**Merge to one front.** One brand, one funnel, one story; the other brand is absorbed. This gives the
cleanest market signal and a single shared funnel instead of two overlapping ones.

The **direction** is decided. The **terms are not**, and can't be settled solo — they require a
conversation with Arian:

1. **Which domain survives** — `augmented-engineering.com` or `tandemize.ai`.
2. **Who owns/carries what** — the natural split is content + tool (Jeroen) vs. consulting delivery
   (Arian), which also matches revealed Pull (Jeroen's is high on writing/craft, unshown on the
   sales/consulting grind).
3. **How credit and revenue split.**

Until those terms land, this ADR stays **Proposed**, and **brand-specific investment is frozen** — no
further build on the site, no second funnel, no product-vs-services commitment — because half of it may
be absorbing into the other brand. The subordinate commercial-model choice (lead with
thought-leadership/distribution; validate paid consulting with one real inbound before building a
shingle) resumes only *after* the merge terms are set.

## Consequences

**Positive:**
- One coherent brand and funnel instead of two competing on the same thesis.
- Shared load with a co-carrier is materially less solo-drain than two overlapping brands — improves the
  sustainability picture (the triage's weakest dimension).
- A content/delivery split lets each person work to their actual Pull.

**Negative / cost:**
- Interpersonal, not technical: someone's brand gets absorbed; needs an explicit ownership + revenue
  conversation that hasn't happened.
- Freezes brand-specific work in the interim (site, funnel, model choice) until terms are agreed.
- ADR-001's funnel framing becomes provisional — it assumed `tandemize.ai` as the destination without
  resolving ownership; it may need to update once the surviving brand is chosen.

## Alternatives Considered

- **Parallel & independent** — each keeps their brand, differentiate by audience/angle. Rejected:
  lowest coordination cost but highest market-confusion and cannibalization risk on one shared thesis.
- **Complementary split, two brands** — `augmented-engineering.com` = thought-leadership + tool,
  `tandemize.ai` = consulting delivery, one funnel feeding both. Viable, and close to ADR-001's implicit
  model; rejected in favour of a single front for a cleaner market signal (the content/delivery *role*
  split is preserved *inside* the merged brand instead).
- **Stay undecided** — name the un-had conversation as the blocker and defer. Rejected as the standing
  state: the direction is cheap to choose now; only the terms need Arian.

## References

- `../../brainstorm/IDEA_TRIAGE.md` — worked example "augmented-engineering (2026-07-03)": the triage
  that surfaced this; binding constraint = the un-had Arian ownership talk.
- [ADR-001](ADR-001-podcast-as-dissemination.md) — points the podcast funnel at `tandemize.ai`; the
  framing this ADR revisits.
- [ADR-005](ADR-005-umbrella-not-proposition.md) — the product/services/distribution model question that
  is downstream of, and blocked by, this merge.
