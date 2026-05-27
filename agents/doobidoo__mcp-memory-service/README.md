# mcp-memory-service

**Persistent shared memory for AI agent pipelines.**

`mcp-memory-service` is an open-source, self-hosted memory backend that gives
every AI agent a reliable, semantic, shared memory that survives across runs,
across frameworks, and across infrastructure — with zero cloud lock-in.

## What It Does

| Without mcp-memory-service | With mcp-memory-service |
|---|---|
| Each agent run starts from zero | Agents retrieve prior decisions in < 5 ms |
| Memory is local to one graph/run | Memory is shared across all agents and runs |
| You manage Redis + Pinecone + glue code | One self-hosted service, zero cloud cost |
| No causal relationships between facts | Knowledge graph with typed edges |
| Context window limits create amnesia | Autonomous consolidation compresses old memories |

## Key Capabilities

- **Framework-agnostic REST API** — 76 endpoints; works with LangGraph, CrewAI, AutoGen, and any HTTP client
- **MCP transport** — native Claude Desktop and OpenCode integration via Model Context Protocol
- **Remote MCP** — HTTPS-first; works in claude.ai browser without Claude Desktop
- **Causal knowledge graph** — typed edges (`causes`, `fixes`, `contradicts`) let agents reason over relationships
- **Semantic retrieval** — sub-5 ms vector search via local ONNX embeddings; memory never leaves your infra
- **Autonomous memory consolidation** — compresses and deduplicates aging memories automatically
- **Quality scoring** — every memory is scored for relevance, recency, and completeness
- **Cross-agent sharing** — `X-Agent-ID` header scopes memories by agent identity
- **OAuth 2.1 + team collaboration** — enterprise-ready auth built in
- **Web dashboard** — semantic search, tag browser, document ingestion, and analytics

## Quick Start

```bash
pip install mcp-memory-service
MCP_ALLOW_ANONYMOUS_ACCESS=true memory server --http
# REST API running at http://localhost:8000
```

```python
import httpx

BASE_URL = "http://localhost:8000"

# Store a memory
httpx.post(f"{BASE_URL}/memory", json={
    "content": "The user prefers concise answers with code examples.",
    "tags": ["preference", "style"],
    "metadata": {"agent_id": "my-agent"}
})

# Retrieve semantically
results = httpx.post(f"{BASE_URL}/memory/retrieve", json={
    "query": "user preferences",
    "n_results": 5
}).json()
```

## Frameworks Supported

LangGraph · CrewAI · AutoGen · Claude Desktop · OpenCode · Cursor · any HTTP client

## Links

- **Repository:** https://github.com/doobidoo/mcp-memory-service
- **Documentation:** https://doobidoo.github.io/mcp-memory-service/
- **Dashboard walkthrough:** https://youtu.be/W34r8VFoSdQ
- **PyPI:** https://pypi.org/project/mcp-memory-service/
