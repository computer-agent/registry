# DM-Code-Agent

A local-first, auditable Python code-maintenance agent built on a **ReAct + Task Planner + Adaptive Replanning** loop. Every plan, tool call, and observation is written to a structured JSONL trace for offline replay and diff — no black-box magic.

The entire core fits in ~1,500 lines of readable Python, making it a rare agent you can actually read, reproduce, and benchmark against.

---

## Run

```bash
npx @open-gitagent/gitagent run -r https://github.com/hwfengcs/DM-Code-Agent
```

---

## What It Can Do

- **Bug fixing** — Locates and fixes small-to-medium bugs, then runs the test suite to verify
- **Regression testing** — Adds tests that cover more than just the visible failure case
- **Code analysis** — Analyzes project structure, function signatures, dependencies, and metrics via AST tools
- **Refactoring** — Performs small refactors or documentation-consistency fixes with file constraints
- **Trace & benchmark reports** — Produces JSONL traces with dry-replay, tool-replay, and offline diff for agent quality auditing

## Key Capabilities

| Capability | Description |
|---|---|
| ReAct Loop | `thought / action / action_input` loop with per-step observation injection |
| Task Planner | 3-8 step plan generated before execution; auto-replanning on failure |
| JSONL Trace | Structured trace of every plan, tool call, LLM summary, and result — replayable offline |
| Reflexion | Extracts failure lessons from prior trials and injects into the next (default-off) |
| Critic | Peer-review gate before solution acceptance (default-off) |
| Self-Consistency | N-way independent selection by majority-vote, critic score, or test-pass (default-off) |
| Adaptive Replanning | Error-signal-to-strategy mapping with token-economics reporting (default-off) |
| Context Memory | Mem0-style atomic memory compression — episodic, semantic, procedural |
| MCP Integration | Attach Playwright, Context7, filesystem, SQLite, and other MCP servers |
| Multi-LLM | DeepSeek, OpenAI (GPT-4o), Claude, Gemini, custom `base_url` |
| Skill System | Domain-specific prompts and tools activated by task signals |
| Maintenance Benchmarks | Hidden-test suite with changed-file constraints and trace analysis |

## Example Usage

```bash
# Install
git clone https://github.com/hwfengcs/DM-Code-Agent.git
cd DM-Code-Agent
python -m venv .venv && source .venv/bin/activate
pip install -e ".[dev]"
cp .env.example .env  # add your API key

# Run a task
dm-agent "Fix the retry boundary in retry.py and run the tests" \
  --provider deepseek \
  --trace traces/retry-fix.jsonl \
  --show-steps

# Inspect the trace
dm-agent-trace analyze traces/retry-fix.jsonl
dm-agent-trace diff traces/baseline.jsonl traces/retry-fix.jsonl
```

## Why It Stands Out

- **Auditable by design** — traces record everything; debug without asking the model again
- **Benchmarked** — ships with coding and maintenance hidden-test suites; SWE-bench Lite Tier-1 baseline published
- **Algorithmic** — Reflexion, Critic, Self-Consistency, and Adaptive Replanning are modular, tested, default-off capabilities — not marketing
- **Tiny core** — ~1,500 LOC vs. ~10k–50k for comparable tools; readable and extensible

## License

MIT — see [LICENSE](https://github.com/hwfengcs/DM-Code-Agent/blob/main/LICENSE)
