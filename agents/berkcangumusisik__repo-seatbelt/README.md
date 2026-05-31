# repo-seatbelt

A four-layer safety system that stands between AI coding agents and the irreversible parts of your repository.

## What it does

**repo-seatbelt** scans your project, computes an AI Safety Score (0–100), and generates safety rule files for 8 AI tools simultaneously — Claude Code, Cursor, Codex, Gemini CLI, Windsurf, Aider, Cline, and Zed. It also ships a live MCP guardrail server, a pre-commit hook, and a GitHub Action CI gate.

### Four layers of protection

| Layer | What it does |
|-------|-------------|
| **Static rules** | Generates `CLAUDE.md`, `AGENTS.md`, `.cursorrules`, `.windsurfrules`, `CONVENTIONS.md`, `.clinerules`, `.rules` so agents know your boundaries on session start |
| **Runtime MCP guardrail** | A live MCP server agents call at decision-time: `check_file_access`, `check_command`, `list_protections` |
| **Pre-commit hook** | Blocks high-risk commits before they leave the developer's machine |
| **CI gate** | GitHub Action that posts an AI Safety Score on every PR and fails on high-risk diffs |

## Quick start

```bash
npx repo-seatbelt init          # interactive setup
npx repo-seatbelt scan          # AI Safety Score + risk report
npx repo-seatbelt mcp           # start the MCP guardrail server
npx repo-seatbelt install-hooks # add pre-commit protection
npx repo-seatbelt ci            # add GitHub Action gate
```

## Supported tools

Claude Code · Cursor · Codex / ChatGPT · Gemini CLI · Windsurf · Aider · Cline · Zed AI

## Links

- Repository: https://github.com/berkcangumusisik/repo-seatbelt
- npm: https://www.npmjs.com/package/repo-seatbelt
