# Newsletter AI Agent

A Claude-based newsletter co-writer and publishing assistant by [@iancarson](https://github.com/iancarson).

**Repository:** https://github.com/iancarson/newsletter-ai-agent

---

## What it does

This agent automates the full newsletter publishing workflow — from research and
drafting to cross-platform repurposing and scheduling — so writers can reduce
distribution overhead from hours to minutes per week.

### Key capabilities

- **Draft newsletter issues** from a topic brief (hook → insight → evidence → takeaway → CTA)
- **Repurpose content** into Substack Notes (≤400 chars), LinkedIn posts, and X/Twitter threads
- **Publish via Substack MCP** — saves drafts and Notes through a connected MCP server
- **Sunday batch prep** — one trigger generates 5 Notes, LinkedIn adaptations, an X thread, and a weekly posting schedule
- **Analyze past issues** — identifies topic coverage gaps and reader patterns
- **Voice-matched output** — configurable for any publication's style, audience, and banned words

### Workflow triggers

| Say this… | Agent does this |
|---|---|
| "run the weekly workflow" | Research + draft 5 Notes + LinkedIn + X thread + save drafts + schedule |
| "repurpose [issue]" | Extract insights → Notes → LinkedIn → X thread → confirm before posting |
| "draft this week's newsletter" | Full issue draft saved to Substack |
| "find topic gaps" | Pulls last 20 issues → coverage analysis → 3 topic recommendations |

### Safety model

The agent uses `human_in_the_loop: destructive` — it **always confirms** before
publishing or posting to any platform. Social MCP tools are used for publishing
only, never for bulk engagement.

### MCP stack

Designed to work with:
- `@marcomoauro/substack-mcp` for draft/publish
- `@modelcontextprotocol/server-brave-search` for research
- `@modelcontextprotocol/server-filesystem` for local drafts

### Example usage

```
Run my Sunday newsletter prep workflow.

This week's topic: The ROI of writing in public

Target outputs:
- 5 Substack Notes (save as drafts)
- LinkedIn adaptations of Notes 1 and 3
- 1 X thread from the key insight
- Suggested posting schedule Mon–Fri
```

---

*Onboarded to the GitAgent Protocol by the [GAP Promoter](https://github.com/open-gitagent/opengap).*
