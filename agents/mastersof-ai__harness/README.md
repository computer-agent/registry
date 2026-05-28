# Harness

An open-source agent runtime where **you control the entire system prompt** — no hidden framework instructions, no behaviour injection, no black box.

## What it does

Define an agent by writing a single `IDENTITY.md` file. Run it with `mastersof-ai`. The harness loads your markdown exactly as written, appends only transparent operational context (date/time, workspace path, available tools), and starts a conversation powered by the Claude Agent SDK.

```
IDENTITY.md  →  mastersof-ai  →  Agent with exactly the context you gave it
```

## Key capabilities

| Feature | Details |
|---|---|
| **Full prompt control** | Your IDENTITY.md is the system prompt — verbatim. No injected behaviour. |
| **Terminal TUI** | `mastersof-ai [--agent x]` — React/Ink UI for solo, local development |
| **Web UI** | `mastersof-ai --serve` — Fastify + React SPA, multi-user, token auth |
| **In-process MCP tools** | memory, workspace, web-search, shell, tasks, introspection, sub-agents, A2A |
| **Production-ready** | Rate limiting, cost caps, per-user isolation, LGPD-compliant privacy, bubblewrap sandbox |
| **Sub-agents & A2A** | Spawn parallel agents or call remote A2A-protocol agents from within an agent |

## Quick start

```bash
npm install -g @mastersof-ai/harness

# Uses your existing Claude Code subscription or an API key
mastersof-ai
```

On first run, `~/.mastersof-ai/` is created with three starter agents (cofounder, assistant, analyst) and a default config.

## Create your own agent

```bash
mastersof-ai create my-agent
# Edit ~/.mastersof-ai/agents/my-agent/IDENTITY.md
mastersof-ai --agent my-agent
```

## Example IDENTITY.md

```markdown
# Market Analyst

You are a senior market analyst. Your job is to research markets,
identify trends, and deliver clear, actionable analysis.

## How to work

- Use web search to gather current data before forming opinions.
- Structure every analysis with: thesis, evidence, risks, and conclusion.
- Save key findings to memory so they compound across sessions.
- Be direct. Commit to positions after weighing evidence.
```

## License

MIT — https://github.com/mastersof-ai/harness/blob/master/LICENSE
