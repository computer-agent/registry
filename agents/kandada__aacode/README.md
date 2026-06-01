# AACode

A lightweight, 100%-Python CLI coding agent built on a **ReAct (Reason + Act) loop**. Give it a task in plain language — it plans, writes code, runs it, reads the errors, fixes them, and ships a working result. No manual prompt engineering needed.

---

## Run

```bash
npx @open-gitagent/gitagent run -r https://github.com/kandada/aacode
```

---

## What It Can Do

- **Autonomous coding** — Write, run, debug, and verify code end-to-end, with TDD loops that don't quit until tests pass
- **Multi-step task planning** — Builds a live TODO list, updates it as work progresses, and verifies each item before marking it done
- **Shell access** — Runs arbitrary shell commands, installs dependencies, writes scripts, and interprets output
- **Web search & fetch** — Searches via SearXNG and fetches URLs for real-time information during coding tasks
- **Sub-agent delegation** — Spawns isolated sub-agents for sub-tasks that would crowd the main context window
- **Multimodal input** — Understands screenshots, UI mockups, and images to generate matching code
- **Extensible skills** — pandas, numpy, Playwright, and user-defined skills auto-loaded from `skills/`
- **MCP integration** — Connects to any MCP server via stdio or SSE

## Provider-agnostic

Works with **DeepSeek** (default), OpenAI GPT-4, Anthropic Claude, Kimi K2.5, Gemini, and any OpenAI-compatible API. Switch providers with three env vars — no code changes.

```bash
export LLM_API_KEY="your-key"
export LLM_API_URL="https://api.deepseek.com/v1"
export LLM_MODEL_NAME="deepseek-chat"
aacode run -p ./my-project "Add unit tests for all public functions"
```

## Quick start

```bash
pip install aacode
aacode init          # configure LLM provider
aacode run -p /your/project "your task"
```

---

## Built with
[gitagent](https://github.com/open-gitagent/gitagent) — a git-native, framework-agnostic open standard for AI agents.
