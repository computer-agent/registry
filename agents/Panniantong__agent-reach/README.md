# Agent Reach

**Give your AI agent eyes to see the entire internet.**

Agent Reach is a unified read/search routing layer that gives any AI agent access to 17+ internet platforms with zero API fees and minimal configuration. It works as a CLI tool, Python library, and MCP server — compatible with Claude Code, OpenClaw, Cursor, Windsurf, and any agent that can run shell commands.

## What It Does

Instead of juggling separate accounts, API keys, and platform-specific wrappers, you give your agent one install command and it can:

- 🌐 **Read any URL** — via Jina Reader (clean Markdown, no HTML noise)
- 🐦 **Twitter/X** — read tweets, search discussions, browse timelines (free, no API key)
- 📖 **Reddit** — search posts, read threads and comments
- 📺 **YouTube** — extract transcripts/subtitles, search videos (via yt-dlp)
- 📦 **GitHub** — read repos, issues, PRs, search code
- 📺 **Bilibili** — extract subtitles, search videos
- 📕 **XiaoHongShu (小红书)** — search notes, read content
- 💼 **LinkedIn** — read public profiles, job listings
- 📡 **RSS/Atom** — read any feed
- 💬 **WeChat Official Accounts** — search and read articles
- 📰 **Weibo** — trending topics, user feeds
- 💻 **V2EX** — posts, comments, user info
- 📈 **Xueqiu** — stock quotes, financial discussions
- 🎵 **Douyin** — video info and download links
- 🎙️ **Podcasts** — audio-to-text transcription via Whisper

## Key Features

| Feature | Details |
|---------|---------|
| 💰 **Zero API fees** | All backends are free open-source tools (yt-dlp, bird CLI, rdt-cli, Jina Reader) |
| 🔒 **Privacy-first** | Cookies stored locally only, never transmitted |
| 🩺 **Self-diagnosing** | `agent-reach doctor` tells you exactly what works and how to fix what doesn't |
| 🤖 **Runtime-agnostic** | CLI, Python library, MCP server, or OpenClaw skill |
| 🔄 **Self-updating** | `agent-reach install --env=auto` keeps upstream tools current |

## Quick Start

Pass this to your agent:
```
Install Agent Reach: https://raw.githubusercontent.com/Panniantong/agent-reach/main/docs/install.md
```

That's it. The agent handles installation, configuration, and self-diagnosis.

## Example Usage

```bash
# Read any URL
agent-reach read https://twitter.com/username/status/123

# Search Twitter
agent-reach search-twitter "LLM benchmarks 2025"

# Get YouTube transcript
agent-reach read https://youtube.com/watch?v=xxxxx

# Search Reddit
agent-reach search-reddit "rust async runtime comparison"

# Run diagnostics
agent-reach doctor
```

## Installation

```bash
pip install agent-reach
agent-reach install --env=auto
```

## MCP / OpenClaw Integration

Agent Reach ships with a `SKILL.md` at `agent_reach/skill/SKILL.md` for direct OpenClaw skill integration, and an MCP server at `agent_reach/integrations/mcp_server.py` for MCP-compatible runtimes.

## Links

- **GitHub**: https://github.com/Panniantong/Agent-Reach
- **PyPI**: https://pypi.org/project/agent-reach/
- **English docs**: https://github.com/Panniantong/Agent-Reach/blob/main/docs/README_en.md
