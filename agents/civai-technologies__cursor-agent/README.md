# Cursor Agent

**cursor-agent** is a Python-based AI coding assistant that replicates the core experience of Cursor's coding IDE assistant — but as a fully programmable, embeddable library.

## What it does

- **Code generation** — produce complete, functional code from natural language descriptions
- **Precise file editing** — line-based surgical edits to existing files (no full rewrites)
- **Code analysis** — review files for bugs, optimizations, and improvements
- **Semantic search** — `codebase_search` finds relevant code snippets across the project
- **Web search** — `web_search` and `trend_search` for up-to-date information
- **Image analysis** — `query_images` for analyzing screenshots, diagrams, and code screenshots
- **Terminal commands** — `run_terminal_cmd` with a configurable permission gate
- **Conversational context** — maintains history for coherent multi-turn sessions
- **Custom tools** — register your own Python functions at runtime via `agent.register_tool()`

## Multi-model support

Works with any of:
- **Anthropic Claude** (`claude-3-5-sonnet-latest`, `claude-opus` etc.)
- **OpenAI GPT** (`gpt-4o`, `gpt-4` etc.)
- **Ollama** — any locally hosted model (`ollama-llama3`, `ollama-mistral`, `ollama-gemma3` etc.)

## Permission system

All destructive operations (file deletion, terminal commands) require explicit user approval by default. YOLO mode with command allowlists/denylists is available for automation workflows.

## Quick start

```bash
pip install cursor-agent-tools
```

```python
import asyncio
from cursor_agent_tools import create_agent

async def main():
    agent = create_agent(model='claude-3-5-sonnet-latest')
    response = await agent.chat("Create a Python function to calculate Fibonacci numbers")
    print(response)

asyncio.run(main())
```

## Links

- **Repository**: https://github.com/civai-technologies/cursor-agent
- **Author**: Femi Amoo (Nifemi Alpine) — [CIVAI Technologies](https://civai.co)
- **License**: MIT
