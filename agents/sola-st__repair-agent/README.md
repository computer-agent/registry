# RepairAgent

**RepairAgent** is an autonomous, LLM-powered agent that fixes bugs in Java projects without any human intervention. Given a buggy project and a failing test suite, it operates in a self-directed loop until all tests pass — or it exhausts its configured budget.

Published at [ICSE 2025](https://arxiv.org/abs/2403.17134), RepairAgent set the state of the art on the [Defects4J](https://github.com/rjust/defects4j) benchmark by correctly repairing **164 bugs**, surpassing all prior automated program repair tools.

## How it works

RepairAgent cycles through three states per bug:

1. **Understand the bug** — runs the failing tests, reads stack traces, forms root-cause hypotheses
2. **Collect fix context** — searches the codebase for relevant methods, imports, and similar patterns
3. **Try fixes** — generates patches (simple first: operator/literal/condition changes; complex next: structural rewrites), applies them, runs the full test suite, and iterates

The loop continues for up to `max_turns` iterations (default 40) until the fix passes or the budget runs out.

## Key capabilities

- 🔁 **Fully autonomous** — no prompting between steps; the agent decides its own next action
- ✅ **Test-driven** — a patch is only accepted when the full suite passes
- 🔬 **Multi-model** — supports OpenAI (`gpt-4o`, `gpt-4.1`, `gpt-5-*`) and Anthropic (`claude-sonnet-4`, `claude-opus-4`, `claude-haiku-4`)
- 🐳 **Docker-native** — runs in a container for fully reproducible environments
- 📊 **Cost-tracked** — monitors API spend per bug; respects a configurable budget cap

## Example usage

```bash
# Interactive guided mode
cd repair_agent
python3 repairagent.py

# Direct mode (no prompts)
python3 repairagent.py run --bugs "Chart 1, Math 5" --model claude-sonnet-4-20250514

# Docker mode
python3 repairagent.py run --docker --bugs "Chart 1" --model gpt-4o-mini
```

## GAP files

- [`agent.yaml`](https://github.com/sola-st/RepairAgent/blob/gitagent-protocol/agent.yaml) — standard GAP manifest
- [`SOUL.md`](https://github.com/sola-st/RepairAgent/blob/gitagent-protocol/SOUL.md) — agent persona and operating instructions

## Citation

```bibtex
@inproceedings{bouzenia2025repairagent,
  title     = {RepairAgent: An Autonomous, LLM-Based Agent for Program Repair},
  author    = {Bouzenia, Islem and Devanbu, Premkumar and Pradel, Michael},
  booktitle = {ICSE 2025},
  year      = {2025},
  url       = {https://arxiv.org/abs/2403.17134}
}
```

Repository: https://github.com/sola-st/RepairAgent
