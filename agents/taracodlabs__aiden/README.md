# Aiden — Autonomous AI OS

Aiden is a local-first, autonomous AI operating system built by [Shiva Deore at Taracod](https://aiden.taracod.com). It runs on Windows, Linux, and WSL with 72 built-in tools spanning browser automation, desktop GUI control, code execution, voice I/O, file management, multi-agent coordination, and real-time data (stocks, email, calendar) — all on-device.

## Key Capabilities

- **72 built-in tools** — shell, Python, Node.js, PowerShell, browser automation (Playwright), desktop mouse/keyboard control, voice TTS/STT
- **19 LLM providers** — Groq, Anthropic Claude, OpenAI, Gemini, Mistral, Ollama (local offline fallback), and more via OpenRouter
- **Multi-agent coordination** — `spawn`, `swarm`, `spawn_subagent` for parallel task execution
- **Persistent semantic memory** — remembers facts and patterns across sessions with SQLite FTS5
- **Active learning** — Skill Teacher, Pattern Detector, and Task Tracker for self-improvement
- **9 channels** — Discord, Slack, Telegram, Email, Webhook, CLI, and more
- **Security hardening** — jailbreak detection, destructive-action confirmation, local-only data governance

## Try It

```bash
# Install via npm
npm install -g aiden-runtime
aiden start
```

Or clone and run:
```bash
git clone https://github.com/taracodlabs/aiden.git
cd aiden && npm install
npm start
```

## Architecture

Aiden uses a hybrid approach: all tool execution, file I/O, and memory stay on-device; only LLM inference prompts go to the cloud provider (or Ollama for fully offline use). The `SOUL.md` is prepended to every system prompt at startup, defining identity and behaviour rules that cannot be overridden by user messages.

## Links

- 🌐 Website: https://aiden.taracod.com
- 💬 Discord: https://discord.gg/CU5wshJW4F
- 📦 npm: https://www.npmjs.com/package/aiden-runtime
- 📖 Docs: https://github.com/taracodlabs/aiden/tree/main/docs
