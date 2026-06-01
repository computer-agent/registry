# Prompt Blueprint — PromptCraft∞ Elite

A professional prompt-engineering AI agent that transforms your simple requirements into **production-ready, fully documented prompts** — optimized for GPT-4, Claude, Gemini, and open-source models.

## What It Does

*Prompt Blueprint* provides two agents and a library of best-practice guides:

- **PromptCraft∞ Elite** — the main agent. Give it any prompt requirement and it executes a 7-stage professional workflow, delivering a complete package: production prompt + usage guidelines + performance benchmarks + troubleshooting playbook.
- **Documentation Expert Agent** — generates exhaustive, GitHub-optimized Markdown documentation from structured or unstructured inputs.
- **Best-Practice Guides** — distilled guides from OpenAI, Anthropic, Google, and more.

## Try It

```bash
# Run with Claude Code or any GAP-compatible runtime
gitagent run -r https://github.com/thibaultyou/prompt-blueprint \
  -p "I need a customer support prompt for a SaaS product, optimized for Claude"
```

Or paste `meta-prompts/prompt-engineering-agent.md` directly into ChatGPT, Claude, or Gemini.

## 7-Stage Workflow

1. **Requirements Intelligence Gathering** — Extracts domain, model, success metrics, and constraints
2. **Task Decomposition** — Maps primary goals, sub-goals, and failure modes
3. **Framework Selection** — Picks the right reasoning approach (CoT, ToT, ReAct, etc.)
4. **Triple-Draft Development** — Produces Variant A (efficiency), B (reliability), C (innovation)
5. **Evaluation & Synthesis** — Scores each variant across 7 dimensions; merges best elements
6. **Enterprise QA** — Safety audit, regulatory check, edge-case stress test
7. **Professional Delivery** — Final prompt + benchmarks + troubleshooting guide

## Key Capabilities

- ✅ **Cross-model compatibility** — GPT-4, Claude, Gemini, LLaMA, Mistral
- ✅ **Enterprise QA** — Constitutional AI compliance, bias detection, GDPR/HIPAA/SOX checks
- ✅ **A/B/C variant drafting** — Compare efficiency vs reliability vs innovation trade-offs
- ✅ **Complete delivery package** — Prompt + docs + metrics + troubleshooting in one go
- ✅ **Zero infrastructure** — Drop the markdown into any AI interface and start immediately

## Repository Structure

| Path | Contents |
|------|----------|
| `meta-prompts/prompt-engineering-agent.md` | PromptCraft∞ Elite — the main agent |
| `meta-prompts/documentation-expert-agent.md` | Documentation generation agent |
| `guides/` | Best-practice guides (OpenAI, Anthropic, Google, unified) |
| `examples/` | Ready-to-use prompt outputs |
| `agent.yaml` | GAP manifest |
| `SOUL.md` | Agent persona and operating principles |
