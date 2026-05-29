# Boop — iMessage Personal AI Agent

**Boop** is a personal AI agent you text from iMessage. It uses the Claude Agent SDK (or Codex/ChatGPT runtime) and runs on your existing subscription — no separate API key needed.

## What it does

Boop is built around a **dispatcher + workers** pattern:

- A lean **interaction agent** reads your iMessage, recalls relevant memories, then decides: answer directly (greetings, clarifications) or spawn a focused sub-agent (anything that needs the real world).
- **Execution sub-agents** are spawned per task. Each gets a crisp job description, runs WebSearch/WebFetch and any integrations you've connected, then returns a concise result the interaction agent relays in its own warm voice.

## Key capabilities

| Feature | Detail |
|---|---|
| **Tiered memory** | Short / long / permanent tiers with decay + daily adversarial consolidation |
| **Automations** | Schedule recurring tasks from plain text ("every morning at 8, summarise my calendar") |
| **Draft-and-confirm** | Any irreversible action (send email, post Slack) is staged as a draft first |
| **Composio integrations** | One API key → 1000+ toolkits: Gmail, Slack, GitHub, Notion, Linear, Stripe, Supabase, etc. |
| **Optional browser use** | Local Patchright Chrome for login-only portals and JS-heavy services |
| **Debug dashboard** | React + Vite UI — Agents, Automations, Memory graph, Connections |
| **Vector search** | Embedding-backed recall (Voyage / OpenAI), falls back to substring |

## Architecture

```
iMessage → Sendblue webhook → Interaction agent → Execution agent(s)
                                      │                  │
                                      ▼                  ▼
                               Convex (memory,    Composio / MCP tools
                               automations,       WebSearch / WebFetch
                               drafts, logs)      Optional local browser
```

## Getting started

```bash
git clone https://github.com/raroque/boop-agent.git
cd boop-agent
npm install
# Follow the setup wizard:
npm run setup
```

You'll need accounts for: Claude Code (or Codex), Sendblue (iMessage bridge), Convex (database), and optionally Composio (integrations).

## Example interactions

> **You:** "Add a reminder to call my dentist next Tuesday at 3pm"  
> **Boop:** "Done — I'll nudge you Tuesday at 3 PM. Your dentist is Dr. Chen, right?"

> **You:** "Every weekday at 9am, pull my top 3 emails and summarise them"  
> **Boop:** "Automation created. I'll boop you at 9 AM on weekdays with your morning inbox snapshot."

## License

MIT — template/starter project, open for extension.
