# awesome-claude-agents

**An orchestrated team of 24+ specialised Claude Code sub-agents** that collaborate to build complete software features across any technology stack — no manual agent selection required.

## What it does

Drop the collection into `~/.claude/agents/` and invoke `@agent-tech-lead-orchestrator`. The tech lead analyses your project, detects the stack, and automatically routes every task to the right specialist. You describe what you want to build; the team figures out who does what and in what order.

## Key capabilities

- **Intelligent orchestration** — a tech-lead orchestrator routes tasks to the optimal specialist; never the wrong tool for the job
- **Framework depth** — dedicated experts for Django, Rails, Laravel, React, and Vue (not just generic "backend" or "frontend" agents)
- **Full lifecycle** — code archaeology, code review, performance optimisation, documentation, and API design all covered
- **Parallel execution** — the team runs up to 2 agents in parallel for speed while keeping context clean
- **Auto-configuration** — `@agent-team-configurator` scans your local agents and updates `CLAUDE.md` so the tech lead always knows what's available

## Team roster

| Category | Agents |
|---|---|
| Orchestrators | tech-lead-orchestrator, project-analyst, team-configurator |
| Core | code-reviewer, code-archaeologist, performance-optimizer, documentation-specialist |
| Django | django-backend-expert, django-api-developer, django-orm-expert |
| Rails | rails-backend-expert, rails-api-developer |
| Laravel | laravel-backend-expert, laravel-eloquent-expert |
| React | react-component-architect |
| Vue | vue-component-architect |
| Universal | backend-developer, frontend-developer, api-architect, tailwind-css-expert |

## Quick start

```bash
# Install globally
git clone https://github.com/vijaythecoder/awesome-claude-agents.git
mkdir -p ~/.claude/agents
ln -sf "$(pwd)/awesome-claude-agents/agents/" ~/.claude/agents/awesome-claude-agents

# Configure for your project
claude "use @agent-team-configurator and optimise my project to best use the available subagents."

# Start building
claude "use @agent-tech-lead-orchestrator and build a user authentication system"
```

## Token usage note

Multi-agent orchestration is intensive — expect 10–50 k tokens per complex feature. Monitor your usage accordingly.

## License

MIT — see [LICENSE](https://github.com/vijaythecoder/awesome-claude-agents/blob/main/LICENSE)
