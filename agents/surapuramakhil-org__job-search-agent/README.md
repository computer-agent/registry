# Job Search Agent

An autonomous, AI-powered job search and application agent built with Python, LangChain, and Selenium. It scans job portals (LinkedIn, Lever, and others), evaluates each listing against your resume and work preferences, writes tailored cover letters, generates role-specific resumes, fills application forms automatically, and tracks every submission — all without manual intervention.

---

## Run

```bash
npx @open-gitagent/gitagent run -r https://github.com/surapuramakhil-org/Job_search_agent
```

---

## What It Can Do

- **Intelligent Job Search** — Queries job portals using your criteria (title, location, date range, salary). Filters out blacklisted companies and irrelevant titles before spending any LLM tokens.
- **Resume Screening** — Scores each listing 1–10 against your resume and preferences. Only applies to listings above your configured threshold.
- **Tailored Cover Letter Generation** — Writes concise, company-specific cover letters (≤3 paragraphs) drawing from the job description and your profile. No generic templates.
- **Application Form Auto-fill** — Answers text, numeric, dropdown and checkbox questions using the most relevant resume section (education, experience, certifications, legal authorisation, etc.).
- **Dynamic Resume Generation** — Generates a customised resume version per application, foregrounding the qualifications most relevant to that role.
- **Application Tracking** — Logs every attempt with company, role, portal, timestamp, model used, token counts, and final status.

---

## Supported Models

| Provider | Models |
|----------|--------|
| OpenAI | GPT-4o (default), GPT-4o-mini |
| Anthropic | Claude Sonnet, Claude Haiku |
| Google | Gemini 2.0 Flash |
| Groq | Llama 3, Mixtral |
| Ollama | Any locally-served model |
| Perplexity | Via API |

Models are configured in `secrets.yaml`. Routes through a TensorZero gateway for unified observability.

---

## Configuration

```yaml
# work_preferences.yaml (example)
remote: true
relocation: false
country: USA
salary_minimum: 100000
blacklisted_companies: [Amazon, Meta]
blacklisted_titles: [intern, junior]
```

```yaml
# secrets.yaml (example)
llm_model_type: openai
llm_api_key: sk-...
llm_model: gpt-4o
```

---

## Topics

`agent` · `ai` · `ai-agents` · `automation` · `bot` · `gpt` · `job` · `job-search` · `langchain` · `llm` · `python` · `selenium` · `tailored-application`

---

## Built with

[GitAgent Protocol](https://gitagent.sh) — an open, vendor-neutral standard for portable AI agents.
