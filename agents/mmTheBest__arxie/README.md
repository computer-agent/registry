# Arxie

Arxie is a self-hostable AI research assistant that turns a curated folder of academic
papers into a field-aware working context. It combines a canonical paper database
(Paperbase), structured evidence extraction, and hybrid retrieval to help researchers
accelerate literature review, hypothesis generation, and experiment design.

## What It Does

- **Ingest**: Import papers from local PDFs, DOI, arXiv IDs, and OpenAlex identifiers
- **Parse & Extract**: Break papers into sections/chunks and extract structured evidence — datasets, methods, metrics, findings, limitations, figures, tables, engineering tricks, and research-design elements
- **Search**: Hybrid retrieval (semantic + keyword) over your paper corpus with Elasticsearch backend
- **Research Artifacts**: Generate experiment plans, benchmark designs, hypotheses, assumption maps, literature reviews, revision priorities, field patterns, and critiques — all grounded in cited evidence
- **Study Workspace**: Save a study (collection + query + focus + pinned papers + explicit sources) and hold a research conversation with citation-backed answers
- **Citation Chasing**: Forward citation traversal via Semantic Scholar to find follow-up and validation work

## Key Capabilities

| Capability | Description |
|---|---|
| `search_papers` | Search Semantic Scholar and arXiv |
| `get_paper_details` | Full metadata for a specific paper |
| `read_paper_fulltext` | Read methods, results, conclusions from a paper |
| `get_paper_structured_data` | Extracted datasets, metrics, figures from Paperbase |
| `get_paper_citations` | Forward citation chasing |
| Literature Review | Collection-grounded review with evidence payloads |
| Hypothesis Generation | Field-grounded hypotheses from corpus patterns |

## Example Usage

```bash
ra query "What are the dominant approaches to long-context transformers?"
ra lit-review "attention mechanisms in computer vision"
ra trace "Attention Is All You Need"
ra chat
```

Or use the browser study app at `http://localhost:8080/app`.

## Tech Stack

- **LangChain** agent loop with `create_agent`
- **OpenAI** models (default: `gpt-4o-mini`, eval: `gpt-4o`)
- **Elasticsearch** for hybrid search
- **PostgreSQL** + **Redis** + **MinIO** for the Paperbase backend
- **FastAPI** REST API + browser UI
- Self-hosted, single-user, MIT licensed
