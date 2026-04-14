# Repositioning vmodel.eu: From Requirements Reviewer to Validation Competency Builder

**Status:** Draft proposition (April 2026)
**Context:** Connects Digital Engineer research (HAN/AEA) with augmented-engineering patterns and vmodel.eu

---

## The Problem With "AI Requirements Review Tool"

Every AI requirements tool on the market makes the same pitch: submit your document, get feedback, improve your requirements. Fraunhofer IESE's Quasar does it. The ki-marktplatz "Requirements AI Assistant" claims 50% productivity gains. A dozen startups do variations.

They all share an assumption: the human in the loop has the competency to act on the feedback. The tool validates. The human responds.

Research from the same institute that sells Quasar (Seifert et al. 2025, Fraunhofer IESE) shows that LLMs "substantially trail human reviewers" at requirements inspection, that "results don't vary across prompting techniques," and that "findings rarely match expert solutions." Their own blog concludes: "AI writes code in seconds, but who guarantees it solves the right problem?"

They answer this with "human-in-the-loop." That's a design pattern. It tells you where the checkpoint is. It doesn't tell you what happens inside it.

## What the Digital Engineer Research Adds

The Digital Engineer framework (Veen 2026, HAN University of Applied Sciences) proposes:

> **Competency = Domain Expertise × Validation Capability × Context Awareness**

The multiplication matters. A human in the loop with low V (validation capability) is not a checkpoint. It's a rubber stamp. The same framework identifies three stances engineers take toward AI:

- **Dependent**: accepts output without checking (the loop is empty)
- **Resistant**: refuses the tool entirely (the loop doesn't exist)
- **Augmented**: uses the tool while maintaining independent judgment (the loop works)

The Augmented stance is not a personality trait. It's the activation of domain knowledge, validation skill, and self-monitoring during AI-assisted work. If that's correct, it's teachable. And if it's teachable, you can build tools that teach it.

## The Repositioning

**Current position:** vmodel.eu is an AI requirements review tool.

**Proposed position:** vmodel.eu develops the validation competency that makes human-in-the-loop work.

The difference:

| AI review tool (current framing) | Validation competency builder (proposed) |
|----------------------------------|------------------------------------------|
| Tool validates, student responds | Tool exposes criteria, student learns to validate |
| Success = clean report | Success = student catches errors the tool misses |
| Develops compliance | Develops judgment |
| Competes with Quasar et al. | Different category entirely |

## Why This Isn't Just Marketing

vmodel.eu already does something most review tools don't: it exposes students to professional quality criteria (IEEE 29148, INCOSE, EARS patterns, traceability) that they would never encounter otherwise. A student who has never seen a traceability matrix can't evaluate one. The tool builds the vocabulary, the mental model, the foundation layer (Layer 1 in the Digital Engineer framework) that validation requires.

This is not a theoretical claim. It's what the tool already does. The repositioning makes it explicit.

But the research also identifies a risk: if students learn to satisfy the tool rather than understand the criteria, the tool develops the Dependent stance instead of the Augmented stance. The assessment becomes "pass vmodel.eu" instead of "understand requirements engineering." This is Hugo Arends' unit test problem at the requirements level: all tests pass, but the engineering judgment isn't there.

## What Changes in the Tool

The repositioning suggests concrete feature directions:

**1. Error injection mode.** Generate requirements documents with planted errors that match the tool's own review categories. Student must find them. This flips who validates: the tool generates, the student reviews. Directly develops V (validation capability).

**2. Validation confidence tracking.** Student marks their confidence before seeing the tool's feedback. Over time, the gap between their assessment and the tool's assessment becomes visible. This develops Layer 3 (meta-cognitive monitoring) — awareness of what you don't know.

**3. Domain-contextualized review.** The tool already handles embedded systems and ML/DL domain-specific NFRs. Extend this: show students that the same requirement can be adequate in one context and dangerous in another. This develops C (context awareness).

**4. "What did the tool miss?" exercises.** Present the tool's output alongside expert review. Student identifies gaps in the tool's analysis. This teaches that AI review is incomplete by design, not by accident, and develops the habit of looking beyond automated feedback.

None of these require rebuilding the tool. They're modes that use the existing scoring and analysis pipeline differently.

## The Article

The convergence of three projects creates a publishable argument:

1. **The research** (Digital Engineer) establishes that validation competency, not tool proficiency, is the critical differentiator — and that "human-in-the-loop" is necessary but insufficient without specifying what the human brings.

2. **The tool** (vmodel.eu) is a concrete case where this plays out. It already builds Layer 1 competency by exposing students to professional criteria. The research shows how to extend it to build Layers 2 and 3.

3. **The practitioner framework** (augmented-engineering) provides the patterns: "Learn the Material" maps to understanding LLM behavioral properties in requirements review; "Reproduce, Don't Assess" maps to checking requirements against domain constraints rather than accepting plausible text; "Layer Your Verification" maps to not stopping at the first automated review pass.

**Possible venues:** Requirements Engineering conference (RE'26), SEFI (engineering education), IEEE EDUCON, or a practitioner-oriented piece for IEEE Software.

**Working title options:**
- "Beyond Human-in-the-Loop: Building the Validation Competency That Makes the Loop Work"
- "An AI Requirements Tool Examined Through Its Own Research"
- "What's Inside the Loop? Validation Competency in AI-Assisted Requirements Engineering"

## The Fraunhofer Comparison

Fraunhofer IESE occupies the same space: they build the tool (Quasar), publish the limitations (Seifert et al.), and advocate human-in-the-loop. The comparison is not adversarial. It's complementary:

- Fraunhofer identifies *that* human oversight is needed
- The Digital Engineer framework identifies *what* the human needs to bring (D×V×C)
- vmodel.eu demonstrates *how* to develop it through tooling

The article doesn't argue Quasar is wrong. It argues the whole category needs a framework for what happens inside the checkpoint. D×V×C provides one.

## Open Questions

- Does vmodel.eu actually develop validation competency, or does it just develop compliance with the tool's own criteria? This is an empirical question that could be tested.
- Is the Augmented stance measurable through the tool's data? If students who use the error injection mode perform better on independent requirements review tasks, that's evidence.
- Should the tool be renamed? The V-model reference in "vmodel.eu" points to methodology. The new positioning points to the engineer. This is a branding question, not an urgent one.
- Where does vmodel.eu live organizationally? Under augmented-engineering (practitioner tools), under Digital Engineer (research outputs), or independently?

---

*Draft — April 14, 2026*
