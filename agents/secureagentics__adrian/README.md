# Adrian — Runtime Security Monitor for AI Agents

**Adrian** is an open-source, [AARM-aligned](https://aarm.dev) runtime security monitoring and control engine for AI agents. It watches every tool call, API interaction, and reasoning trace in real time — detecting malicious, misaligned, or out-of-remit behaviour before or as it happens.

## What It Does

Most agent monitors watch *what* an agent does (activity logs). Adrian also watches *why* — correlating an agent's reasoning traces with its actions to give ~35% better detection accuracy than behaviour-only approaches (per OpenAI / DeepMind research, 2025).

**Key capabilities:**

- 🔍 **Prompt injection detection** — catches attempts to hijack or redirect the agent mid-session
- 🛠️ **Tool-call auditing** — every MCP call, API hit, DB write, and file operation is logged and classified
- 🧠 **Reasoning-trace analysis** — understands *why* the agent took an action, not just *what* it did
- 🚨 **Policy-drift detection** — flags when an agent starts operating outside its configured remit
- 🛑 **In-flight intervention** — runs in *audit* (log + alert) or *block* (halt before execute) mode
- 🏠 **Self-hostable** — full stack (Go backend + Next.js dashboard + Llama.cpp Gemma classifier) on a single Docker host, no external telemetry

## Quick Install

```python
pip install adrian-sdk

import adrian
from langchain_openai import ChatOpenAI

adrian.init(api_key="adr_live_...")
llm = ChatOpenAI(model="gpt-4o")
response = await llm.ainvoke("your agent prompt here")
adrian.shutdown()
```

That's it — all LangChain / LangGraph calls are automatically instrumented. Events appear in the dashboard within seconds.

## Self-Hosting

Adrian ships a complete Docker Compose stack with a Go backend, Next.js dashboard, and a local Llama.cpp container running Gemma 4 (E2B / E4B). No cloud dependency. No telemetry leaving the box.

```sh
git clone https://github.com/secureagentics/Adrian
cd Adrian
docker compose --profile setup run --rm setup bootstrap
docker compose --profile llm up -d
```

## Why Adrian?

Most monitoring tools in this space are ML classifiers trained on labelled prompt-injection datasets. Adrian uses world-model reasoning: it holds a working understanding of what the agent is *supposed* to be doing and assesses each new action against that. If your e-commerce agent starts resetting passwords, that's a flag — even if it has never appeared in any training data.

## Links

- 📖 [Documentation](https://docs.adrian.secureagentics.ai)
- 📊 [Managed Dashboard](https://app.adrian.secureagentics.ai)
- 🐍 [PyPI — adrian-sdk](https://pypi.org/project/adrian-sdk/)
- 💬 [Discord](https://discord.gg/6nmJ9k3u6)
- 🔗 [GitHub](https://github.com/secureagentics/Adrian)
