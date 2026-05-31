# SkillForge

**SkillForge** is an open-source web application that generates production-grade
AI Agent Skill packages through a structured 7-step pipeline, strictly aligned
with the Anthropic Agent Skills specification.

## What It Does

Give SkillForge a skill name and description and it will:

1. **Analyse requirements** — identifies functional boundaries, usage scenarios,
   and — most critically — the *knowledge gap* (what the model doesn't already
   know and therefore needs in the SKILL.md).
2. **Decide architecture** — selects the right structure pattern, freedom level,
   and plans all supporting resource files.
3. **Craft metadata** — generates and scores three candidate `description` values;
   picks the one with the best trigger precision and information density.
4. **Generate SKILL.md body** — 150–450 lines with overview, workflow, rules,
   ❌/✅ anti-pattern examples, edge cases, and a validation checklist.
5. **Quality audit** — scores the draft on 10 dimensions (1–10 each); fixes
   anything below 8.
6. **Generate resource files** — produces all `scripts/`, `references/`, and
   `templates/` files planned in Step 2. No `...` or `TODO` placeholders.
7. **Write usage docs** — installation steps, ≥5 natural-language trigger
   examples, iteration suggestions, and a final checklist.

It also **repairs existing Skills** via a 3-step diagnose → rewrite → audit flow.

## Key Features

- Real-time streaming output for every pipeline step
- `%%SKILL_BEGIN%%` / `%%SKILL_END%%` marker extraction — no truncation
- ZIP download of the complete skill package (SKILL.md + supporting files)
- Cancel running tasks, retry failed steps, delete history
- Supports Claude CLI, Anthropic API, and any OpenAI-compatible backend
- Full-stack TypeScript: React 19 + Tailwind CSS 4 + Express + tRPC + MySQL

## Example Usage

> "Generate a skill for scraping product prices from e-commerce pages."

> "Fix my existing git-rebase skill — it keeps getting triggered for the wrong tasks."

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | React 19, Tailwind CSS 4, shadcn/ui |
| Backend | Express 4, tRPC 11 |
| Database | MySQL / TiDB (Drizzle ORM) |
| LLM | Claude CLI / Anthropic API / OpenAI-compatible |

## Repository

https://github.com/mmlong818/skillforge
