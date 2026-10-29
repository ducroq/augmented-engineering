# Hypothesis Log

Provisional positions whose evidence lives in the future. Not tasks (GH issues), not frozen decisions (ADRs), not solved problems (`memory/gotcha-log.md`). Format: agent-ready-projects `templates/hypothesis-log.md`. Pin the falsification criterion (Method) before the data lands; don't loosen it afterwards, open a new entry instead. Resolved entries move to `## Resolved` with a one-line outcome.

## Open

### [2026-10-29] H-1: As agents make the left leg of the V cheap, engineering value moves to the right leg

**Position (provisional):** Agents compress specify/design/implement; the scarce skill becomes verify/integrate/validate. Agents will increasingly take *verification* (against spec and model: tests, static analysis, simulation), while humans keep *validation* (is the model faithful to reality, is the spec the right problem). Motivating evidence: claim E-1 (reproduce-don't-assess catches what plausibility review misses); Seifert et al. 2025 (LLMs trail humans at requirements inspection); the evidence backlog (GH #18-#50) is dominated by verification findings; vendors expose verification, not just generation, to agents (MathWorks MCP Core Server: tests, static analysis, execution; `knowledge/watch-list.md` 2026-10-29). Confidence: EMERGING at best, N=1.

**Alternative:** The human role shrinks on the right leg too. Signal: agent-run validation (not only verification) catching model-fidelity or wrong-problem errors at a rate comparable to humans, or published practice where simulation/test oracles are trusted without a human validation step and defect rates do not rise.

**Method:** Classify each new evidence issue and own-project finding as (a) verification error an agent caught, (b) verification error only a human caught, (c) validation error (wrong model / wrong problem) and who caught it. H-1 holds if (c) stays human-caught in the large majority; it is refuted if agents catch (c) routinely. First concrete test: Driven Pendulum via the MATLAB MCP server, recording which errors the agent's own simulation loop catches and which need the engineer.

**Revisit trigger:** The right-leg section of `PROPOSITION-vmodel-reposition.md` is drafted and reviewed, or 10 newly classified findings.

**Review by:** 2027-01-31

**Domain:** V-model, verification vs validation, proposition
**Status:** open

---

## Resolved

*(none yet)*
