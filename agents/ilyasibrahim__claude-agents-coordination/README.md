# Claude Agents Coordination

A **production-grade multi-agent coordination system** for Claude Code that solves three
critical problems in long-running agent workflows:

1. **Context amnesia** — agents forget prior work within 15–20 minutes
2. **Coordination chaos** — multiple agents overwriting each other's output
3. **Delegation limits** — manual oversight required for every routing decision

## Architecture

### Tiered Agent System

| Tier | Agents | Role |
|------|--------|------|
| 1 — Orchestrators | code-quality, test-engineer, architect, ml-engineer | End-to-end workflow ownership |
| 2 — Specialists | security-engineer, sre, rfc, data-engineer, frontend, backend, devops, docs | Focused execution |
| 3 — On-demand | lrl-nlp-expert, data-viz-specialist, ux-designer | Deep domain expertise |

### Dual-Registry Model

- **`_registry.md`** — Institutional memory: what was done, what was delivered, what is next.
- **`_tech-debt.md`** — Explicit debt ledger: every shortcut logged with severity, source, and remediation plan.

### 4-Step Coordination Protocol

1. **Registry Check** — restore context before any task
2. **Context Injection** — distribute relevant history to sub-agents
3. **Sequencing** — parallel or sequential execution per dependency order
4. **Verification** — quality gates (lint, type-check, test, OWASP) before marking done

## Key Commands

| Command | What it does |
|---------|-------------|
| `/review-full <path>` | Multi-level code review (L1 peer → L4 reliability) |
| `/ci` | Full local quality gate before pushing |
| `/debt` | View and manage tech-debt registry |
| `/rfc <topic>` | Create and manage RFC design documents |
| `/postmortem <incident>` | Structured incident review with auto debt logging |

## Quick Start

```bash
# Install user-level config (agents, commands, skills)
mkdir -p ~/.claude && rsync -a claude-user/ ~/.claude/

# Install project-level config (memory, registries, project commands)
mkdir -p .claude && rsync -a claude-project/ .claude/
```

Then open Claude Code and run `/review-full src/` or `/ci` to see the system in action.

## Performance

| Metric | Before | After |
|--------|--------|-------|
| Productive session length | ~15–20 min | 2+ hours |
| Protocol token overhead | 370 lines (always) | 150–250 lines (selective) |
| Review depth | Single-level | L1 → L4 graduated escalation |
| Tech-debt visibility | None | Explicit ledger |

## Resources

- **Repo**: https://github.com/ilyasibrahim/claude-agents-coordination
- **Article series**: https://medium.com/@ilyas.ibrahim
- **License**: Unlicense (public domain)
