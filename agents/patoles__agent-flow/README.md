# Agent Flow

**Real-time visualization of Claude Code and Codex agent orchestration.**

Agent Flow makes the invisible visible: as Claude Code or Codex executes, it renders every tool call, sub-agent spawn, and coordination step as a live, interactive node graph in your browser or VS Code side panel.

## Key Capabilities

- **Live node graph** — watch agent execution unfold as an interactive canvas you can pan, zoom, and click to inspect individual tool calls
- **Multi-runtime support** — auto-detects Claude Code (via HTTP hooks) and Codex (via JSONL rollout tailing) concurrently, shown side-by-side
- **Multi-session tracking** — manage multiple concurrent agent sessions with tabs, each tagged by runtime
- **Timeline & transcript panels** — review the full execution timeline, file attention heatmap, and message transcript for any session
- **JSONL log replay** — point at any `.jsonl` event log to replay or tail historical agent activity
- **Zero-config startup** — `npx agent-flow-app` in one terminal, run your agent in another; events stream in real time

## Usage

```bash
# Quickest path — no install required
npx agent-flow-app

# Then start a Claude Code session in another terminal
claude "build me a REST API"
```

Or install the VS Code extension and open **Agent Flow** from the Command Palette (`Cmd+Shift+P`).

## Why It Exists

Debugging AI agent behavior is hard when all you see is the final output. Agent Flow was built out of real pain — tracing what went wrong in a multi-agent game-creation platform — and open-sourced so every developer working with AI agents can benefit.

## Links

- GitHub: https://github.com/patoles/agent-flow
- Demo: https://www.youtube.com/watch?v=Ud6eDrFN-TA
- License: Apache-2.0
