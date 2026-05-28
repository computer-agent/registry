# Second Brain Agent 🧠

A **Personal Knowledge Management AI agent** that turns your scattered markdown notes into a searchable, conversational knowledge base — inspired by Tiago Forte's *Building a Second Brain* methodology.

## What It Does

Second Brain Agent watches your markdown note directory and automatically ingests everything it finds:

- 📝 **Markdown files** — extracted text and metadata
- 📄 **PDFs** — local and remote (including arXiv papers)
- 🎥 **YouTube videos** — auto-transcribed and indexed
- 🌐 **Web pages** — fetched and chunked for semantic search
- 🔗 **File URLs** — any linked local document

All content is broken into chunks, embedded with HuggingFace sentence-transformers, and stored in a local **ChromaDB** vector database — entirely on your machine.

## Key Capabilities

| Capability | Detail |
|---|---|
| **Semantic Search** | Ask questions in natural language; the agent finds the most relevant chunks across all your notes |
| **Domain Filtering** | Automatically classifies notes by domain (Work, Personal, Workout, etc.) from filename conventions |
| **Journal Awareness** | Handles date-structured journal entries for temporal queries (`## 02 Dec 2024`) |
| **MCP Server** | Exposes the vector DB via Model Context Protocol — plug any MCP-compatible LLM into your notes |
| **Smart Connections** | Surfaces non-obvious relationships between notes |

## Example Usage

```bash
# Index your Obsidian vault
SRCDIR=~/Documents/MyNotes DSTDIR=~/sba-data uv run python transform_md.py

# Start the MCP server (then connect your LLM client)
uv run python mcp_server.py

# Query via CLI
uv run python qa.py "What did I learn about systems thinking last month?"
```

## Setup

```bash
# Clone and install
git clone https://github.com/flepied/second-brain-agent.git
cd second-brain-agent
cp example.env .env   # fill in your API keys
uv install
```

**Required env vars:** `OPENAI_API_KEY`, `HUGGINGFACEHUB_API_TOKEN`, `SRCDIR`, `DSTDIR`  
**Optional:** `ASSEMBLYAI_API_KEY` for higher-quality transcription

## Stack

- **LangChain** — orchestration
- **ChromaDB** — local vector store
- **FastMCP** — MCP server
- **HuggingFace sentence-transformers** — embeddings
- **OpenAI** — answer generation (GPT-4o by default)

## Protocol

This agent conforms to the [GitAgent Protocol](https://gitagent.sh) — see [`agent.yaml`](https://github.com/flepied/second-brain-agent/blob/main/agent.yaml) and [`SOUL.md`](https://github.com/flepied/second-brain-agent/blob/main/SOUL.md).
