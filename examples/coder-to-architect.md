# From Coder to Architect

**Pattern:** All four

## What happened

Several embedded systems practitioners have published detailed accounts of how their development workflow changed after adopting AI coding agents. A consistent pattern emerges across these accounts, independent of each other: the engineer stops writing code and starts writing specifications.

The workflow typically evolves through stages:

1. **Copy-paste phase.** Ask a chat model for code, paste it into the IDE, hope it works. ("Vibe coding.")
2. **Spec-driven phase.** Write a functional specification in Markdown. Let the AI generate code from it. When something breaks, update the spec, not the code.
3. **Agent phase.** Move from chat to a coding agent that can see the project directory, edit files, compile, and test. The agent reads the spec and implements it.
4. **Full automation.** The agent compiles, flashes firmware, reads serial output, runs tests, fixes bugs, and commits. The engineer specifies and validates.

The endpoint: "My main tasks became writing my wishes in plain English, supervising progress, and verifying results."

Two human responsibilities remain: **specify** (what to build) and **test** (does it work). Everything between is delegated.

## Where the four patterns show up

**Learn the Material.** AI skills and tools have silent failure modes. Practitioners report that custom automation "sometimes doesn't trigger" and you "have to pay attention." The agent doesn't tell you when it's not using the tools you gave it. You have to notice.

**Layer Your Verification.** The typical flow has at least five layers: specification review, compilation, flashing, serial monitor, and test execution. Each catches different errors. One practitioner reports ~3,000 lines of generated code with only 2 compilation errors (both auto-fixed), but behavioral issues found only during testing.

**Context Is Architecture.** The biggest infrastructure decisions, containerized development environments, isolated test networks, serial port routing, security boundaries, are context the AI cannot see or decide. As one practitioner put it: "That is not really an AI problem, it is a VM infrastructure problem." Custom skills are needed because generic AI tools are "more for web development."

**Reproduce, Don't Assess.** "Compilers do not tolerate hallucinations because for them, they are simply errors." Compilation is forced reproduction. Testing is forced reproduction. The practitioners who succeed are the ones who never rely on reading the code to verify it.

## The numbers

| Metric | Value |
|--------|-------|
| Generated code volume | ~3,000 lines per project |
| Compilation errors | 1-2 (auto-corrected) |
| Behavioral errors found in testing | 2+ per project |
| Verification layers in typical workflow | 5 (spec review, compile, flash, serial, test) |

## Why this matters

The "coder to architect" transition isn't about productivity. It's about which competencies matter. Writing code becomes less important. Writing specifications, assessing AI-generated designs, understanding physical constraints, and testing rigorously become more important.

This is the shift from tool proficiency to engineering judgment. The engineers who succeed aren't the ones who prompt best. They're the ones who know the domain well enough to specify correctly and validate thoroughly.

## When this pattern doesn't apply

The full workflow assumes projects complex enough to warrant a specification. For a 50-line script, vibe coding is fine. The patterns kick in when the project is too large to hold in your head and too consequential to ship without testing.

## Sources

Practitioner workflow documentation from multiple embedded systems engineers (2025-2026), including published video walkthroughs and companion GitHub repositories. Combined audience: 300K+ views across multiple accounts.
