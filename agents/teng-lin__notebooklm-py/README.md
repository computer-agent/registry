# notebooklm-py

**Unofficial Python API and AI-agent skill for Google NotebookLM.** Full programmatic access to NotebookLM's features — including capabilities the web UI doesn't expose — via Python, CLI, and AI agents like Claude Code, Codex, and OpenClaw.

## What It Does

`notebooklm-py` gives agents and developers complete control over Google NotebookLM:

- **Notebook management** — create, list, rename, delete notebooks
- **Source ingestion** — add URLs, YouTube, PDFs, text, Markdown, Word, EPUB, audio, video, images, and Google Drive files
- **Chat** — ask questions, retrieve conversation history, save answers as notes
- **Research** — run web and Google Drive research agents (fast/deep mode) and auto-import sources
- **Content generation** — audio overviews (4 formats, 50+ languages), video overviews (3 formats + cinematic), slide decks, infographics, quizzes, flashcards, reports, data tables, and mind maps
- **Downloads & export** — MP3, MP4, PDF, PPTX, PNG, CSV, JSON, Markdown; batch downloads; quiz/flashcard JSON export; mind map hierarchical JSON
- **Sharing** — manage public/private links and per-user permissions programmatically
- **Multi-account** — named profiles, `NOTEBOOKLM_PROFILE` env isolation, `NOTEBOOKLM_AUTH_JSON` for CI/CD

## Features Beyond the Web UI

| Feature | Details |
|---------|---------|
| Batch downloads | Download all artifacts of a type at once |
| Quiz / flashcard export | Structured JSON, Markdown, or HTML |
| Mind map JSON | Hierarchical export for visualization tools |
| Data table CSV | Download structured tables as spreadsheets |
| Slide deck as PPTX | Editable PowerPoint (web UI only offers PDF) |
| Slide revision | Modify individual slides with natural-language prompts |
| Source fulltext access | Retrieve indexed text of any source |
| Multi-account profiles | Switch Google accounts without re-authenticating |
| Browser cookie import | Reuse an existing browser session |

## Quick Start

```bash
# Install
pip install "notebooklm-py[browser]"
playwright install chromium

# Authenticate
notebooklm login

# Use
notebooklm create "My Research"
notebooklm source add "https://example.com/paper.pdf"
notebooklm ask "What are the key findings?"
notebooklm generate audio "make it engaging" --wait
notebooklm download audio ./podcast.mp3
```

## Agent Integration (Claude Code / GitAgent)

```bash
# Install the skill into your agent's skill directory
notebooklm skill install
# or via npx
npx skills add teng-lin/notebooklm-py
```

Once installed, agents can invoke NotebookLM capabilities directly:
> "Create a podcast about the linked paper" → notebooklm-py handles the full pipeline.

## Python API

```python
import asyncio
from notebooklm import NotebookLMClient

async def main():
    async with NotebookLMClient.from_storage() as client:
        nb = await client.notebooks.create("Research")
        await client.sources.add_url(nb.id, "https://example.com", wait=True)
        result = await client.chat.ask(nb.id, "Summarize this")
        print(result.answer)
        status = await client.artifacts.generate_audio(nb.id)
        await client.artifacts.wait_for_completion(nb.id, status.task_id)
        await client.artifacts.download_audio(nb.id, "podcast.mp3")

asyncio.run(main())
```

## Notes

- Uses undocumented Google internal APIs — may break without notice.
- Not affiliated with Google.
- Best for prototypes, research pipelines, and personal automation.
- Requires Python 3.10+.
