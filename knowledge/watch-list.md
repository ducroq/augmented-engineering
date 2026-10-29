# Watch List

Things worth tracking that are **not yet** evidence for the four patterns — research results, early tooling, single-paper claims, or industry moves that *might* mature into examples or shift a pattern.

## How this differs from `examples/`

- **`examples/`** — published evidence already supporting one of the four patterns. Pattern-first, practitioner-accessible, sourced.
- **Watch list (here)** — items that are too early, too narrow, or too speculative to file as evidence. Promotion happens when (a) the work is replicated or adopted, and (b) a practitioner can actually use it.

## Promotion / drop criteria

An item graduates to `examples/` when **all** of:
- A working engineer can apply or observe it today (not lab-only)
- At least one independent replication or production adoption exists
- It clearly maps to one of the four patterns

An item gets dropped when:
- Six months pass with no replication or adoption
- The result fails to reproduce
- A better example covering the same ground enters `examples/`

## Currently watching

| Added | Item | Source | Candidate pattern | Promotion trigger |
|-------|------|--------|-------------------|-------------------|
| 2026-05-18 | **RecursiveMAS** — multi-agent framework where agents share information via embedding space rather than text. Claims 1.2–2.4× faster inference, ~76% token reduction by round 3, 0.31% of params trained. Apache 2.0, tested on Qwen + Llama-3 across code-gen / medical / search. | [VentureBeat via ovr.news](https://ovr.news/en/artikel/us_media_venturebeat_a5971e00aaf7/) (UIUC + Stanford, 2026-05-15) | *Learn the Material* (advisory) — embedding-space coordination as a behavioral property worth knowing | Adoption in mainstream agent tooling (Claude Code, Cursor, LangGraph) OR independent replication beyond the original paper |
| 2026-10-29 | **MATLAB/Simulink agentic tooling** — MathWorks ships an MCP Core Server (5 tools: `evaluate_matlab_code`, `run_matlab_file`, `run_matlab_test_file`, `check_matlab_code` static analysis, `detect_matlab_toolboxes`; coding guidelines exposed as MCP resources), MATLAB + Simulink Agentic Toolkits (agent skills), in-product MATLAB/Simulink Copilot (R2025b/R2026a), and `llms-with-matlab` (OpenAI, Azure, local Ollama). Vendor tooling, no outcome data yet. | [MCP Core Server](https://github.com/matlab/matlab-mcp-core-server), [Guide to Agentic AI](https://www.mathworks.com/campaigns/offers/next/agentic-ai-with-matlab.html), [Generative AI with MATLAB](https://www.mathworks.com/products/matlab/generative-ai.html), [LLMs with MATLAB](https://www.mathworks.com/matlabcentral/fileexchange/163796-large-language-models-llms-with-matlab) | *Reproduce, Don't Assess* (agent computes in MATLAB instead of reasoning about equations); *Layer Your Verification* (static analysis + unit tests as agent-callable layers); *Context Is Architecture* (guidelines-as-resources, skills) | Published practitioner results (error rates, rework) from MCP-connected MATLAB/Simulink work, OR our own run: Driven Pendulum redone via the MCP server, compared with the original |
