# Phantom

**An autonomous AI co-worker with its own computer.**

Phantom is not a chatbot. It is a persistent, self-improving agent that lives on a dedicated VM (Docker / Hetzner Specter), remembers everything across sessions via vector search, evolves its own configuration after every session, and communicates wherever you are — Slack, Web Chat, Telegram, Email, or Webhook.

## Key Capabilities

- **Autonomous task execution** — full computer access (Read, Write, Bash, WebSearch, Agent tools); builds infrastructure without being asked
- **Vector-backed memory** — Qdrant + nomic-embed-text embeddings; semantically indexed recall across all sessions
- **Self-evolution engine** — 6-step post-session reflection pipeline with 5 safety gates; Phantom rewrites its own `phantom-config/` files, bumps its version, and commits
- **MCP server** — 17+ tools exposed as a streamable HTTP MCP endpoint; other agents can use Phantom as a tool
- **Multi-channel** — Slack (Socket Mode), Web Chat (SSE streaming + React UI), Telegram, Email (IMAP/SMTP), Webhook, CLI
- **Multi-provider** — Anthropic (default, Claude Opus), Z.AI/GLM-5.1, OpenRouter (100+ models), Ollama, vLLM, LiteLLM, custom Anthropic-compatible endpoints

## What Phantom Has Actually Built (in production)

- A ClickHouse analytics platform with 28.7M rows of Hacker News data, a REST API, and a real-time dashboard — without being asked
- Discord support for itself after being asked "Can I talk to you on Discord?"
- An observability stack monitoring its own infrastructure with 890K rows of metrics

## Quick Start

```bash
# Docker (recommended)
cp .env.example .env         # Add ANTHROPIC_API_KEY + Slack tokens
docker compose up -d
```

See [docs/](https://github.com/ghostwright/phantom/tree/main/docs) for full setup, provider switching, and the MCP reference.

## Spec

| Field | Value |
|-------|-------|
| Version | 0.20.2 |
| Model | Claude Opus (configurable) |
| Runtime | Bun + Docker |
| Tests | 1,819 |
| License | Apache 2.0 |
| Language | TypeScript |
