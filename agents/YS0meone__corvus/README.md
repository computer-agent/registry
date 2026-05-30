# Corvus — Multi-Agent AI Research System

Corvus is a production-quality **multi-agent research assistant** built on LangGraph. It helps you discover academic papers and get evidence-based answers grounded in their full text.

## What it does

**1. Paper Finding**
- Searches Semantic Scholar (200M+ papers) using keyword queries with filters (year, venue, citation count)
- Runs web searches via Tavily to discover seminal work and broader context
- Performs forward and backward citation snowballing to surface related papers
- Auto-reruns searches with a refined plan if the initial results are insufficient

**2. Evidence-Based Q&A**
- Lets you select papers from the search results to focus on
- Retrieves relevant evidence chunks from indexed full text (stored in Qdrant)
- Synthesises grounded answers citing only the papers you chose
- Clearly flags papers whose full text could not be indexed

## Architecture

```
User → Supervisor (LangGraph)
         ├─ Paper Finding Agent
         │    ├─ Planner
         │    ├─ ReAct search executor (s2_search, tavily, forward/backward snowball)
         │    └─ Replanner
         └─ Q&A Agent
              ├─ Evidence retrieval (Qdrant vector search)
              ├─ Sufficiency evaluator
              └─ Answer synthesiser
```

- **Orchestration:** LangGraph supervisor + subgraph pattern
- **LLM:** Google Gemini 2.0 Flash via LangChain
- **Vector store:** Qdrant (scoped per selected papers)
- **Ingestion:** Celery + Redis background worker — arXiv PDF → Grobid → chunked embeddings
- **API:** FastAPI + LangGraph SDK streaming
- **Frontend:** React 19 + Vite
- **MCP server:** expose search tools directly in Claude Desktop

## Key capabilities

| Tool | Description |
|------|-------------|
| `s2_search_papers` | Semantic Scholar keyword search with filters |
| `tavily_research_overview` | Web search for context and author profiles |
| `forward_snowball` | Papers that cite a given seed paper |
| `backward_snowball` | Papers cited by a given seed paper |
| `retrieve_and_answer_question` | Evidence RAG over selected papers |

## Live demo

[corvus-agent.vercel.app](https://corvus-agent.vercel.app)

## Quick start

```bash
git clone https://github.com/YS0meone/Corvus.git && cd Corvus
cp backend/.env_example backend/.env.local
# fill in OPENAI_API_KEY, GEMINI_API_KEY, COHERE_API_KEY, S2_API_KEY
make infra        # starts Redis, Qdrant, Grobid via Docker Compose
make worker       # Celery PDF ingestion worker
make dev          # LangGraph backend  (http://localhost:2024)
make frontend     # React frontend     (http://localhost:5173)
```

## License

MIT — Copyright (c) 2025 Tim Yuan
