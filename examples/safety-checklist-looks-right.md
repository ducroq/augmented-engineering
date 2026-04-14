# The Safety Checklist That Looked Right

**Pattern:** Reproduce, Don't Assess

## What happened

Researchers tested whether LLMs could perform HAZOP analysis, a standard safety review technique used in chemical and process engineering. They fed plant descriptions to GPT-4 and asked it to identify hazards, causes, and safeguards.

The outputs looked professional. Correct formatting, plausible language, appropriate technical vocabulary. Human reviewers rated the text as highly similar to expert-written HAZOP entries: **over 86% textual similarity** on standard metrics.

Then they checked whether the content was actually correct.

**Semantic validity: 19-37%.** Between two-thirds and four-fifths of the AI-generated safety analysis was wrong in ways that looked right.

The failure mode is specific: the AI produced outputs with correct units, correct terminology, and plausible magnitude, but wrong substance. A safeguard that doesn't exist. A cause that doesn't apply to this plant. A hazard scenario that sounds reasonable but misses the actual risk.

Assessment ("does this HAZOP look reasonable?") would pass these outputs. Only reproduction, going back to the plant design and checking each entry against the actual system, catches the errors.

## The numbers

| Metric | Value |
|--------|-------|
| Textual similarity to expert HAZOP | >86% |
| Semantic validity | 19-37% |
| Undetectable by surface review | 63-81% of errors |

## Why this matters

This is Pattern 4 at industrial scale. If your verification method is "read the output and check if it looks right," you will miss most errors in domains where AI produces fluent, well-formatted, wrong content.

The HAZOP case is particularly dangerous because the stakes are physical safety. A missed hazard scenario in a chemical plant isn't a code bug you can patch on Tuesday.

The fix is what it always is: reproduce the analysis independently. Check each claim against the actual system. Don't ask "does this look right?" Ask "what answer do I get when I work through this myself?"

## When this pattern doesn't apply

If the domain has a compiler, the compiler is your reproducer. Code either runs or it doesn't. The danger zone is domains where outputs are evaluated by reading, not by executing: safety analysis, requirements documents, design reviews, academic claims.

## Source

Park et al. (2025). LLM-assisted HAZOP analysis. Study comparing AI-generated and expert-generated HAZOP entries across multiple plant scenarios.
