# nanobot

**nanobot** is a lightweight, open-source AI agent framework designed to be your personal, always-on assistant. It keeps the agent loop small and readable while delivering practical multi-channel chat, persistent memory, and a rich tool ecosystem.

## What It Does

nanobot receives messages from **15+ chat platforms** — Telegram, Discord, Slack, WhatsApp, WeChat, WeCom, Feishu, DingTalk, Matrix, QQ, MS Teams, Email, WebSocket, and a built-in React/TypeScript WebUI — and acts on them using an async LLM loop.

### Key Capabilities

| Capability | Details |
|---|---|
| **Multi-channel chat** | Telegram, Discord, Slack, Feishu, WhatsApp, WeChat, Teams, DingTalk, Matrix, Email, WebSocket, WebUI |
| **LLM providers** | Anthropic, OpenAI, OpenAI-compatible, Azure, AWS Bedrock, GitHub Copilot, Codex, NVIDIA NIM, Hugging Face, and more |
| **Tools** | Filesystem (read/write/edit), shell execution (sandboxed), web search/fetch, MCP server integration, image generation, subagent spawning |
| **Memory** | Dream two-phase consolidation: atomic session writes, long-term memory distillation, context compaction |
| **Long-horizon goals** | `/goal` command holds a sustained objective across many turns with visible progress |
| **Cron & scheduling** | Natural-language cron reminders, scheduled tasks, heartbeat monitoring |
| **WebUI** | Vite/React SPA with WebSocket multiplex, image uploads, streaming responses, locale switcher |
| **OpenAI-compatible API** | `/v1/chat/completions` and `/v1/models` for programmatic access |

## Quick Start

```bash
pip install nanobot-ai
nanobot setup        # interactive wizard: pick provider, set API key
nanobot gateway      # start the agent
```

Then connect your favourite chat channel via `nanobot --help` and start chatting.

## Architecture

nanobot uses an async `MessageBus` that decouples channels from the agent core:

```
Channel (Telegram/Discord/…)
        │
        ▼
   MessageBus (async queue)
        │
        ▼
   AgentLoop  ──▶  AgentRunner ──▶  LLM Provider
                        │
                        ▼
                    Tool Execution
                  (fs / shell / web / MCP …)
                        │
                        ▼
                   OutboundMessage ──▶ Channel
```

The core loop (`loop.py`, `runner.py`) is intentionally small. New capabilities live in channels, tools, or skills — never inline in the loop.

## Example Use Cases

- **Personal assistant** — runs 24/7 on a VPS, answers Telegram messages, schedules reminders, and searches the web on your behalf.
- **Coding helper** — integrates with your dev environment via MCP, reads/writes files, runs tests in a shell sandbox.
- **Research agent** — given a `/goal`, searches the web, summarises findings, and reports back across multiple turns.
- **Team bot** — connects to Slack or MS Teams, handles slash commands, forwards alerts, and manages shared reminders.

## Links

- **Docs**: https://nanobot.wiki
- **Repo**: https://github.com/HKUDS/nanobot
- **PyPI**: https://pypi.org/project/nanobot-ai/
- **Discord**: https://discord.gg/MnCvHqpUGB
