# Agentic Company Researcher

A production-ready, multi-agent research platform built on **LangGraph** and **Tavily** that generates comprehensive company research reports on demand.

## What it does

Given a company name, URL, headquarters, and industry, the agent orchestrates a full research pipeline:

1. **Grounding** — Anchors context for the company before dispatching agents
2. **Parallel Research** (four simultaneous specialists):
   - **CompanyAnalyzer** — Core products, leadership team, business model, target market
   - **IndustryAnalyzer** — Market size, growth, direct competitors, positioning
   - **FinancialAnalyst** — Funding rounds, investors, revenue model, key metrics
   - **NewsScanner** — Announcements, partnerships, press coverage, awards
3. **Collector & Curator** — Aggregates, scores (Tavily relevance ≥ 0.4), and deduplicates research documents
4. **Enricher** — Supplements curated data with additional context
5. **Briefing** (Gemini 2.5 Flash) — Generates structured category briefings from high-context synthesis
6. **Editor** (GPT-5.1) — Compiles all briefings into a polished, deduplicated markdown report with MLA references

## Output format

Reports follow a fixed schema:
- **Company Overview** — Business model, leadership, products, differentiators
- **Industry Overview** — Market position, competitors, challenges
- **Financial Overview** — Funding history, investors, revenue model
- **News** — Chronological events: announcements, partnerships, recognition
- **References** — MLA-formatted citations

## Key features

- Dual-model architecture: Gemini 2.5 Flash for large-context synthesis + GPT-5.1 for precise formatting
- Asynchronous processing via FastAPI with polling-based progress tracking
- React frontend with real-time progress display and PDF export
- Deployable via Docker or the included setup script
- Live demo: https://companyresearcher.tavily.com

## Example usage

```bash
# Start the backend
python application.py

# POST a research request
curl -X POST http://localhost:8000/research \
  -H "Content-Type: application/json" \
  -d '{"company": "Stripe", "url": "https://stripe.com", "hq_location": "San Francisco, CA", "industry": "FinTech"}'
```

## Setup

Requires: `TAVILY_API_KEY`, `GEMINI_API_KEY`, `OPENAI_API_KEY`

```bash
git clone https://github.com/guy-hartstein/company-research-agent.git
cd company-research-agent
./setup.sh   # auto-detects uv or pip
```
