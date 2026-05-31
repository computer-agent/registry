# claude-code-hermit

> Turn Claude Code into a 24/7 personal AI assistant — self-learning, cost-aware, and operator-gated.

**claude-code-hermit** is a Claude Code plugin that wires Claude's native scheduling, messaging channels, remote control, and memory system into a fully autonomous personal assistant you deploy on your own machine or in Docker. One Claude subscription powers multiple independent hermits — each with its own memory, budget, and routines.

---

## Run

```bash
npx @open-gitagent/gitagent run -r https://github.com/gtapps/claude-code-hermit
```

---

## Install

```bash
cd /path/to/your/project
claude plugin marketplace add gtapps/claude-code-hermit
claude plugin install claude-code-hermit@claude-code-hermit --scope project

# Boot and run the setup wizard
claude /claude-code-hermit:hatch

# Go always-on with Docker
claude /claude-code-hermit:docker-setup
```

---

## What It Can Do

- **Always-on autonomy** — Runs on scheduled routines (morning brief, evening summary, heartbeat checks) via Claude Code's native `/loop` and `CronCreate`. Restarts automatically after sleep and network drops.
- **Self-learning with operator control** — Reflects on session journals, identifies recurring patterns, and proposes improvements. Two subagents (`reflection-judge`, `proposal-triage`) vet candidates before they reach you. You approve via `/proposal-act accept <ID>` — nothing is applied without your say.
- **Discord & Telegram channels** — Send commands and receive results via DM, exactly as if you were at the terminal. Powered by Claude Code's native Channels plugin.
- **Cost transparency** — Every LLM call logged to `.claude/cost-log.jsonl`. Per-session totals in `.status.json`. Per-day rollup in `cost-summary.md`. Morning brief includes yesterday's spend. Soft `idle_budget` cap with a warning at 80%.
- **Local & self-hosted** — Runs on bare tmux or Docker. Data stays on your hardware. No telemetry, no external dependencies beyond your Claude subscription.
- **Hardened Docker baseline** — `cap_drop: ALL`, `no-new-privileges`, `pids_limit`. Opt-in `/docker-security` wizard adds LAN containment, DNS allowlist sidecar, and resource bounds.
- **Observability skills** — `/hermit-brain` (open loops, fragile zones), `/hermit-evolution` (cost trends, behavioral shifts), `/hermit-health` (alert state, channel status, heartbeat).

## Pre-built Domain Hermits

Stack domain plugins on top of any hatched hermit:

- **`dev-hermit`** — Safety layer for code-writing: push guard, branch discipline, gated PRs.
- **`homeassistant-hermit`** — Home Assistant skills, automation builder, Python CLI.
- **`fitness-hermit`** — Strava MCP wiring, activity deep-dives, weekly-load routines.

## Architecture Highlights

- **Voyager-style curriculum** — Raw session journals distill into compiled artifacts (`MEMORY.md` + domain files) that reload next session. The operator is editor-in-chief.
- **Three-condition rule** — A pattern becomes a proposal only if it recurred, had a meaningful consequence, and admits a concrete actionable change. Noise is filtered before it reaches the inbox.
- **`OPERATOR.md` as policy** — The `/hatch` wizard generates a personal rulebook capturing your priorities, constraints, and approval gates. The hermit reads it every session.

## Links

- [GitHub](https://github.com/gtapps/claude-code-hermit)
- [Full Documentation](https://github.com/gtapps/claude-code-hermit/tree/main/plugins/claude-code-hermit/docs)
- [Changelog](https://github.com/gtapps/claude-code-hermit/blob/main/plugins/claude-code-hermit/CHANGELOG.md)
