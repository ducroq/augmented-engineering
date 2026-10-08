---
title: Sovereign-washing and public AI (Rikap, Stikker)
added: 2026-10-08
last_verified: 2026-10-08
shelf_life: 12-24m
sources:
  - "Eva Hofman, 'Hoe onafhankelijk blijft AI-bedrijf Mistral?', De Groene Amsterdammer nr. 34, 2026-08-17 (paywalled; journalism, interviews with Cecilia Rikap and Marleen Stikker)"
  - "Cecilia Rikap, The Rulers (book, referenced in the article; not read yet)"
feeds: framing for ese_bot ("sovereignty as architecture constraint") and the tool-agnostic constraint; none of the four patterns directly
---

**Status:** journalism and opinion from two named critics. This is a *perspective*. What
sovereignty means operationally in the estate is defined elsewhere, and this entry does not
redefine it:

- **Descriptive axes** (run control, openness, provenance, data exposure; including TNO's "open
  washing" warning): `~/repos/veen-systems/infra/ai-tooling/sovereignty.md`
- **What sovereignty requires** (a rehearsed exit): `~/repos/veen-systems/SovereignStack/docs/adr/ADR-001-what-sovereign-requires.md`

## The perspective

- **Owning a model is not owning the stack** (Rikap, economist, UCL). LatamGPT is presented as
  independent but is built inside AWS with AWS money and help. Mistral sits at the edge of an
  ecosystem it cannot dominate; an insider expected it to end up dependent on a US cloud giant (a
  Microsoft investment followed in July 2026). Her test: not "do we buy from another country" but
  "can the vendor exercise power over our way of life" (paraphrased translation).
- **Sovereign-washing** (Stikker, Waag Futurelab): sweeping sovereignty claims are easy to dismiss
  and invite deals with US companies that only *suggest* European jurisdiction. Be specific per
  layer (chips, datacenters, cloud, software), and anchor it legally and economically. This is the
  policy-level twin of TNO's "open washing", and the same per-layer stance that the infra axes and
  SovereignStack already take.
- **Public AI** (Stikker): a base model trained on paid-for public-sector data, democratically
  governed, for others to build on. Both warn against techno-nationalism ("European values") in
  favour of universal values and cooperation beyond Europe.
- **Embrace, extend, extinguish**: Microsoft's 1990s pattern, with the browser wars as precedent,
  offered as the thing to watch for in AI partnerships.

## Why it matters here

- It gives words for explaining *why* ese_bot and the estate treat sovereignty as architecture:
  "sovereign-washing" names the failure that per-layer checks exist to catch.
- The article also claims a US cut-off of Anthropic models for EU use in spring 2026. That is
  unverified, and is tracked as a trip-wire in `~/repos/veen-systems/infra/platform-watch.md`
  (Anthropic row), not here. If it holds, the tool-agnostic constraint stops being a portability
  nicety and becomes resilience.

## Counter-evidence / open questions

- Both interviewees are critics of big tech; the article includes no defence of the Mistral deal
  beyond Mensch's one-line quote.
- "Public AI within two years" is a proposal, not evidence of feasibility.
