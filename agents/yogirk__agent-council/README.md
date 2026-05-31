# Agent Council

**Convene a panel of CLI-based AI agents to deliberate on your hardest engineering questions.**

Agent Council orchestrates Claude Code, Codex CLI, and Gemini CLI through a structured
three-stage deliberation — independent opinions, peer review, and chairman synthesis — then
delivers a verdict with consensus mapping, divergence analysis, and a confidence score.

## What makes it different

Every existing LLM council is API-based (pass text, get text back). Agent Council is
different: council members are **CLI agents with tool access**. They can grep your codebase,
read migration files, and run `git log` before opining. Opinions are grounded in your
actual project, not abstract text generation.

You're also tapping into **subscriptions you already have** — no new API tokens required.

## Key Capabilities

- **`/council "question"`** — Dispatch all agents in parallel, collect independent opinions, synthesise as chairman
- **`/council --with-review`** — Add a Stage 2 peer-review round before synthesis
- **`/council --quick`** — Skip peer review for fast turnaround
- **`/council-list`** — List all past deliberation sessions
- **`/council-replay <session>`** — Replay a past session in the terminal
- **`/council-revisit <session>`** — Re-run deliberation with current project context ("living decisions")
- **`/council-outcome <session> "result"`** — Record what actually happened to close the loop
- **`/council-nudge <session> --agent codex --correction "..."`** — Dispatch a targeted Stage 4 correction to a single agent

## Example

```
/council "Should we use Postgres or DynamoDB for our event sourcing system?"
```

```
Stage 1 complete: 3/3 successful opinions

--- CHAIRMAN SYNTHESIS (claude) ---

Consensus: All agents agree — Postgres is the right choice given strong
consistency requirements and team SQL experience.

Divergence: Claude emphasises ACID guarantees. Codex flags a 10TB scaling
ceiling without sharding. Gemini suggests read replicas as a scaling bridge.

Confidence: HIGH — Strong consensus across models.
```

## Installation

```bash
npx cliagent-council
```

Or manually:

```bash
git clone https://github.com/yogirk/agent-council.git
cd agent-council && ./setup
```

**Requirements:** [Bun](https://bun.sh) + at least 2 of: Claude Code, Codex CLI, Gemini CLI.

## GitAgent Protocol

This agent ships with `agent.yaml` + `SOUL.md` at the repo root, making it fully
[GAP-compliant](https://gitagent.sh). Run it on any compatible runtime or list it
in the [Open GAP registry](https://registry.gitagent.sh).
