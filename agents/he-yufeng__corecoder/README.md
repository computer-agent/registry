# CoreCoder

**CoreCoder** is a minimal, readable AI coding agent built in ~1,400 lines of Python. Think of it as the [nanoGPT](https://github.com/karpathy/nanoGPT) of coding agents — every key architectural pattern from Claude Code, distilled into a codebase you can read in one afternoon.

## What It Does

CoreCoder runs as an interactive REPL or one-shot CLI in your terminal, helping with:

- **Code editing** — search-and-replace with unique-match guarantee and diff output
- **File management** — read, write, glob, and grep across your project
- **Safe shell execution** — runs commands with dangerous-command blocking
- **Context compression** — 3-layer compression (HISTORY_SNIP → Microcompact → CONTEXT_COLLAPSE) to keep sessions running long
- **Sub-agent spawning** — isolated sub-agent with its own context window for complex tasks
- **Session persistence** — save and resume sessions across restarts

## Key Architecture Patterns

| Pattern | CoreCoder |
|---|---|
| Search-and-replace editing | `tools/edit.py` — 70 lines |
| Parallel tool execution | `agent.py` — ThreadPool |
| 3-layer context compression | `context.py` — 145 lines |
| Sub-agent with isolated context | `tools/agent.py` — 50 lines |
| Dangerous command blocking | `tools/bash.py` — 95 lines |
| Session persistence | `session.py` — 65 lines |
| Dynamic system prompt | `prompt.py` — 35 lines |

## Model Support

Works with any OpenAI-compatible API endpoint — Claude (via OpenRouter), GPT-4o, DeepSeek, Qwen, Kimi, local Ollama models. Install the optional LiteLLM extra for 100+ providers including Bedrock and Vertex.

## Install

```bash
pip install corecoder
export OPENAI_API_KEY=your-key
corecoder -m gpt-4o
```

## Example Usage

```
$ corecoder -m kimi-k2.5

You > read main.py and fix the broken import

  > read_file(file_path='main.py')
  > edit_file(file_path='main.py', ...)

Fixed: halper → helper.
```

## Links

- **Repository:** https://github.com/he-yufeng/CoreCoder
- **PyPI:** https://pypi.org/project/corecoder/
- **Architecture deep-dive (7 articles):** https://github.com/he-yufeng/CoreCoder/tree/main/article
