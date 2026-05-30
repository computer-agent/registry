# LLM

**LLM** is a CLI tool and Python library by [Simon Willison](https://github.com/simonw) for running prompts, chatting, and working with Large Language Models — all from a single, consistent interface.

## What it does

- **Run prompts** from the command-line against any supported model:
  ```bash
  llm "Explain the CAP theorem in plain English"
  llm -m claude-4-opus "Review this PR" < diff.txt
  ```
- **Multi-turn chat** sessions:
  ```bash
  llm chat -m gemini-2.0-flash
  ```
- **Tool use** — register Python functions and let the model call them during inference.
- **Structured output** — extract typed JSON with `llm -s "..." --schema '...'`.
- **Embeddings** — generate and store vectors for semantic search.
- **Templates** — save named system prompts: `llm -t my-template`.
- **Plugin system** — extend model support: `llm install llm-anthropic`.
- **Automatic logging** — every prompt/response stored in SQLite, queryable with `llm logs`.

## Key capabilities

| Skill | Command |
|-------|---------|
| One-shot prompt | `llm "..."` |
| Interactive chat | `llm chat` |
| Embeddings | `llm embed` |
| Log viewer | `llm logs` |
| Plugin management | `llm install` |
| Key management | `llm keys set <provider>` |

## Models supported

Works with OpenAI (gpt-4o, gpt-4o-mini), Anthropic Claude (via plugin), Google Gemini (via plugin), local models via Ollama, llama.cpp, MLX, and dozens more through the plugin ecosystem.

## Install

```bash
pip install llm
# or
brew install llm
```

## Links

- 📦 PyPI: https://pypi.org/project/llm/
- 📖 Docs: https://llm.datasette.io
- 🐙 GitHub: https://github.com/simonw/llm
