# OpenYak

OpenYak is a **local-first AI agent workbench** for desktop work. It runs entirely
on your own machine — no account, no hosted backend, no telemetry — and gives you a
hands-on AI assistant that can act on real files, run tools, and keep long, productive
threads going without losing context.

## What It Does

- **File understanding:** Works with DOCX, XLSX, PPTX, PDF, CSV, and local project
  folders. Upload a memo and get an executive brief; upload a budget workbook and get
  variance analysis with talking points.
- **Artifact workspace:** Generates reusable Markdown briefs, tables, diagrams,
  checklists, and structured outputs in a right-side panel, distinct from inline chat.
- **Tool execution:** Read, write, rename, and organise files with user-controlled
  permissions. Destructive actions require explicit confirmation.
- **Long-context work:** Multi-step office workflows stay coherent across many turns
  with automatic context compaction — analysis → plan → follow-up without restarting.
- **Multi-agent task batches:** Spawn focused child-agent tasks in parallel and collect
  an aggregated result back in the parent thread.
- **Local models:** Ollama (any model), Rapid-MLX (Apple Silicon), or any
  OpenAI-compatible local endpoint — fully offline when you want it.
- **BYOK cloud providers:** OpenRouter, OpenAI, Anthropic, Google, DeepSeek, Groq,
  Mistral, xAI, and more — requests go directly from your desktop to the provider.
- **Remote access:** Scan a QR code in settings to use your desktop agent from mobile
  via Cloudflare Tunnel.
- **Automations:** Schedule recurring cleanup, reporting, and file workflows.

## Key Capabilities at a Glance

| Task | Output |
|------|--------|
| Read a dense memo | Executive brief, risks, owners, next actions, send-ready email |
| Analyse a spreadsheet | Budget vs. actual variance, drivers, anomalies, talking points |
| Review a slide deck | Slide-by-slide story, evidence gaps, speaker notes, decision ask |
| Synthesise multiple files | One board brief reconciling memo, budget, deck, and PDF |
| Long follow-up thread | RACI, 30-day plan, agenda, follow-up drafts without restarting |

## Tech Stack

Built with **Tauri v2 + Rust** (desktop shell), **Next.js 15** (chat UI), and
**FastAPI + SQLite** (agent engine). Open source under Apache-2.0.

## Privacy

Files, conversations, memory, artifacts, and tool permissions are stored locally.
Cloud model requests go directly from your desktop to the provider you configure —
OpenYak does not proxy or retain model traffic.

## Getting Started

```bash
npm run dev:all   # starts backend on :8000 and frontend on :3000
```

See the [repository README](https://github.com/openyak/openyak) for full setup
instructions, including local model configuration and platform-specific notes.
