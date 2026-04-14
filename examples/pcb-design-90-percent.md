# The PCB That Was 90% Done

**Pattern:** Layer Your Verification

## What happened

Los Alamos National Laboratory's space electronics division tested an AI platform (Circuit Mind) that generates PCB schematics from block diagram specifications. They gave it two real designs: a medium-difficulty STM32 board and a high-difficulty FPGA board.

The medium-difficulty result looked impressive: **90% complete in minutes.** The AI generated a viable schematic for most of the design, a task that normally takes 60-80 hours manually.

Then the engineers reviewed it.

They found errors the AI's own verification reports had missed: an incorrect LED resistor value and a disconnected VBUS rail. Neither error was flagged by the tool's built-in checks. Both would have caused hardware failures if the board had been fabricated.

The high-difficulty design told a different story. The AI could only complete **50%** because it lacked support for FPGA and DDR4 memory components. An engineer spent 32 hours on the FPGA integration alone, another 32 on DDR4. Deep hardware expertise was non-negotiable.

## The numbers

| | Medium difficulty | High difficulty |
|---|---|---|
| AI completion | 90% | 50% |
| Engineer completion | 10% | 50% |
| Errors found in human review | 2 | 4 |
| Errors flagged by AI's own V&V | 0 | 0 |

## Why this matters

Two layers of verification were needed. The AI's built-in V&V (layer 1) found nothing. Human engineering review (layer 2) found the actual defects. If the team had trusted the tool's own reports, two errors would have reached fabrication.

This is Pattern 2: each verification layer catches what the previous one missed. The AI's self-check was not worthless, it may have caught other issues, but it was insufficient alone.

The engineers also discovered an unexpected lesson: **don't over-constrain the AI.** Effective use required knowing what to specify tightly and what to leave flexible. That's a contextual engineering judgment (Pattern 3) that no amount of AI capability replaces.

## When this pattern doesn't apply

If you're generating something that's immediately testable (a script you can run, a query you can execute), the execution environment is your second layer. Layered verification matters most for artifacts that are evaluated by review, not by running them.

## Source

Love, C. & Mu, Y. (2025). *Evaluation of an AI-based schematic design tool for PCB development.* Los Alamos National Laboratory, LA-UR-25-30842.
