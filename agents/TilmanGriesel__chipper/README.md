# Chipper

**Chipper** is a modular, hackable, privacy-first RAG (Retrieval-Augmented Generation) agent platform for tinkerers, educators, and builders who want powerful local LLM workflows without sending data to the cloud.

---

## Run

```bash
npx @open-gitagent/gitagent run -r https://github.com/TilmanGriesel/chipper
```

---

## What It Can Do

| Skill | Description |
|---|---|
| **RAG Query** | Answer questions grounded in your documents via ElasticSearch vector retrieval |
| **Document Embed** | Chunk and vectorize documents into the knowledge base |
| **Web Scrape** | Extract and index content from web pages |
| **Audio Transcribe** | Convert audio files to text and index the transcript |
| **Ollama API Proxy** | Proxy any Ollama client request with server-side RAG and system prompt injection |

---

## Key Features

- **Local & Cloud Models** — Run models via [Ollama](https://ollama.com/) locally or connect to [Hugging Face](https://huggingface.co/) API
- **ElasticSearch Integration** — Scalable, vectorized document storage and retrieval
- **Fully Dockerized** — One `docker compose up` and it's running
- **Ollama API Compatible** — Works as a drop-in proxy for Enchanted, Open WebUI, Ollamac, and the Ollama CLI
- **Offline Web UI** — Built with vanilla JS + TailwindCSS, no internet required
- **Edge TTS** — Listen to responses using WebAssembly-based client-side TTS
- **Distributed Processing** — Chain multiple Chipper instances together

## Why Chipper?

Chipper was born from a real need: to help explore a book's characters and ideas using local LLMs, keeping private creative work entirely off the cloud. That origin gives it a clear soul — **privacy-first, approachable, and built to be forked**.

**Live demo:** https://demo.chipper.tilmangriesel.com/
**Project site:** https://chipper.tilmangriesel.com/

## Setup

```bash
git clone https://github.com/TilmanGriesel/chipper.git
cd chipper
python setup.py          # interactive setup
docker compose up -d     # launch all services
```

See the [full setup guide](https://chipper.tilmangriesel.com/get-started.html) for detailed instructions.
