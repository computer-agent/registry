# DevAssistant

**DevAssistant** is a personal, task-driven autonomous agent by [@Saik0s](https://github.com/Saik0s) that helps developers achieve complex objectives without hand-holding every step.

## What it does

Given a single high-level goal (e.g. *"scaffold a FastAPI service with JWT auth and write tests"*), DevAssistant:

1. **Decomposes** the objective into prioritised milestones using GPT-4
2. **Executes** each task with a rich tool-set — Python REPL, Bash, file I/O, web scraping, GitHub integration, DuckDuckGo search
3. **Remembers** results in a local FAISS semantic memory so later tasks can build on earlier ones
4. **Evaluates** whether the objective is fully achieved after every cycle
5. **Iterates** — generates new tasks, re-prioritises, and continues until done

It is particularly suited for tasks whose output is a set of files: code generation, research reports, project scaffolding, and migrations.

## Key capabilities

- Milestone-based task decomposition (`ReasoningModule`)
- Multi-tool execution with guardrails (`ExecutionModule`)
- Semantic memory retrieval (`MemoryModule` + FAISS)
- Iterative self-evaluation and loop termination (`EvaluationModule`)
- Runs safely inside Docker (`make docker`) — recommended for file-system-modifying tasks

## Example usage

```bash
# Install dependencies
make install

# Run with an objective
python -m main --obj "Create a Python script that fetches the top 10 Hacker News stories and saves them to stories.json"

# Run inside Docker (recommended for destructive tasks)
make docker
```

## Requirements

- Python 3.11+
- OpenAI API key (`OPENAI_API_KEY`)

## Links

- [Repository](https://github.com/Saik0s/DevAssistant)
- [GitAgent Protocol](https://gitagent.sh)
