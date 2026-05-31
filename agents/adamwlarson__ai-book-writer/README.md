# AI Book Writer

A collaborative multi-agent system built on [AutoGen](https://github.com/microsoft/autogen) that turns a single creative premise into a complete, polished, multi-chapter book.

## What it does

Six specialised agents work in a structured pipeline:

| Agent | Responsibility |
|---|---|
| **Story Planner** | Maps the high-level arc — plot points, character arcs, story beats, transitions |
| **Outline Creator** | Produces a detailed N-chapter outline in a strict, parseable format |
| **World Builder** | Establishes every setting, atmosphere, and sensory detail the story requires |
| **Memory Keeper** | Tracks continuity after each chapter; raises alerts on inconsistencies |
| **Writer** | Authors the actual prose (hard minimum: 5 000 words per chapter) |
| **Editor** | Reviews drafts for quality, outline alignment, and character consistency |

## Example usage

```bash
git clone https://github.com/adamwlarson/ai-book-writer.git
cd ai-book-writer
pip install -r requirements.txt
# Start LM Studio (or any OpenAI-compatible local server) then:
python main.py
```

Enter a premise when prompted (e.g. *"A retired astronaut discovers a second moon has appeared overnight"*) and specify the number of chapters. The pipeline runs fully autonomously until the manuscript is complete.

## Key capabilities

- Fully local — no cloud API required by default (uses `http://localhost:1234/v1`)
- Continuity-aware — the Memory Keeper prevents plot holes across chapters
- Quality-gated — the Editor enforces the 5 000-word minimum before approving any chapter
- Outline-driven — all agents defer to the canonical chapter outline

## Repository

https://github.com/adamwlarson/ai-book-writer
