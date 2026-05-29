# Infinite Agentic Loop

> **Tutorial**: [Infinite Agentic Loop with Claude Code](https://youtu.be/9ipM_vDwflI)  
> **Repo**: https://github.com/disler/infinite-agentic-loop  
> **Author**: [@disler](https://github.com/disler)

## What It Does

The Infinite Agentic Loop is a **meta-agent orchestrator** that commands parallel AI
sub-agents to generate endlessly evolving, unique content iterations from a
specification file. Instead of a single agent writing output sequentially, it deploys
*waves of parallel agents* — each assigned a distinct creative direction — producing
diverse, spec-compliant results simultaneously.

## Key Capabilities

- **Four generation modes** via the `/project:infinite` Claude Code slash command:
  - `count = 1` → single iteration
  - `count = 5–20` → batch mode (agents launch simultaneously or in batches of 5)
  - `count = infinite` → continuous wave generation until context limits are reached
- **Parallel sub-agent coordination** — each agent receives the full spec, a snapshot
  of existing iterations, a unique iteration number, and an assigned creative dimension
  to prevent duplication.
- **Spec-driven generation** — reads a Markdown specification file (`specs/`) that
  defines content format, naming patterns, quality standards, and evolution strategy.
- **Directory-aware** — reconnaissance phase reads all existing iterations before each
  wave so no two outputs are the same.
- **Progressive sophistication** — infinite mode escalates creative complexity wave by
  wave, from functional basics to paradigm-shifting innovations.
- **Context-budget management** — monitors total context usage and concludes gracefully
  when limits approach.

## Example Usage

```bash
# Start Claude Code in the repo
claude

# Single iteration
/project:infinite specs/invent_new_ui_v3.md src 1

# Batch of 20 UI components
/project:infinite specs/invent_new_ui_v3.md src_new 20

# Infinite mode — keeps generating until context runs out
/project:infinite specs/invent_new_ui_v3.md infinite_src_new/ infinite
```

## Architecture

```
.claude/commands/infinite.md   ← The orchestrator prompt (this agent's brain)
specs/                         ← Specification files that define what to generate
src/ src_infinite/             ← Output directories for generated iterations
CLAUDE.md                      ← Project context for Claude Code
```

The orchestrator runs as a **Claude Code custom slash command**. It dispatches
sub-agents via the `Task` tool, coordinating parallel execution, managing naming,
and collecting results — all within a single Claude Code session.

## Why It's Useful

- Demonstrates the **Infinite Agentic Loop pattern** — a reusable architecture for
  any domain (UI components, test cases, docs, code variants, data synthesis).
- Works out-of-the-box with Claude Code — no external infrastructure needed.
- Fully spec-driven — swap the spec file to generate anything: write a spec, run the
  loop, get 20 unique outputs in minutes.
