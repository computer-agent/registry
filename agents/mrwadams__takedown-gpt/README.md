# TakedownGPT ⬇️🤖

**TakedownGPT** is a LangChain-powered AI agent that automates the tedious
research and drafting involved in filing domain takedown requests. Built by
[Matt Adams](https://github.com/mrwadams), it combines WHOIS/RDAP lookups,
live web search, and GPT-powered email drafting into a single autonomous workflow.

## What it does

Given a domain name and a takedown reason, the agent:

1. **Identifies the domain registrar** — via WHOIS or RDAP lookup
2. **Finds the abuse contact** — web-searches the registrar's takedown email address
3. **Drafts a professional takedown email** — citing the stated reason and any additional context

Supported takedown reasons include copyright infringement, trademark infringement,
defamation/libel, privacy violations, malware/phishing, terms-of-service
violations, personal safety concerns, and custom reasons.

## Tools / Skills

| Tool | Description |
|------|-------------|
| `get_registrar` | WHOIS lookup to identify the domain registrar |
| `rdap_lookup` | RDAP protocol alternative for registrar queries |
| `Search` | DuckDuckGo web search to find abuse contact emails |

## Example usage

```
Domain: malicious-phishing-site.com
Reason: Malware or phishing activities
→ Agent finds registrar (e.g. GoDaddy), locates abuse@godaddy.com,
  drafts a takedown request email ready to send.
```

## Model

- Preferred: `openai:gpt-4o`
- Fallback: `openai:gpt-3.5-turbo`

## Human-in-the-loop

The agent **drafts** the takedown email but does **not** submit it automatically.
The human reviews and sends — `human_in_the_loop: destructive`.

## Links

- 📦 Repository: https://github.com/mrwadams/takedown-gpt
- 🚀 Live demo: https://takedowngpt.streamlit.app
