# KiLee Agent

**KiLee** is a DeepSeek-powered terminal AI agent that lets you read and write
files, run shell commands, search the web, and keep a persistent memory — all
from your command line.

## What it does

- 📁 **File operations** — read, write, edit, list directories, grep content
- 💻 **Shell execution** — run any bash command with risk-based approval
- 🌐 **Web** — search and fetch page content for up-to-date answers
- 🧠 **Memory** — save facts and preferences across sessions (`~/.kilee/memory.json`)
- 🗜️ **Context compression** — auto-compresses long conversations to preserve tokens
- 🔌 **Multi-provider** — DeepSeek (default), OpenAI, Groq, OpenRouter, or any
  OpenAI-compatible endpoint

## Installation

```bash
git clone https://github.com/Yunle-Lee/KiLee-agent.git
cd KiLee-agent
pip install -e .
kilee         # launches setup wizard on first run
```

## Usage

```bash
kilee                        # interactive chat
kilee setup                  # configure API key and model
kilee whoami                 # show current config
```

Ask KiLee anything. It will use its tools to act, not just describe.

## Context Engineering

Drop a `KILEE.md` file in your project root — KiLee automatically injects it
into every session, giving it immediate awareness of your codebase, stack, and
conventions.

## License

MIT — [GitHub](https://github.com/Yunle-Lee/KiLee-agent)
