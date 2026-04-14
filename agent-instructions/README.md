# Agent Instructions in the Wild

Real-world agent instruction files collected from practitioners. Different tools, same underlying pattern: structured markdown that shapes agent behavior in a specific domain.

## Index

| File | Tool | Domain | What makes it interesting |
|------|------|--------|--------------------------|
| [evdk-assignments.agent.md](evdk-assignments.agent.md) | Copilot | Embedded C / education | Agent implements image-processing algorithms from PDF specs, builds firmware, runs unit tests. Teaching scaffold — students write the algorithms, the skill knows the workflow. |
| [evdk-performance-test.agent.md](evdk-performance-test.agent.md) | Copilot | Embedded hardware | Fully autonomous: patches source, builds firmware, flashes to MCU over LinkServer, reads timing results from COM port, restores source. No human in the loop. |

## Conventions

- Include the original file as-is — don't edit for style or strip tool-specific fields.
- Add to the index with: tool, domain, and one line on what makes it interesting.
- Any tool welcome: Claude Code skills, Copilot .agent.md, Cursor .cursorrules/.mdc, Gemini CLI rules, OpenCode .md, BMAD personas.
