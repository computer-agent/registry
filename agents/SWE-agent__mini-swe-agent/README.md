# mini-swe-agent

**The minimal AI software engineering agent** — ~100 lines of Python, no custom tools, just bash.

Built by the Princeton & Stanford team behind [SWE-bench](https://swebench.com) and [SWE-agent](https://swe-agent.com),
`mini-swe-agent` asks: *what if our agent was 100x simpler, and still worked nearly as well?*

## What it does

`mini` resolves GitHub issues, writes and edits code, and assists with any command-line task
by iteratively reasoning and executing bash commands. It scored **>74% on SWE-bench Verified**
with Gemini 3 Pro — rivalling far more complex agents.

## Key capabilities

- 🐚 **Bash-only** — no tool-calling API needed; works with literally any LLM
- 📦 **Multi-environment** — local, Docker/Podman, Singularity, bubblewrap, contree
- 🤖 **Any model** — powered by [litellm](https://github.com/BerriAI/litellm); OpenAI, Anthropic, Gemini, open-source via openrouter
- 📈 **Linear trajectory** — every step appends to history; great for debugging & fine-tuning
- ⚡ **Fast startup** — lighter than Claude Code, zero config required to start

## Quick start

```bash
pip install mini-swe-agent
mini  # launches the interactive CLI
```

Or run without installing:

```bash
pip install uv && uvx mini-swe-agent
```

## Example usage

```python
from minisweagent.agents.default import DefaultAgent
from minisweagent.models.litellm_model import LitellmModel
from minisweagent.environments.local import LocalEnvironment

agent = DefaultAgent(
    LitellmModel(model_name="claude-sonnet-4-5"),
    LocalEnvironment(),
)
agent.run("Fix the failing tests in src/utils.py")
```

## Benchmarks

| Model | SWE-bench Verified |
|---|---|
| Gemini 3 Pro | >74% |
| GPT-5 / Sonnet 4 (random switch) | boosted performance |

## Adopted by

Meta, NVIDIA, Essential AI, IBM, Nebius, Anyscale, Princeton University, Stanford University, and many more.

## Links

- 📚 [Documentation](https://mini-swe-agent.com/latest/)
- 🐙 [GitHub](https://github.com/SWE-agent/mini-swe-agent)
- 📦 [PyPI](https://pypi.org/project/mini-swe-agent/)
- 🏆 [SWE-bench Leaderboard](https://www.swebench.com/)
