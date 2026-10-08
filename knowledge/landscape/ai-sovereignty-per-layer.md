---
title: AI sovereignty is decided per layer, not per model
added: 2026-10-08
last_verified: 2026-10-08
shelf_life: 12-24m
sources:
  - "Eva Hofman, 'Hoe onafhankelijk blijft AI-bedrijf Mistral?', De Groene Amsterdammer nr. 34, 2026-08-17 (paywalled; journalism, interviews with Cecilia Rikap and Marleen Stikker)"
  - "Cecilia Rikap, The Rulers (book, referenced in the article; not read yet)"
feeds: ese_bot ("sovereignty as architecture constraint"); none of the four patterns directly
---

**Status:** journalism and opinion from two named experts. Useful as framing; check the factual
items before repeating them.

## The idea

Having a "European" model does not make you sovereign. Rikap (economist, UCL) and Stikker (Waag
Futurelab) argue from different angles that sovereignty is decided across a **stack of layers**:
chips, compute, datacenters, cloud, models, software. Control at one layer means little if another
layer is owned by someone who can exercise power over it.

- **Rikap:** LatamGPT is presented as independent but is built inside AWS with AWS money and
  technical help. Mistral sits at the edge of an ecosystem it can never dominate, and was expected
  (by an insider she interviewed) to end up dependent on a US cloud giant. "The problem is not that
  the EU buys technology from another country. The problem is buying it from a company able to
  exercise power over our way of life." (paraphrased translation)
- **Stikker:** sweeping statements about sovereignty are easy to dismiss and invite
  **sovereign-washing**: constructions with US companies that suggest European jurisdiction without
  delivering it. Be specific per layer; anchor sovereignty legally and economically. Her concrete
  proposal: a **public AI** base model trained on paid-for public-sector data, democratically
  governed, that others build on.
- Both warn against techno-nationalism ("European values") and prefer universal values and
  cooperation with Canada and the Global South.
- Historical frame: Microsoft's **embrace, extend, extinguish**, and the 1990s browser wars, as
  the pattern to watch for in AI.

## Reported facts (verify before reuse, 6m relevance)

- July 2026: Mistral announced deep cooperation with Microsoft, with a multi-billion investment
  promised.
- The article states that in spring 2026 the US government "switched off" Anthropic's models for
  European use. Unverified here; this would matter a lot for tool-agnosticism and for our own
  tooling. Check a primary source before repeating it.

## Why it matters here

- **ese_bot** already treats sovereignty as an architecture constraint. The per-layer framing gives
  that a vocabulary: for each layer (model weights, inference host, cloud, vector store, embeddings
  API), who can switch it off or change the terms?
- **Tool-agnostic constraint.** If access to a model provider can be withdrawn by a government, the
  "patterns work with any AI system" constraint is not only a portability nicety; it is resilience.
  Context Is Architecture artefacts (plain markdown, in-repo memory) survive a provider switch;
  provider-specific features do not.
- Possible landscape angle for the podcast: "sovereign-washing" as the policy-level cousin of
  "looks right" outputs.

## Counter-evidence / open questions

- Both interviewees are critics of big tech; the article includes no defence of the Mistral deal
  beyond Mensch's one-line quote.
- "Public AI within two years" (Stikker) is a proposal, not evidence of feasibility.
- What does per-layer sovereignty actually cost an engineering team? ese_bot may have numbers.
