# django-ai-assistant

A Django library that lets developers integrate LLM-powered AI assistants into their web applications in minutes — with full tool calling, RAG, and a multi-turn conversation model baked in.

## What it does

`django-ai-assistant` sits between your Django application and an LLM (OpenAI GPT-4o, Anthropic Claude, or Google Gemini). Developers subclass `AIAssistant`, decorate Python methods with `@ai_assistant_tool`, and instantly have an assistant that can reason over user requests and call those methods — querying databases, sending notifications, calling third-party APIs — all within Django's permission model.

## Key capabilities

- **Tool calling** — Expose any Django logic as an agent tool using a single decorator
- **RAG** — Override `get_instructions()` to inject dynamic context (querysets, vector results) into each turn
- **Thread management** — Conversations are persisted as `Thread` + `Message` Django models with per-user ownership
- **Auto REST API** — django-ninja generates a full CRUD API for threads and messages automatically
- **Multi-provider** — Works with OpenAI, Anthropic, and Google Gemini via LangChain extras

## Example usage

```python
from django_ai_assistant import AIAssistant, ai_assistant_tool

class MovieRecommendationAssistant(AIAssistant):
    name = "Movie Recommendation Assistant"
    instructions = "You are a helpful movie expert. Use your tools to find great films."
    model = "gpt-4o"

    @ai_assistant_tool
    def search_movies(self, genre: str) -> list[str]:
        """Search for movies by genre."""
        return list(Movie.objects.filter(genre=genre).values_list("title", flat=True)[:10])
```

## Installation

```bash
pip install django-ai-assistant[openai]  # or [anthropic] / [google]
```

## Resources

- 📖 [Documentation](https://vintasoftware.github.io/django-ai-assistant/)
- 💬 [Discord Community](https://discord.gg/fQfH9PkJM6)
- 🐙 [GitHub Repository](https://github.com/vintasoftware/django-ai-assistant)
- 🏢 Maintained by [Vinta Software](https://www.vinta.com.br/)
