# Integuru

**Integuru** is an AI agent that builds permissionless integrations by reverse-engineering the internal APIs of any web platform — even platforms that publish no official API.

## What It Does

Point Integuru at a browser session (HAR file + cookies) and describe the action you want to automate. Integuru will:

1. **Identify the target endpoint** — from hundreds of captured requests, it finds the one responsible for your described action using LLM reasoning.
2. **Build a dependency graph** — dynamic values (session tokens, account IDs, CSRF tokens) are traced back recursively to their source requests, forming a Directed Acyclic Graph (DAG).
3. **Generate runnable Python code** — each node in the DAG becomes a Python function; the full traversal reproduces the authenticated action end-to-end.

## Key Capabilities

- HAR file parsing and network request/response analysis
- LLM-driven dynamic-part identification (tokens, IDs, session variables)
- Recursive dependency graph construction
- Clean Python code generation with no manual curl-wrangling
- Support for 2FA-protected platforms (capture cookies post-2FA)
- Input variable substitution (e.g., parameterise the year in a document download)

## Example Usage

\`\`\`bash
# Capture browser session
poetry run python create_har.py

# Run the agent
poetry run integuru --prompt "download utility bills" --model gpt-4o
\`\`\`

## Models

- Primary: **GPT-4o** (graph building, function calling)
- Fallback: **o1-preview** (code generation)

## Links

- GitHub: https://github.com/Integuru-AI/Integuru
- Live product: https://www.integuru.com
