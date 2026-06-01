# Paper Claw

An intelligent research digest agent that monitors arXiv daily, classifies papers by topic, generates concise multilingual summaries using your preferred LLM provider, and delivers personalised HTML and Markdown email digests.

---

## Run

```bash
npx @open-gitagent/gitagent run -r https://github.com/PigeonDan1/paper_claw
```

---

## What It Can Do

- **Multi-Source Fetching** — arXiv (170+ categories); extensible to other academic sources
- **Topic Classification** — Keyword-based classification into user-defined research categories (e.g. ASR, TTS, LLM, RAG, Object Detection, Diffusion Models)
- **Multilingual AI Summaries** — Generates 2–4 sentence summaries in Chinese, English, Japanese, Korean, German, French, or Spanish — faithful to the abstract, never invented
- **Multi-Provider LLM** — DeepSeek → Kimi → OpenAI → Anthropic Claude → Gemini → rule-based fallback; resilient even without API keys
- **Email Delivery** — HTML preview (first 3 papers) + full Markdown digest as attachment, sent to configurable recipient list
- **Research Presets** — One-command setup for Speech & Audio, NLP & LLM, Computer Vision, or General AI/ML research
- **State Tracking** — Auto-deduplication across runs; never emails a paper twice
- **GitHub Actions Ready** — Includes daily workflow for zero-ops scheduled digests

---

## Setup

```bash
git clone https://github.com/PigeonDan1/paper_claw.git
cd paper_claw
pip install -r requirements.txt
cp .env.example .env        # add SMTP + LLM API keys
cp config/recipients.example.json config/recipients.json
python scripts/main.py --day 2026-03-10
```

Or, for AI agents, apply a preset in one line:

```python
from skill.example import apply_preset
apply_preset("nlp")  # configures arXiv categories + classification automatically
```

---

## Configuration

| Variable | Required | Description |
|----------|----------|-------------|
| `SMTP_HOST` | ✅ | SMTP server host |
| `SMTP_PORT` | ✅ | SMTP port (usually 465) |
| `SMTP_USER` | ✅ | Sender email address |
| `SMTP_PASS` | ✅ | SMTP auth token or app password |
| `DEEPSEEK_API_KEY` | ☑️ | Preferred provider for summaries |
| `MOONSHOT_API_KEY` | ☑️ | Kimi (recommended for Chinese) |
| `OPENAI_API_KEY` | ☑️ | OpenAI fallback |
| `ANTHROPIC_API_KEY` | ☑️ | Claude fallback |
| `GOOGLE_API_KEY` | ☑️ | Gemini fallback |

At least one LLM API key is recommended; rule-based summaries work without any.

> **Note:** `agent.yaml` and `SOUL.md` are being added to the repo via [PR #2](https://github.com/PigeonDan1/paper_claw/pull/2). This registry entry will pass CI validation once that PR is merged.
