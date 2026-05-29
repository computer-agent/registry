# TradingAgents

**TradingAgents** is an open-source, multi-agent LLM financial trading framework by [TauricResearch](https://github.com/TauricResearch) that replicates the collaborative dynamics of a real trading firm.

## What It Does

Given a ticker symbol and a date, TradingAgents orchestrates a pipeline of specialised agents that independently analyse the market and then debate their findings before the Portfolio Manager delivers a final, rated trading decision.

### Agent Pipeline

| Role | Responsibility |
|------|---------------|
| **Fundamentals Analyst** | Reads financial statements (balance sheet, cash-flow, income statement) to assess intrinsic value |
| **Sentiment Analyst** | Aggregates StockTwits, Reddit, and news sentiment to gauge crowd mood |
| **News Analyst** | Monitors global macro headlines and event-driven catalysts |
| **Technical Analyst** | Applies MACD, RSI, and pattern recognition to price data |
| **Bull Researcher** | Champions the upside case in a structured debate |
| **Bear Researcher** | Challenges bullish assumptions and surfaces risks |
| **Research Manager** | Synthesises the bull/bear debate into a 5-tier rated investment plan |
| **Trader** | Converts the research plan into a concrete BUY/HOLD/SELL transaction proposal |
| **Aggressive / Conservative / Neutral Debators** | Three-way risk debate evaluating volatility, liquidity, and position sizing |
| **Portfolio Manager** | Final decision-maker — synthesises everything into a rated, evidence-backed decision |

### Decision Scale

`Buy → Overweight → Hold → Underweight → Sell`

### Memory & Learning

Each completed run is logged to a persistent memory file (`~/.tradingagents/memory/trading_memory.md`). On subsequent runs for the same ticker, realised returns are fetched and the Portfolio Manager receives prior decisions plus lessons learned — enabling continuous improvement.

### Multi-Provider LLM Support

OpenAI (GPT), Anthropic (Claude), Google (Gemini), xAI (Grok), DeepSeek, Qwen, GLM, MiniMax, OpenRouter, Ollama (local), and Azure OpenAI.

## Quick Start

```bash
git clone https://github.com/TauricResearch/TradingAgents.git
cd TradingAgents
pip install .
tradingagents   # interactive CLI
```

Or via Python:

```python
from tradingagents.graph.trading_graph import TradingAgentsGraph
from tradingagents.default_config import DEFAULT_CONFIG

ta = TradingAgentsGraph(debug=True, config=DEFAULT_CONFIG.copy())
_, decision = ta.propagate("NVDA", "2026-01-15")
print(decision)
```

## Research Disclaimer

TradingAgents is designed for **research purposes only**. Trading performance varies with model choice, temperature, data quality, and market conditions. This is not financial, investment, or trading advice. See https://tauric.ai/disclaimer/

## Citation

```bibtex
@misc{xiao2025tradingagentsmultiagentsllmfinancial,
  title={TradingAgents: Multi-Agents LLM Financial Trading Framework},
  author={Yijia Xiao and Edward Sun and Di Luo and Wei Wang},
  year={2025},
  eprint={2412.20138},
  archivePrefix={arXiv},
  url={https://arxiv.org/abs/2412.20138}
}
```
