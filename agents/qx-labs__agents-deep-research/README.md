# agents-deep-research

A powerful **multi-agent deep research assistant** built on the [OpenAI Agents SDK](https://github.com/openai/openai-agents-python) by [QX Labs](https://www.qxlabs.com). Given any research query, it iteratively hunts down knowledge gaps, dispatches specialised sub-agents to fill them, and synthesises everything into a comprehensive, fully-cited Markdown report.

## Key Capabilities

- **Two research modes:**
  - `IterativeResearcher` — fast, focused queries → reports up to ~1,000 words / 5 pages
  - `DeepResearcher` — long-form structured reports (20+ pages) via parallel section research
- **Multi-agent pipeline:** KnowledgeGapAgent → ToolSelectorAgent → (WebSearchAgent | WebsiteCrawlerAgent) → WriterAgent → ProofreaderAgent
- **Provider-agnostic:** runs on OpenAI, Anthropic, Gemini, DeepSeek, Perplexity, OpenRouter, Azure OpenAI, Hugging Face, Ollama, and LM Studio
- **Automated:** no clarifying questions — usable end-to-end in pipelines
- **Always cited:** every claim in the final report carries a numbered URL reference

## Example Usage

```python
import asyncio
from deep_researcher import IterativeResearcher, DeepResearcher

# Simple research
researcher = IterativeResearcher(max_iterations=5, max_time_minutes=5)
report = asyncio.run(researcher.run("Overview of quantum computing", output_length="5 pages"))

# Deep structured report
researcher = DeepResearcher(max_iterations=3, max_time_minutes=10)
report = asyncio.run(researcher.run("Comprehensive analysis of Tesla's market position"))

print(report)
```

```bash
# CLI
pip install deep-researcher
deep-researcher --mode deep --query "Life and works of Plato" --max-iterations 3 --max-time 10 --verbose
```

## Installation

```bash
pip install deep-researcher
```

See the [repository](https://github.com/qx-labs/agents-deep-research) for full setup instructions including API key configuration and custom tool extension.

## Sample Outputs

- [Life and Works of Plato](https://github.com/qx-labs/agents-deep-research/blob/main/examples/sample_output/plato.md) — 7,980 words
- [Text Book on Quantum Computing](https://github.com/qx-labs/agents-deep-research/blob/main/examples/sample_output/quantum_computing.md) — 5,253 words
- [Deep-Dive on Tesla](https://github.com/qx-labs/agents-deep-research/blob/main/examples/sample_output/tesla.md) — 4,732 words
