# Genesis AGI

**Genesis** is an open-source autonomous AI agent cognitive architecture built on [Claude Code](https://docs.anthropic.com/en/docs/claude-code) as its reasoning engine. It is not a chatbot, an API wrapper, or a prompt chain — it is a system designed to get fundamentally better the longer it runs alongside a user.

## What it does

Genesis provides four interconnected capabilities that compound over time:

### 🧠 Persistent 4-Layer Memory
- **Essential knowledge** — long-term facts, preferences, and context about the user
- **Proactive recall** — surfaces relevant knowledge before you ask
- **Semantic search** — Qdrant-powered vector retrieval across everything Genesis has learned
- **Knowledge pipeline** — transforms raw interactions into structured, reusable procedures

### 📚 Closed-Loop Self-Learning
Outcome classification, causal attribution, and procedure extraction with Laplace-smoothed confidence scores. Genesis tracks its own accuracy and can show the user the receipts.

### 🌙 Background Cognition
Genesis acts between sessions — researching, reflecting, auditing, and communicating via Telegram while the user is away. Not waiting for a prompt.

### 🔑 Earned Autonomy
Trust is granted per action category through demonstrated competence. First failure triggers demotion. The user always controls the levers; Genesis earns its scope of action over time.

## Key capabilities

| Skill | Description |
|---|---|
| Persistent memory | 4-layer hybrid memory compounding across months |
| Self-learning | Outcome-driven learning with confidence calibration |
| Background cognition | Autonomous research and reflection between sessions |
| Earned autonomy | Per-category trust model, evidence-based |
| Web research | MCP-powered search and fetch with anti-bot handling |
| Telegram integration | Async bidirectional channel |
| Code intelligence | GitNexus blast-radius analysis + Serena LSP |

## Getting started

```bash
git clone https://github.com/WingedGuardian/GENesis-AGI.git ~/genesis-setup
cd ~/genesis-setup
./scripts/host-setup.sh
```

After install: `cd ~/genesis && claude`

## Requirements

- Ubuntu 22.04+ (dedicated Linux machine or VM)
- Claude account (Claude Code as reasoning engine)
- 8 GB RAM minimum, 16 GB recommended
- Tailscale (for remote dashboard access)

## Runtime

Genesis runs as a set of systemd user units inside an Incus container, with Qdrant for vector storage and a Guardian/Sentinel dual-watchdog for reliability.

## What makes it different

Most AI agents are reactive and stateless — equally ignorant about you on day 100 as day 1. Genesis is different: it accumulates context, acts autonomously, and calibrates its own judgment. It's a cognitive partner, not a tool.

---

[Repository →](https://github.com/WingedGuardian/GENesis-AGI) · [Discord →](https://discord.com/invite/Zkc3XMQpJX) · License: MIT
