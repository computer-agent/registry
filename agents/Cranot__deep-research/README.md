# Deep Research

**Fractal exploration of any question through recursive AI agents.**

Deep Research is a multi-agent system that takes any question and transforms it into a comprehensive, synthesized report by recursively decomposing it. An orchestrator agent breaks the question into angles, each angle spawns sub-agents to investigate further, and everything synthesizes back up the tree into one authoritative answer.

## What it does

- **Recursive decomposition** — complex questions are broken into sub-questions automatically, to any depth
- **Parallel exploration** — all sub-agents run concurrently for fast results
- **Multi-model ensemble support** — use Claude, Gemini, Kimi, Grok, or Azure OpenAI at different tree levels
- **Four research strategies**: recursive, Socratic, perspective expansion, and web-grounded
- **Persistent checkpoints** — resume interrupted research from where it left off
- **Typed knowledge graphs** — every finding carries epistemic state (Unknown → Explored → Validated → Synthesized)

## Example usage

```bash
# Basic research (Claude opus orchestrator + haiku researchers)
deep-research research "What makes startups successful?"

# Socratic mode — improve the question first
deep-research socratic "How do I become more productive?"

# Perspective expansion
deep-research perspectives "What makes good leadership?"

# Grounded research with web search
deep-research research --strategy grounded_research "Current state of AI agents"

# Legacy bash (still works)
./deep-research.sh -m opus -r haiku -d 2 "Why do smart people make bad decisions?"
```

## Output

Reports save to `reports/YYYY-MM-DD-question-slug/SYNTHESIS.md` with individual agent outputs in `agents/`.

## Models supported

| Provider | Models |
|---|---|
| Claude | opus, sonnet, haiku |
| Gemini | flash, pro |
| OpenRouter | grok, grok-3, grok-4 |
| Kimi | kimi (free, best merger) |
| Azure OpenAI | gpt5-mini |

## Skills

| Skill | Description |
|---|---|
| `recursive_research` | Decompose → spawn parallel researchers → synthesize |
| `socratic` | Challenge assumptions, surface better questions |
| `perspective_expander` | Multi-angle analysis with blind spot detection |
| `grounded_research` | Web-verified, fact-checked answers |

Created by [Dimitris Mitsos](https://github.com/Cranot) & [AgentsKB.com](https://agentskb.com). MIT licensed.
