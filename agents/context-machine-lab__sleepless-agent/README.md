# Sleepless Agent

**A 24/7 AgentOS that keeps working while you sleep — powered by Claude Code.**

> Repo: https://github.com/context-machine-lab/sleepless-agent

## What it does

Sleepless Agent is a persistent background daemon that transforms your Claude Code
Pro subscription into a continuously-running AI development assistant. Instead of
leaving your allocation idle overnight, it picks up tasks and executes them
autonomously, surfacing the results as GitHub PRs for your morning review.

## Key capabilities

| Capability | Description |
|---|---|
| **Slack + CLI interface** | Submit tasks via `/think` in Slack or the `sle` CLI — no browser needed |
| **Multi-agent pipeline** | Every task flows through a Planner → Worker → Evaluator chain |
| **Isolated workspaces** | Each task runs in its own directory; parallel tasks never collide |
| **Auto task generation** | During idle windows the agent brainstorms and self-assigns new work |
| **Budget-aware scheduling** | Separate day/night Claude usage thresholds prevent quota exhaustion |
| **Git-native output** | Completed work lands on a feature branch with an auto-opened PR |

## Example usage

```bash
# Install
pip install sleepless-agent

# Start the 24/7 daemon
sle daemon

# Submit a task (Slack or CLI)
sle add "Refactor the auth module to use JWT"

# Check status
sle check

# Read a result
sle report 42
```

## Architecture

```
Slack / CLI  →  Task Queue (SQLite)  →  Smart Scheduler
                                              │
                              ┌───────────────┴───────────────┐
                          Planner                          Auto-Generator
                              │
                           Worker  ←── isolated workspace
                              │
                          Evaluator  →  Git commit  →  PR
```

## Model

Uses `claude-sonnet-4-5-20250929` via the Claude Code Python Agent SDK with a
30-turn worker budget and a 1800-second per-task timeout.

## License

MIT — see [LICENSE](https://github.com/context-machine-lab/sleepless-agent/blob/main/LICENSE)
