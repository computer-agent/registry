# claude-agents

**Author:** [iannuttall](https://github.com/iannuttall) · **Stars:** 2000+ · **License:** MIT

A curated collection of **seven specialized Claude Code sub-agents** that cover the
full software-development lifecycle. Install them project-wide or globally; Claude
Code auto-discovers and activates the right specialist for every task.

## Sub-agents

| Agent | Role |
|---|---|
| `code-refactorer` | Improve code structure, readability, and maintainability without changing behaviour. Decomposes long functions, eliminates duplication, and applies design patterns. |
| `security-auditor` | Enterprise-grade security audits (OWASP-aligned) across auth, input validation, data protection, APIs, and dependencies. Produces a `security-report.md` with a remediation checklist. |
| `frontend-designer` | Convert mockups, wireframes, and screenshots into pixel-perfect component architectures and design-system specs. |
| `prd-writer` | Draft comprehensive Product Requirements Documents with goals, personas, functional requirements, UX flows, success metrics, and user stories. |
| `project-task-planner` | Transform a PRD into a structured, prioritised development task list (setup → frontend → backend → testing → deploy). |
| `content-writer` | Create engaging Flesch-Kincaid 8th-grade blog posts, articles, and docs. Operates in *outline* and *write* modes. |
| `vibe-coding-coach` | Translate visual references and vague "vibes" into working applications, abstracting technical complexity for non-technical builders. |

## Installation

**Project-specific:**
```bash
mkdir -p .claude/agents
cp agents/*.md .claude/agents/
```

**Global (all projects):**
```bash
mkdir -p ~/.claude/agents
cp agents/*.md ~/.claude/agents/
```

## Usage

Once installed, Claude Code automatically delegates to the correct sub-agent based
on context. No extra configuration needed — each agent's `description` field tells
Claude Code exactly when to activate it.

## Example prompts

- *"I just finished the auth system, can you clean it up?"* → `code-refactorer`
- *"Audit our API for security vulnerabilities"* → `security-auditor`
- *"Write a PRD for a pet-photo sharing app"* → `prd-writer`
- *"Turn this PRD into a sprint task list"* → `project-task-planner`
- *"Build me an app that feels like Notion but for recipes"* → `vibe-coding-coach`

## Links

- [Repository](https://github.com/iannuttall/claude-agents)
- [GitAgent Protocol](https://gitagent.sh)
- [Open GAP Registry](https://registry.gitagent.sh)
