# Driven Pendulum: Reproduce, Don't Assess

**Domain:** Physics / embedded hardware — electromagnetic pendulum synchronization
**Pattern:** Mechanical reproduction — when checking equations, compute the answer independently instead of reasoning about whether the equation "looks right"

---

## 1. What Was Built

The Driven Pendulum project (originally "SlingerDwinger") makes mechanical pendulum clocks keep quartz-accurate time (~1 second/day) using contactless electromagnetic synchronization. It converges three threads of prior work: van Baalen's concept (proven in a tower clock, 2015), Hodzelmans' physics (forced oscillation experiments, 2017), and Notenboom's electronics (Raspberry Pi Pico pulse generator, 2022).

The project required documenting 68 physics equations across 10 theory chapters, with formal traceability from requirements through theory to verification stages. The agentic workflow generated comprehensive theory documentation, then needed to verify it. That verification step is where the interesting pattern emerged.

---

## 2. How the Agents Were Used

The verification happened in three layers:

```
Layer 1: Self-review
    Claude generated the theory document, then reviewed it for
    "physics soundness" — dimensions, plausibility, consistency
    → Found: 0 errors

Layer 2: Independent review (Gemini)
    Google Gemini reviewed the same theory summary for
    "physics soundness"
    → Found: 0 errors

Layer 3: Mechanical reproduction (Sonnet)
    Sonnet 4.5, prompted to numerically reproduce every
    calculation step-by-step — substitute values, compute,
    compare to stated result
    → Found: 3 errors
```

The difference between Layer 2 and Layer 3 is not the model — it's the prompt. Gemini was asked to *assess* the equations. Sonnet was asked to *reproduce* them. The prompt forces a fundamentally different mode:

```
For each equation:
1. EXTRACT: Write the equation exactly; list all inputs with values
2. DIMENSIONAL ANALYSIS: Verify units balance
3. NUMERICAL REPRODUCTION: Substitute values; compute step-by-step
4. CONSISTENCY CHECK: Does this value appear elsewhere? Are uses consistent?
5. CROSS-REFERENCE: Does it match the source material?

RULES:
- Never skip a calculation. Show all work.
- Trust nothing. Treat every number as potentially wrong.
- When checking tables: verify EVERY row.
```

After the initial three errors, a dedicated equation-checker agent (using the same mechanical reproduction approach) found two additional errors, bringing the total to five.

---

## 3. What Worked

**Mechanical reproduction caught all errors; soundness review caught none.** The three errors found:

**Error 1 — Wrong label.** A table header stated "0.5 kg bob, 5 degrees amplitude" but the values were computed at 1 degree. The coupling strength difference is 5x (epsilon = 0.012 at 1 degree, not 0.0023 at 5 degrees). The table *looked* right — epsilon values were in a reasonable range, units checked out, the column structure was clean. Only when Sonnet computed `m * g * theta = 0.5 * 9.81 * 0.0175` (1 degree) and then `0.5 * 9.81 * 0.0873` (5 degrees) did the mismatch become visible.

**Error 2 — Formula error.** A dwell time formula had a spurious leading factor of 2 and was missing a theta_max term. The stated formula predicted 84 ms; the table said 43 ms. The formula structure looked reasonable — correct dimensions, physically sensible form. Sonnet found it by computing dwell time step-by-step and comparing to the table.

**Error 3 — Inconsistency.** "3.3 ms per swing" times 3600 swings/hour should give ~12 s/hr. The document also stated 36 s/hr. Root cause: a formula used `/6` (from a 2pi approximation) where it should have been `/2`. Each number individually is plausible — 3.3 ms corrections and synchronization rates of tens of s/hr are physically reasonable. Arithmetic exposed what plausibility reasoning couldn't.

**The pattern is general.** All three errors share the same characteristic: the wrong answer was in the right ballpark, had correct units, and fit within a physically reasonable range. This is exactly the class of error that "does this look right?" review will miss. It's also, notably, the class of error that experienced physicists miss in peer review — plausible results survive scrutiny until someone recomputes.

---

## 4. What Didn't Work

**"Soundness review" is worthless for numerical verification.** Both Claude's self-review and Gemini's independent review assessed the equations for physical plausibility, dimensional consistency, and theoretical coherence — and found zero errors. The problem isn't that these models are bad at physics. They correctly identified that the equations were dimensionally consistent, referenced appropriate theory, and produced results in reasonable ranges. They just never *computed* anything.

This mirrors a well-known problem in peer review: reviewers check that equations make sense conceptually but rarely substitute numbers and verify results. LLMs default to the same mode unless explicitly redirected.

**The equation-checker prompt is brittle.** It works because it forces step-by-step computation, but if the model decides to skip rows ("the remaining rows follow the same pattern...") or summarize instead of computing, errors slip through. The "verify EVERY row" instruction needs enforcement, not just instruction.

**Self-review is unreliable.** The model that generated the document failed to find errors in its own output even with an explicit "review for errors" prompt. This is consistent with findings that LLMs are better at generating than self-correcting (Huang et al., 2024, "Large Language Models Cannot Self-Correct Reasoning Yet Without External Feedback").

---

## 5. The Pattern

> **When** verifying numerical or mathematical content (equations, calculations, tables of derived values),
> **use** mechanical reproduction: prompt the agent to substitute specific values into every equation, compute step-by-step, and compare the result to the stated answer — rather than asking whether the equation "looks right" or "is physically sound,"
> **because** plausible-but-wrong results survive reasoning-based review but fail arithmetic checks.

This is the equation-verification equivalent of test-driven development: don't trust that code works because it looks correct — run it and check the output. The same principle applies to equations: don't trust that a formula is correct because the dimensions check out — substitute values and verify the result.

The pattern has a natural complement: use soundness review for *conceptual* errors (wrong model, missing physics, inappropriate assumptions) and mechanical reproduction for *numerical* errors (arithmetic mistakes, wrong coefficients, copy-paste errors). They catch different classes of problems.

**When this pattern doesn't apply:**
- Symbolic or purely algebraic work where there are no numerical values to substitute
- When the equations are trivially simple (F = ma) and errors would be obvious
- When the cost of verification exceeds the cost of the error — reproducing 68 equations takes significant compute and time; for a back-of-envelope estimate, it's overkill

---

## 6. Limitations

The 3/3 (or 5/5 with the follow-up) error detection rate is specific to this document and this set of errors. We don't know the false negative rate — how many errors the mechanical reproduction also missed. The errors found were all in the "wrong coefficient" class; the pattern may not catch errors in model selection, boundary conditions, or assumptions.

The comparison between Gemini (0 errors found) and Sonnet (3 errors found) is suggestive but confounded — different model, different prompt, different session. A cleaner test would be the same model with assessment-prompt vs. reproduction-prompt. The project has informal evidence of this (Claude's self-review also found 0 errors) but not a controlled comparison.

The "reproduce, don't assess" principle is well-established in engineering verification practice (independent calculation checks are standard in structural engineering, for instance). What's new here is applying it as an LLM prompting strategy. This aligns with but does not independently validate the broader principle.

---

## 7. Session Update: 2026-03-16

### V&V on informal messages

The reproduce-don't-assess pattern was applied to **WhatsApp messages** drafted for stakeholder Bas Hodzelmans — informal technical communication, not formal documentation. V&V caught 5 errors before sending:

1. **Unit confusion (NUMERICAL):** Stated "4.3 ms/hr" correction rate; actual value 180 ms/hr (≈ 4.3 s/day). Factor ~42 error. Skipped the intermediate step ΔT/T = ½·Δg/g.
2. **Material property overestimate (NUMERICAL):** Ferrite rod μr stated as ~1000–3000; actual value for rod-type ferrite is ~100–400. Confused rod antennas with MnZn toroids.
3. **Missing force formula (ASSUMPTION):** Only the coaxial dipole-dipole formula was used; the recommended configuration (magnet swinging laterally past coil) requires the broadside formula, which gives half the force.
4. **Wrong coil orientation (ASSUMPTION):** Advised coil axis horizontal perpendicular to swing plane; for a vertical magnet dipole this gives weak coupling. Correct: vertical axis.
5. **Incorrect terminology (LABEL):** Called the coil a "pancake coil" when it's a short solenoid with a removable rod core. The physics was correct but the name was wrong — caught by the human, not by V&V.

This extends the pattern's applicability: it works for back-of-envelope calculations in informal messages, not just formal 68-equation theory documents. Error #5 is notable as a **human-in-the-loop catch** — V&V verified the physics but didn't flag that the component name was wrong for the geometry described.

### 6-agent parallel review

After updating the project documentation, six specialized review agents ran in parallel:

| Agent | Scope | Issues found |
|-------|-------|-------------|
| Doc quality | CLAUDE.md, RUNBOOK, gotcha-log | 7 (broken refs, duplication, dead pointers) |
| Theory consistency | Equation numbering, cross-refs | 5 (missing EQ-26b/c in index, ambiguous ranges) |
| Prototype plan | Force calcs, BOM, practicality | 9 (wrong force value, winding conflicts, missing guidance) |
| Audit completeness | C1–C22 sequential, DONE verification | 3 (stale metadata, cosmetic) |
| Memory system | MEMORY.md structure, duplication | 3 (stale promoted entries, N52 moment rounding) |
| Requirements traceability | FR/NFR coverage, orphans | 6 (NFR-04 orphaned, V0 untraced, Ch 10 missing) |

**Total: 14 unique issues found across 6 agents in ~2 minutes.** All 14 were subsequently fixed. This is evidence for the multi-agent verification pattern: specialized agents running in parallel catch cross-cutting issues that a single broad reviewer would miss.

### Human-in-the-loop moment

After all V&V was complete, all 14 review findings fixed, and two commits pushed, the human caught that "pancake coil" was incorrect terminology for a short solenoid with a rod core. The physics was correct everywhere — the force mechanism (∂B_z/∂x gradient from a vertical-axis coil) was accurately described. But the *name* was wrong for the physical object being built.

This is evidence for claims C-1/C-2: domain expertise catches errors that formal verification cannot. The equation-checker verifies arithmetic; the 6-agent review checks structural consistency; but knowing that "a coil with a 50-75mm rod core is not a pancake" requires understanding what these components physically are.

### agent-ready-projects adoption

The project adopted the agent-ready-projects v1.0.0 framework during this session, creating CLAUDE.md (Layer 1), RUNBOOK.md (Layer 2), and gotcha-log.md (Layer 4). This provided immediate structure for the curation loop. Five operational patterns were fed back as [issue #1](https://github.com/ducroq/agent-ready-projects/issues/1).

---

## 8. Session Update: 2026-05-04 — Layered V&V Compounds

### Trigger

The day before (2026-05-03), a simulation-findings document recommended a Hall sensor to the stakeholder based on a bare-pendulum + EM Python simulator. The recommendation was wrong: the application is a working mechanical clock + EM, where the escapement self-sustains amplitude and EM only needs to phase-lock — exactly the injection-locking scenario the project's own `docs/theory/03_synchronization.md` had already framed. The sim was internally consistent. The theory was internally consistent. No verification check examined the two together.

The error class is *"structurally correct simulation conclusion promoted to application advice without re-anchoring to deployment scenario."* The existing `equation-checker.md` template would not catch it — the equations were fine. No template existed for the class.

### Response: build the missing layers, smoke-test against the artifact that motivated them

In one day, two new template families were added — physics-verification (theory-side) in `agent-ready-papers` (`33eecdc`) and physics-tests (code-side) in `agent-ready-projects` (`89dde90`) — synthesised from physics-teaching tradition (Polya, Feynman), Mahajan-style estimation, ASME V&V 10/20/40, Roache MMS, and Lean formal verification.

The next day (2026-05-04), all four theory-side templates were applied to the driven-pendulum doc set as a smoke test. ~115 individual checks, ~25 distinct issues surfaced.

### Headline finding

**The new `cross-document-consistency.md` template caught the v2-doc failure mode reproduced inside the theory chapter set itself.** Ch 10 (the simulation chapter) describes 5 sim models, none of which include the escapement / self-sustaining-drive term that Ch 03's injection-locking framework requires. Yet Ch 10's experiments are tagged as validating predictions T-03.x (lock acquisition, lock range, 30-day stability). Executing Ch 10 as written would re-run the v2-doc class of error — a bare-pendulum sim presented as validation of a clock+EM theory.

This is exactly the failure mode the template was built to detect. The template caught its own motivating error class, recursively, in the artifact next door — first positive evidence that the family closes the gap it was designed for.

### Layered V&V compounds — each new layer caught what previous layers missed

| Layer | When | New errors found | Missed by which previous layer |
|-------|------|------------------|--------------------------------|
| Plausibility review (Claude self / Gemini) | 2026-03 | 0 | — |
| equation-checker (mechanical reproduction) | 2026-03 | 5 (arithmetic) | Plausibility — looks right |
| WhatsApp message V&V | 2026-03-16 | 5 (units, terminology, formula structure) | Plausibility — informal context |
| 6-agent parallel review | 2026-03-16 | 14 (cross-cutting structural) | Single-pass review |
| `cross-document-consistency.md` | 2026-05-04 | 4 HIGH (Ch 10 reproduces v2-doc error; FR-07 contradiction; ε downstream) + 8 MEDIUM | equation-checker — per-document scope only |
| `dimensional-checker.md` | 2026-05-04 | 8 HIGH (EQ-12 force-not-power; PI controller term mismatch; EQ-58 tempco) + 5 cross-section symbol drifts | equation-checker — only checks numeric examples |
| `estimation-checker.md` | 2026-05-04 | Pinpointed Ch 04 §4.2.3 ×100 error from Ch 04's *own* parameters; Config W BOM internally inconsistent | All previous — these are scaling expressions with no numeric example to reproduce |
| `two-paths-consistency.md` | 2026-05-04 | Ch 03 §3.3.2 "two paths to 14.4 min/day" are circular | All previous — looks like cross-validation, isn't |

Each row added new findings the previous rows could not have caught — not because the previous layer was bad, but because each layer has a structurally different scope. Plausibility review reasons. Mechanical reproduction substitutes. Cross-document checks scope. Dimensional checks units. Estimation reproduces with the doc's own inputs. Two-paths-consistency catches cross-validations that aren't.

The OPAL case study (in `PROPOSITION.md`) showed five verification layers each finding different defects in a one-shot review. This session shows the same pattern unfolding *over time* on a single project — and, more importantly, that **building the next layer is now cheap enough to do the same week the gap is identified**.

### A textbook reproduce-don't-assess example, sharpened

The `cross-document-consistency` check found a 200× discrepancy between Ch 04 §4.2.3 ("0.17 mN at 22.5 mm c-t-c") and `prototype_v0.md` ("35–64 mN at 15 mm c-t-c") but did not adjudicate which side was wrong.

The `estimation-checker` did, in five lines:

1. EQ-26 prefactor $3\mu_0/(2\pi) \sim 6\times 10^{-7}$
2. With Ch 04's stated $m_{\rm perm} = 0.4$ A·m², $m_{\rm coil} = 0.019$ A·m²: numerator $\sim 8\times 10^{-3}$
3. At x = 22.5 mm: $x^4 \sim 2.6\times 10^{-7}$
4. F ~ $6\times 10^{-7} \cdot 8\times 10^{-3} / 2.6\times 10^{-7} \sim 18$ mN
5. Ch 04's own table says 0.17 mN — 100× under-estimate.

Plugging the doc's own numbers into the doc's own equation gave 18 mN, not 0.17 mN. Localisation: the error is in Ch 04 §4.2.3 (table arithmetic), not in EQ-26. Downstream: Ch 04's framing "EM force is 0.04% of restoring force" understates by 100× — the actual figure is ~4%, comfortable for ε ≈ 0.02 sync.

This is reproduce-don't-assess applied to *forensic localisation*: the check that adjudicates between two conflicting claims is to reproduce one of them with that claim's own stated inputs. It worked in five lines. The 200× drift had been live in the doc set for weeks.

### Calibration evidence (the templates also confirmed what they should have)

Not every finding was a bug. The templates produced 13 explicit OK results that mattered:

- **Sensor optionality is consistent across all current docs** (open-loop = optional, closed-loop = required). The v2-doc retraction had propagated correctly through Ch 01, Ch 05, Ch 08, the stakeholder summary, and the prototype plan.
- **Geometry A decision (ADR-001) propagated cleanly** through Ch 04, Ch 09, theory_summary.
- **Hodzelmans Geometry-B pulse-width caveat correctly applied** in Ch 05 (the CLAUDE.md "never transfer validation data between geometries" hard constraint was being obeyed).
- **EQ-26 / EQ-26c prefactor (½ ratio between coaxial and broadside) symbolically verified** from the dipole-dipole potential.
- **All Adler-equation limits (ε → 0, Δω → 0) satisfied.**

This is calibration: a template that finds nothing in a known-clean chapter earns trust by failing to false-positive. The summary tables in the verification reports surface OK findings as a top-level section, not just buried noise — a template-feedback suggestion fed back to `agent-ready-papers#5`.

### Forward step: scope-domain registry for the new sim

The proactive sibling to `cross-document-consistency` is `scope-domain-registry.md`: declare the model's scope upfront, then check claims against it mechanically. A registry entry was written *before* the new clock+EM simulator is implemented (`driven-pendulum/sim/scope/pendulum_clock.md`) — declaring INCLUDES (escapement, Geometry A, fixed and sensor-triggered pulse modes), EXCLUDES (Geometry B, multi-pendulum coupling, eddy currents, mainspring detail), regime of validity, and 5 OPEN_SCOPE questions to resolve before implementation. The registry is the contract the future sim must satisfy. If executed properly, this prevents the v2-doc class of error structurally — the next sim cannot be applied outside scope without the verification agent flagging it.

### What this updates

| Artifact | Update |
|---|---|
| Case-study driven-pendulum (this file) | This Section 8. |
| `claim-registry.md` E-1 | Source field extended with 2026-05-04 evidence: 4 templates, ~25 issues across ~115 checks. |
| Issue in this repo | Filed as evidence-tracking entry (see Evidence issue list). |
| `agent-ready-papers#5` | Smoke-test report posted with template-feedback suggestions. |
| `agent-ready-projects#13` | Awaiting smoke test — deferred until new clock+EM sim exists. |

### Implication for the proposition

The driven-pendulum case study originally supported one pattern: "reproduce, don't assess" (mechanical reproduction beats plausibility review). This session strengthens it from a stand-alone pattern to a member of a layered family — *each verification layer with a structurally different scope catches what the previous layer cannot*, and **building each new layer is now cheap enough to do the same week the gap is identified**. The proposition's "Verification Became Cheap Enough to Layer" thesis (currently anchored to OPAL's static 5-layer review) gains a temporal/iterative axis from this session: layers can be added in response to specific failures, validated against the artifact that motivated them, and produce results within a single working day.

The recursion is the strongest evidence: the template caught its own motivating error class reproduced in the theory chapter set next door.

### Cross-references

Verification reports archived in driven-pendulum repo (commit `e1bdd32`):
- `docs/cross_document_consistency_2026-05-04.md` — 28 checks, 15 issues, 13 OK
- `docs/dimensional_check_2026-05-04.md` — ~78 equation checks, ~18 issues
- `docs/estimation_limiting_twopaths_2026-05-04.md` — 19 checks, 5 NEW findings + corroboration

Forward-looking artifact (commit `d1fbe7a`):
- `sim/scope/pendulum_clock.md` — scope-domain registry for the planned clock+EM sim

Cross-repo:
- [agent-ready-papers#5](https://github.com/ducroq/agent-ready-papers/issues/5) — adoption-feedback issue for physics-verification family + smoke-test results posted as comment
- [agent-ready-projects#13](https://github.com/ducroq/agent-ready-projects/issues/13) — adoption-feedback issue for physics-tests family (smoke test deferred)
