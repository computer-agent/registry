# claude-code-agents

**A complete E2E development workflow for solo-dev startups using Claude Code.**

Built by [Paul @ UndeadList](https://undeadlist.com), this plugin gives a solo developer a
full virtual engineering team — code reviewers, QA engineers, security auditors, and a
DevOps engineer — all orchestrated through Claude Code's `Task()` API with strict
human-approval protocols to keep AI in scope at every step.

## What It Does

Provides **24 specialized Claude Code subagents** and **6 workflow skills** that cover
the entire development lifecycle for Next.js / React / TypeScript projects (Prisma, npm/pnpm, Vercel).

### Audit Agents (11 — run in parallel)
| Agent | Scope |
|---|---|
| `code-auditor` | Code quality, DRY, complexity |
| `bug-auditor` | Runtime bugs (not security) |
| `security-auditor` | OWASP deep scan (single authority) |
| `doc-auditor` | Documentation gap analysis |
| `infra-auditor` | Config, env vars, HTTP headers |
| `ui-auditor` | Accessibility, UX issues |
| `db-auditor` | N+1 queries, indexes, ORM misuse |
| `perf-auditor` | Bundle size, render performance |
| `dep-auditor` | Dependency vulnerabilities |
| `seo-auditor` | Meta tags, OpenGraph, structured data |
| `api-tester` | Endpoint validation, response contracts |

### Fix / Implement Agents (4)
- **`fix-planner`** — prioritises audit findings into a `FIXES.md` action list
- **`code-fixer`** — implements approved fixes one at a time
- **`test-runner`** — validates fixes without regressions
- **`test-writer`** — auto-generates tests for new features (TDD)

### Browser QA Agents (4)
- **`browser-qa-agent`** — navigates UI via Chrome, finds console errors
- **`fullstack-qa-orchestrator`** — end-to-end find → fix → verify loop
- **`console-monitor`** — real-time console error watching
- **`visual-diff`** — before/after screenshot comparison

### Deploy Agents (2)
- **`deploy-checker`** — pre-deployment build and config validation
- **`env-validator`** — environment variable completeness

### Utility Agents (2)
- **`pr-writer`** — generates detailed PR descriptions
- **`seed-generator`** — creates realistic test data

### Supervisor (1)
- **`architect-reviewer`** — final gate; oversees audit → fix → re-audit loop

## Workflow Skills (Slash Commands)

| Skill | What It Does |
|---|---|
| `/full-audit` | All 11 auditors in parallel → fix-planner creates `FIXES.md` |
| `/pre-commit` | code-auditor + test-runner before committing |
| `/pre-deploy` | deploy-checker + env-validator + dep-auditor |
| `/new-feature` | test-writer → code-fixer → test-runner → browser-qa (TDD) |
| `/bug-fix` | Write failing test → fix → verify (regression prevention) |
| `/release-prep` | Full audit → fixes → deploy validation → pr-writer |

## Install

```bash
# Inside Claude Code — install as a plugin (all 24 agents + 6 skills):
/plugin marketplace add undeadlist/claude-code-agents
/plugin install claude-code-agents@undeadlist-claude-code-agents
```

Or from the terminal:
```bash
claude plugin install claude-code-agents@undeadlist-claude-code-agents --scope user
```

## Example Usage

```bash
# Full parallel audit
claude "Run full-audit workflow on src/"

# Pre-commit check
claude "Run pre-commit workflow"

# TDD new feature
claude "Run new-feature workflow for: user settings page"

# Fix a specific bug
claude "Run bug-fix workflow for: checkout form submits twice on double-click"

# Full release prep
claude "Run release-prep workflow for v1.2.0"
```

## Stack

Optimised for **Next.js / React / TypeScript** with Prisma, npm/pnpm, and Vercel.
Stack-agnostic agents (`security-auditor`, `code-auditor`, `doc-auditor`, `pr-writer`,
`fix-planner`, `architect-reviewer`) work on any project.

## License

MIT — use it, fork it, adapt it.
