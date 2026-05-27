# AI Agent System — rjmurillo/ai-agents

A production-grade, coordinated multi-agent system for software development teams
that want AI velocity **with** real governance.

## What it does

Ships **23+ specialized AI agents** for Claude Code (and 24 for GitHub Copilot CLI)
that cover every phase of the software development lifecycle:

| Role | Agent | Responsibility |
|------|-------|----------------|
| Coordination | `orchestrator` | Central hub; delegates to specialists, keeps context clean |
| Discovery | `analyst` | Research, spikes, requirements, and feasibility |
| Design | `architect` | System design, ADR authoring, tech-debt triage |
| Build | `implementer` | Code generation guided by specs and ADRs |
| Quality | `qa` | Testing strategy, Pester/pytest authoring, coverage |
| Safety | `security` | Vulnerability detection, CWE/OWASP scanning |
| Operations | `devops` | CI/CD pipelines, deployment, and observability |
| Adversarial | `critic` | Pokes holes in other agents' outputs |
| Governance | `session-init` / `session-end` | Session gates, memory persistence, handoffs |
| Improvement | `reflect` | Weekly retrospectives and self-improvement tracking |

## Key capabilities

- **ADR-steered governance** — architecture decisions live in `.agents/architecture/ADR-*.md`; agents never break them without a new ADR proposal
- **Explicit handoff protocols** — each agent passes a structured HANDOFF.md to the next, keeping the orchestrator context lean
- **Cross-session memory** — via Serena MCP + Forgetful; citation-verified graph traversal with health reporting
- **Review gates** — five validation checkpoints before a PR lands (spec, pre-PR script, security scan, QA, and ADR compliance)
- **Skill-first routing** — any task that matches an installed skill invokes that skill's tested workflow first

## Installation

**Claude Code:**
```
/install-plugin rjmurillo/ai-agents
```

**GitHub Copilot CLI:**
```
/plugin marketplace add rjmurillo/ai-agents
/plugin install project-toolkit@ai-agents
```

## Example usage

```
# Claude Code — run the orchestrator on a new feature
Task(subagent_type="orchestrator", prompt="Build a rate-limiting middleware for our FastAPI service per ADR-017")

# Trigger a security scan
Task(subagent_type="security", prompt="Scan PR #234 for CWE-89 and OWASP A03")

# Weekly retro
Task(subagent_type="reflect", prompt="Run the weekly retrospective")
```

## License

MIT — [github.com/rjmurillo/ai-agents](https://github.com/rjmurillo/ai-agents)
