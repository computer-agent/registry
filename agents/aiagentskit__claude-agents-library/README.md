# Claude Agents Library

**34 production-ready Claude agent configurations** organised across 7 professional
categories, ready to copy-paste as system prompts or drop into Claude Code's
`.claude/agents/` directory.

## What It Does

The Claude Agents Library gives you a curated roster of specialist AI personas —
each one a deeply-configured Markdown file that transforms Claude into a domain
expert with consistent behaviour, defined responsibilities, and example prompts.

Instead of starting from a blank system prompt every time, you grab the agent
that matches your task, paste it in, and get a senior specialist.

## Categories & Agents

| Category | Agents |
|---|---|
| **Design** (5) | Brand Guardian, UX Researcher, Visual Designer, Motion Designer, Design System Architect |
| **Engineering** (6) | AI Engineer, Backend Architect, DevOps Automator, Frontend Developer, Mobile App Builder, Rapid Prototyper |
| **Marketing** (7) | App Store Optimizer, Content Strategist, Growth Hacker, SEO Specialist, Social Media Manager, Email Marketer, Campaign Analyst |
| **Product** (3) | Feedback Synthesizer, Product Roadmapper, Competitive Analyst |
| **Project Management** (3) | Sprint Planner, Retrospective Facilitator, Risk Manager |
| **Studio Operations** (5) | Client Relations Manager, Resource Planner, Process Documenter, Billing Specialist, Onboarding Guide |
| **Testing** (5) | API Tester, QA Strategist, Performance Tester, Accessibility Auditor, Security Scanner |

## Key Features

- **v1.2 — 34 agents** across 7 professional categories
- **Copy-paste ready** — each agent ships with purpose, responsibilities, skills, communication style, and example prompts
- **Claude Code compatible** — drop agents into `.claude/agents/` for auto-discovery
- **MCP integration patterns** — 7 ready-made workflows with code examples
- **Model selection matrix** — 30+ task-specific recommendations with cost comparisons
- **Cost optimisation** — up to 82% savings with guidance on Haiku vs. Sonnet vs. Opus

## Quick Start

```bash
# Project-specific
mkdir -p .claude/agents
cp agents/engineering/ai-engineer.md .claude/agents/

# Global (available in all projects)
mkdir -p ~/.claude/agents
cp agents/*.md ~/.claude/agents/
```

## Example Usage

Paste an agent's Markdown content as your system prompt, then interact normally:

```
# You are the AI Engineer agent from the Claude Agents Library...
[paste agent content here]

User: Help me design a RAG pipeline for a legal document search system.
```

## Repository

https://github.com/aiagentskit/claude-agents-library
