# Career-Ops

**AI-powered job search pipeline built on Claude Code.**

Career-ops was built and battle-tested during a real job search that evaluated
740+ offers, generated 100+ tailored CVs, and resulted in a Head of Applied AI
hire. It is designed to help you find roles with genuine fit — not to flood
inboxes with mass applications.

## Key Capabilities

- **Offer Evaluation** — structured A–G scoring across role fit, compensation,
  growth, culture, risk, and legitimacy
- **CV Generation** — ATS-optimised HTML→PDF and LaTeX/Overleaf output,
  tailored per application
- **Portal Scanner** — zero-LLM-cost scan of 45+ Greenhouse/Ashby/Lever APIs
  to surface new openings
- **Batch Processing** — parallel lightweight scoring of many offers at once
- **Application Pipeline** — from inbox URL to scored report to PDF in one pass
- **Interview Prep** — company-specific intel reports + STAR+R story bank
- **LinkedIn Outreach** — find the right contacts, draft warm messages
- **Application Tracker** — status overview across all active opportunities
- **Follow-up Cadence** — surface stale applications, suggest next steps
- **Rejection Patterns** — analyse what's not working and sharpen targeting
- **Live Apply Assist** — fill application forms (always stops before Submit)

## 14 Skill Modes

`oferta` · `ofertas` · `pipeline` · `pdf` · `latex` · `scan` · `batch` ·
`contacto` · `deep` · `interview-prep` · `training` · `project` · `tracker` ·
`apply` · `patterns` · `followup`

## Multi-Language Support

Runs in English (default), German/DACH, French/Francophone, and Japanese —
with market-specific vocabulary for each region.

## Human-in-the-Loop

Career-ops **never submits an application without explicit user approval.**
The agent evaluates, drafts, and prepares — the human always makes the final
call.

## Example Usage

```
# Evaluate a job posting
/career-ops <job-url>

# Scan portals for new openings
/career-ops scan

# Generate a tailored CV
/career-ops pdf

# See all commands
/career-ops
```

## Links

- Repository: https://github.com/santifer/career-ops
- Author: https://santifer.io
