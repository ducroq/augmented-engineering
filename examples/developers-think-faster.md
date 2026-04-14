# The Developers Who Thought They Were Faster

**Pattern:** Learn the Material

## What happened

METR (an AI evaluation organization) ran a controlled study in 2025. Sixteen experienced open-source developers worked on 246 real issues across repositories with 22,000+ stars. Crossover design: each developer worked some issues with AI tools and some without, eliminating individual skill as a variable.

The developers believed they were **20% faster** with AI assistance.

They were actually **19% slower.**

A 39-percentage-point gap between perceived and actual performance.

## The numbers

| Metric | Value |
|--------|-------|
| Sample | 16 developers, 246 issues |
| Perceived speed change | +20% (faster) |
| Actual speed change | -19% (slower) |
| Perception gap | 39 percentage points |
| Repository quality | 22K+ stars (established, complex codebases) |

## Why this matters

This is Pattern 1 in its most dangerous form: **confident but wrong**, applied not to the AI's output but to the developer's self-assessment.

The LLM behavioral property here isn't in the model. It's in the human. Working with AI *feels* productive. The fluent outputs, the instant responses, the impression of progress. But for complex work in established codebases, the actual result was negative.

The study's crossover design is important. This isn't "bad developers are slow with AI." The same developers, on comparable tasks, were measurably slower when using the tools they believed were helping them.

Why? The researchers suggest that the overhead of context specification, output validation, and integration exceeded the time saved by generation. For complex work in large codebases, the validation cost eats the generation benefit.

## What to do with this

The finding doesn't mean AI tools are useless. It means **your perception of their value is unreliable.** You cannot trust the feeling of being faster.

Measure. Track actual completion times, not vibes. If you can't measure, at minimum recognize that the confident sense of acceleration is a known bias, not a reliable signal.

This is the core of Pattern 1: LLMs have behavioral properties you need to design around. One of those properties is that they make you feel more capable than you are. The material isn't just in the model. It's in your response to the model.

## When this finding doesn't apply

The study measured experienced developers on complex, real-world issues. For simple tasks (boilerplate, formatting, routine code), AI likely does save time. The danger zone is complex work where validation overhead dominates: exactly the work where you most want AI help, and where it most confidently suggests it's helping.

## Source

METR (2025). *Measuring the Impact of Early-2025 AI on Experienced Open-Source Developer Productivity.* https://metr.org/blog/2025-07-10-early-2025-ai-experienced-os-dev-study/
