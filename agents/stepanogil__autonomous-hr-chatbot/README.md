# Autonomous HR Chatbot

An autonomous HR assistant agent that answers employee queries using a suite of
specialized tools — all powered by OpenAI's language models.

## What it does

Employees can ask natural-language questions about HR policies and their personal
records, and the agent autonomously selects the right tool to answer:

| Query type | Tool used |
|---|---|
| "What's the policy on unused vacation leave?" | **Timekeeping Policies** — semantic search over the official HR policy document (Pinecone / OpenAI file-search vector store) |
| "How many sick days do I have left?" | **Employee Data** — Python/pandas REPL querying a structured employee dataset |
| "If I work 3 extra hours each day for 2 weeks, how many overtime hours is that?" | **Calculator** — LangChain LLMMathChain / arithmetic |

## Key capabilities

- **Policy retrieval** via RAG: embeddings generated with `text-embedding-ada-002` and stored in Pinecone; v2 uses OpenAI's built-in `file_search` tool.
- **Employee data analysis** via a Python AST REPL with access to a pandas dataframe of employee records.
- **Arithmetic** via LangChain's LLMMathChain (v1) or model reasoning (v2).
- **Streaming front-end** built with Streamlit, including live reasoning-summary display in v2.
- Two implementations included: `v1` (LangChain + Pinecone, 2023) and `v2` (OpenAI Responses API + GPT-5, 2026).

## Tech stack

- **LLM**: GPT-3.5-turbo (v1) / GPT-5 with reasoning summaries (v2)
- **Orchestration**: LangChain agents (v1) / OpenAI Responses API agent loop (v2)
- **Vector store**: Pinecone (v1) / OpenAI file-search vector store (v2)
- **Front-end**: Streamlit
- **Data**: pandas CSV employee dataset + plain-text HR policy document

## Example usage

```
User: What is the policy on unused vacation leave?
Agent: [searches Timekeeping Policies] According to the policy, unused vacation
       leave of up to 10 days may be carried over to the following year...

User: How many sick leaves do I have left?
Agent: [queries Employee Data] You have 7 sick leave days remaining.
```

## Getting started

See the [README](https://github.com/stepanogil/autonomous-hr-chatbot#how-to-use-this-repo)
for setup instructions. You will need OpenAI and Pinecone API keys (v1) or just
an OpenAI key with a vector store set up (v2).

## Links

- **Repo**: https://github.com/stepanogil/autonomous-hr-chatbot
- **Blog post**: https://medium.com/@stephen.bonifacio/creating-a-mostly-autonomous-hr-assistant-with-chatgpt-and-langchains-agents-and-tools-1cdda0aa70ef
- **Video demo**: https://www.youtube.com/watch?v=id7XRcEIBvg
