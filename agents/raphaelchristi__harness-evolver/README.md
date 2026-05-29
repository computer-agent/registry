# Harness Evolver

**Harness Evolver** is a LangSmith-native autonomous optimizer for LLM agent codebases, distributed as a Claude Code plugin and npm package (`npx harness-evolver@latest`).

Point it at any agent project and it will iteratively improve the agent — prompts, routing, tool calls, retrieval, and orchestration architecture — through a rigorous, data-driven loop grounded in LangSmith evaluation.

## What It Does

- **Sets up ground truth**: Creates a LangSmith Dataset with train + held-out splits and an LLM-as-judge rubric. Captures a baseline score.
- **Evolves iteratively**: Spawns self-organizing proposer sub-agents, each investigating a specific failure lens derived from trace data. Proposers work in isolated git worktrees — nothing touches main until it wins.
- **Gates rigorously**: Every candidate must beat the current best on held-out examples, pass constraint checks, and clear an efficiency gate. Regressions are blocked.
- **Compounds learning**: Winning patterns are consolidated into evolution memory and promoted back into CLAUDE.md for future iterations.
- **Archives everything**: Losers are archived with diffs and scores so future proposers can avoid dead ends or branch from promising failures.

## Skills

| Skill | What it does |
|---|---|
| `/harness:setup` | Explore project, configure LangSmith, create dataset, write `.evolver.json` |
| `/harness:evolve` | Run the propose-evaluate-merge optimization loop |
| `/harness:health` | Diagnose dataset quality and auto-correct issues |
| `/harness:status` | Rich ASCII progress chart with iteration history |
| `/harness:deploy` | Tag, push, and finalize the winning evolved version |
| `/harness:certify` | Validate and certify the agent against its evaluation rubric |

## Quick Start

```bash
cd my-llm-project
export LANGSMITH_API_KEY="lsv2_pt_..."
claude

/harness:setup      # explores project, configures LangSmith
/harness:health     # check dataset quality
/harness:evolve     # run the optimization loop
/harness:status     # check progress
/harness:deploy     # tag and finalize
```

## Real Results

Tested on a RAG agent (Agno + Gemini Flash Lite): **0.575 → 1.000 correctness (+74%)** in 7 iterations. 4 candidates merged, 3 rejected by gate checks.

## Runtime

Works with Claude Code, Cursor, Codex, and Windsurf. Requires `LANGSMITH_API_KEY`.

## Links

- Repository: https://github.com/raphaelchristi/harness-evolver
- npm: https://www.npmjs.com/package/harness-evolver
- Paper: https://arxiv.org/abs/2603.28052 (Meta-Harness, Lee et al.)
