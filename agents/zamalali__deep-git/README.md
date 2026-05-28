# DeepGit

**DeepGit** is an advanced, LangGraph-based agentic research workflow designed to perform deep discovery across GitHub repositories. It intelligently searches, analyses, and ranks repos based on your natural-language query — surfacing powerful but less-known tools that a standard GitHub search would miss.

## What It Does

Given a query like *"I need a lightweight chain-of-thought reasoning library that runs on CPU"*, DeepGit:

1. **Expands your query** into precise GitHub search tags via an LLM.
2. **Detects hardware constraints** from your wording (e.g., "GPU-poor", "low RAM") and enforces them throughout.
3. **Retrieves at scale** using the GitHub API and hybrid dense retrieval (ColBERT v2 token embeddings + BM25 + FAISS).
4. **Re-ranks** with a cross-encoder (MiniLM-L-6-v2) for passage-level accuracy.
5. **Filters by dependency compatibility** — inspects `requirements.txt` / `pyproject.toml` to discard repos your hardware can't run.
6. **Analyses community health** — stars, forks, issue cadence, recent commits, contributor count.
7. **Scores code quality** — structural signals indicating a well-organised, production-ready project.
8. **Delivers a ranked table** with links, similarity scores, hardware badges, and health indicators.

## Key Features

- 🔍 **Deep semantic search** — ColBERT v2 multi-dimensional token-level matching, not just cosine similarity
- ⚛️ **Cross-encoder re-ranking** — passage-level accuracy via `cross-encoder/ms-marco-MiniLM-L-6-v2`
- 🔩 **Hardware-aware filtering** — only recommends repos that actually run on your machine
- 📊 **Multi-factor ranking** — combines semantic similarity, community health, and code quality
- 🚀 **Gradio UI + LangGraph dev dashboard** supported
- 🐳 **Docker-ready** with a provided Dockerfile

## Example Usage

```bash
# Set your API keys
export GROQ_API_KEY=your_key_here
export GITHUB_API_KEY=your_github_token

# Run the agent
python app.py
```

Or launch the full LangGraph dev workflow:

```bash
langgraph dev
```

## Model

Uses **Groq** (`deepseek-r1-distill-llama-70b`) by default for query expansion and reasoning. MiniMax (`MiniMax-M2.7`, 204K context) is supported as an alternative.

## Links

- 🔗 [GitHub Repository](https://github.com/zamalali/DeepGit)
- 🤗 [HuggingFace Space (lite version)](https://huggingface.co/spaces/zamal/DeepGit)
