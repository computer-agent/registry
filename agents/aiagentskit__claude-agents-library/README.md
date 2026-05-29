# Claude Agents Library

**34 production-ready Claude agent configurations** organised across 7 professional
categories — ready to drop into Claude Code's `.claude/agents/` directory or paste
as a system prompt in any Claude-compatible runtime.

## What It Does

The Claude Agents Library gives you a curated roster of specialist AI personas.
Each agent is a deeply-configured Markdown file that transforms Claude into a
domain expert with a defined purpose, core responsibilities, key skills,
communication style, and example prompts.

Instead of writing system prompts from scratch, you grab the right agent,
copy it in, and get consistent, expert-level output every time.

## Categories & Agents

| Category | Count | Agents |
|---|---|---|
| **Engineering** | 6 | AI Engineer, Backend Architect, DevOps Automator, Frontend Developer, Mobile App Builder, Rapid Prototyper |
| **Marketing** | 7 | TikTok Strategist, Instagram Curator, X/Twitter Strategist, Reddit Community Builder, App Store Optimizer, Content Creator, Growth Hacker |
| **Design** | 5 | Brand Guardian, UI Designer, UX Researcher, Visual Storyteller, Whimsy Injector |
| **Product** | 3 | Trend Researcher, Feedback Synthesizer, Sprint Prioritizer |
| **Project Management** | 3 | Experiment Tracker, Project Shipper, Studio Producer |
| **Studio Operations** | 5 | Support Responder, Analytics Reporter, Infrastructure Maintainer, Legal Compliance Checker, Finance Tracker |
| **Testing** | 5 | Tool Evaluator, API Tester, Workflow Optimizer, Performance Benchmarker, Test Results Analyzer |

## Key Features

- **v1.2 — 34 agents** across 7 professional domains
- **Copy-paste ready** — each agent ships with purpose, responsibilities, skills, and example prompts
- **Claude Code compatible** — drop agents into `.claude/agents/` for automatic discovery
- **MCP integration patterns** — 7 ready-made workflows with code examples
- **Model selection matrix** — 30+ task-specific recommendations with cost comparisons
- **Cost optimisation guide** — up to 82% API cost savings with Haiku/Sonnet/Opus routing

## Quick Start

```bash
# Project-specific install
mkdir -p .claude/agents
cp -r engineering product marketing .claude/agents/

# Global install (available in all projects)
mkdir -p ~/.claude/agents
cp -r engineering product marketing ~/.claude/agents/
```

## Example Usage

Reference an agent in Claude Code or paste it as a system prompt:

```
Acting as the AI Engineer agent, design a RAG pipeline for legal document search.
```

## Repository

https://github.com/aiagentskit/claude-agents-library
