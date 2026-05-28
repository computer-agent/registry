# claude-code-agents

A complete end-to-end development workflow for solo developers building with **Next.js / React / TypeScript** using Claude Code. Built by [Paul @ UndeadList](https://undeadlist.com) from real-world production experience.

## What It Does

Gives a solo dev a full virtual engineering team, orchestrated through Claude Code's `Task()` API:

- **24 specialized subagents** — each with a non-overlapping domain, designed to run in parallel
- **6 reusable workflow skills** — installable as slash commands (`/full-audit`, `/pre-commit`, `/pre-deploy`, `/new-feature`, `/bug-fix`, `/release-prep`)
- **Strict human-approval protocols** — AI agents cannot make changes without explicit checkpoint approval

## Agent Categories

| Category | Count | Purpose |
|---|---|---|
| Audit agents | 11 | Code, security, db, perf, SEO, deps, infra, UI, docs, bugs, APIs — run in parallel |
| Fix/implement agents | 4 | fix-planner, code-fixer, test-runner, test-writer |
| Browser QA agents | 4 | Chrome integration, UI testing, console monitoring, visual diff |
| Deploy agents | 2 | Pre-deploy validation, env config |
| Utility agents | 2 | PR writer, seed/test-data generator |
| Supervisor | 1 | architect-reviewer — final gate, oversees full pipeline |

## Key Workflows

```bash
# Full parallel audit — all 11 auditors simultaneously
claude "Run full-audit workflow on src/"

# Pre-commit check
claude "Run pre-commit workflow"

# TDD new feature
claude "Run new-feature workflow for: user authentication"

# Pre-deployment validation
claude "Run pre-deploy workflow"
```

## Install as Plugin

```bash
# Inside Claude Code
/plugin marketplace add undeadlist/claude-code-agents
/plugin install claude-code-agents@undeadlist-claude-code-agents
```

## Design Philosophy

> *"You don't have a QA team. You don't have a code reviewer. You don't have time to waste on AI going rogue. This workflow is all of that — in a box, with guardrails."*

All agents follow strict protocols: one change at a time, explicit scope, human checkpoint before destructive actions, regression testing after every fix. Audit reports write to `.claude/audits/` (gitignored).

## Stack

Optimized for Next.js / React / TypeScript / Prisma / Vercel. Stack-agnostic agents (security, code quality, docs, PR writer) work on any project.

## Links

- Repository: https://github.com/undeadlist/claude-code-agents
- Author: https://undeadlist.com
