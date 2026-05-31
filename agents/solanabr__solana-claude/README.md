# solana-claude

**Production-ready Claude Code configuration for full-stack Solana blockchain development.**

`solana-claude` turns any Claude (or compatible) LLM into an expert Solana builder with deep knowledge spanning on-chain programs, DeFi protocols, frontend dApps, mobile (Solana Mobile SDK), Unity games, security auditing, and DevOps. It ships a battle-tested configuration you drop into any Solana project with a single `curl` command.

---

## What it does

- **15 specialized sub-agents** — each loaded on-demand to keep context lean:
  `solana-architect`, `anchor-engineer`, `pinocchio-engineer`, `defi-engineer`,
  `solana-frontend-engineer`, `mobile-engineer`, `unity-engineer`,
  `rust-backend-engineer`, `devops-engineer`, `solana-qa-engineer`,
  `token-engineer`, `tech-docs-writer`, `solana-researcher`, `game-architect`,
  `solana-guide`

- **24 workflow commands** — `/quick-commit`, `/audit-solana`, `/profile-cu`,
  `/diff-review`, `/setup-mcp`, `/cleanup`, and more — covering build, deploy,
  test, profile, and commit workflows

- **6 MCP server integrations** — Helius (60+ RPC/DAS tools), Solana Foundation
  official docs, Context7 (library docs), Playwright (dApp e2e testing),
  context-mode (response compression), memsearch (persistent semantic memory)

- **Progressive skill loading** — 10 external submodules (Solana Foundation,
  SendAI, Trail of Bits, Vercel, Cloudflare, QEDGen, Colosseum, and more) loaded
  only when relevant, keeping the base context under 120 lines

- **Security-first** — enforced rules: checked arithmetic everywhere, full
  account validation, devnet-before-mainnet deploy gates, CU profiling,
  verifiable builds for mainnet

---

## Quick Start

```bash
# Option 1: One-liner (Claude Code)
curl -fsSL https://raw.githubusercontent.com/solanabr/solana-claude/main/install.sh | bash

# Option 2: Non-Claude runtimes (Cursor, Windsurf, Codex, etc.)
curl -fsSL https://raw.githubusercontent.com/solanabr/solana-claude/main/install.sh | bash -s -- --agents

# Option 3: Manual
git clone --recurse-submodules https://github.com/solanabr/solana-claude.git
cp -r solana-claude/.claude /path/to/your-project/
cp solana-claude/CLAUDE-solana.md /path/to/your-project/CLAUDE.md
```

Then start Claude Code (`claude`) and the full agent configuration is live.

---

## Example usage

```
# In Claude Code, once installed:
"I need to build a token staking program with crank-less rewards"
→ solana-architect designs the account layout
→ anchor-engineer implements the program
→ solana-qa-engineer writes BankClient tests
→ devops-engineer sets up the deploy pipeline

# Security audit
/audit-solana

# CU profiling before mainnet
/profile-cu

# Smart commit with branch naming convention
/quick-commit
```

---

## Links

- Repository: https://github.com/solanabr/solana-claude
- Install docs: see `QUICK-START.md` in the repo
- License: MIT
