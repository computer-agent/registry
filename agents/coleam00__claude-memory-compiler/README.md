# Claude Memory Compiler

An autonomous background agent that turns your Claude Code conversations into a
growing, searchable personal knowledge base — automatically.

## What It Does

Inspired by [Andrej Karpathy's LLM Knowledge Base](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f),
this agent installs three Claude Code lifecycle hooks that run silently in the
background:

| Hook | What it does |
|---|---|
| `SessionEnd` | Captures the transcript and spawns a background flush |
| `PreCompact` | Safety net — also flushes before Claude compacts context |
| `SessionStart` | Injects the compiled knowledge index into the next session |

## Core Skills

- **memory-flush** — Calls the Claude Agent SDK to extract decisions, lessons,
  and patterns from a session transcript and appends them to a dated daily log.
- **knowledge-compile** — Reads daily logs and compiles them into structured,
  cross-referenced Markdown articles (`concepts/`, `connections/`, `qa/`).
- **knowledge-query** — Answers natural-language questions by reading the master
  index first, then pulling relevant articles — no vector database needed.
- **knowledge-lint** — Runs seven health checks (broken links, orphans,
  contradictions, staleness) against the compiled knowledge base.

## Why No RAG?

At personal scale (50–500 articles), an LLM reading a structured `index.md`
outperforms cosine similarity. RAG becomes necessary only when the index itself
exceeds the context window (~2 000+ articles).

## Quick Start

```
Tell Claude Code:
"Clone https://github.com/coleam00/claude-memory-compiler into this project
and set up the hooks so my conversations compile into a knowledge base.
Read AGENTS.md for the full technical reference."
```

## Key Commands

```bash
uv run python scripts/compile.py          # compile new daily logs
uv run python scripts/query.py "question" # ask the knowledge base
uv run python scripts/lint.py             # run health checks
```

## Links

- **Repository:** https://github.com/coleam00/claude-memory-compiler
- **Technical reference:** `AGENTS.md` in the repo
