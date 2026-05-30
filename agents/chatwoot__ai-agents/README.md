# AI Agents — Ruby SDK

A delightful, provider-agnostic **Ruby SDK for building sophisticated multi-agent AI workflows** with seamless handoffs, tool integration, shared context, and real-time callbacks.

Maintained by the [Chatwoot](https://chatwoot.com) team. MIT licensed.

> **Note:** A PR proposing `agent.yaml` + `SOUL.md` to the upstream repo is open at
> [chatwoot/ai-agents#69](https://github.com/chatwoot/ai-agents/pull/69).
> The registry entry points to the fork branch where the GAP files already live.
> Once the upstream PR is merged, the `repository` field will be updated to the canonical URL.

## What It Does

`ai-agents` gives Ruby developers all the primitives needed to build multi-agent systems:

| Capability | Description |
|---|---|
| **Multi-Agent Orchestration** | Create specialist agents with distinct roles, instructions, and tools |
| **Seamless Handoffs** | Transparent, automatic agent-to-agent transfers mid-conversation |
| **Tool Integration** | Extend agents with custom Ruby classes that call APIs, query databases, trigger workflows |
| **Thread-Safe Runners** | Reusable `AgentRunner` instances safe for concurrent request handling |
| **Shared Context** | Fully serialisable conversation state that persists across process restarts |
| **Real-Time Callbacks** | Event hooks for agent thinking, tool start/complete, handoffs, and errors |
| **Structured Output** | JSON schema–validated responses for reliable data extraction |
| **Provider-Agnostic** | Works with OpenAI, Anthropic, Gemini, and any LLM supported by RubyLLM |

## Quick Start

```ruby
gem 'ai-agents'
```

```ruby
require 'agents'

Agents.configure do |config|
  config.openai_api_key = ENV['OPENAI_API_KEY']
end

support = Agents::Agent.new(
  name: "Support Agent",
  instructions: "Help users resolve account and billing issues",
  tools: [FaqLookupTool.new, TicketTool.new]
)

runner = Agents::Runner.with_agents(support)
result = runner.run("I can't log in to my account")
puts result.output
```

## Multi-Agent Example (ISP Support)

```ruby
triage  = Agents::Agent.new(name: "Triage",  instructions: "Route customers to the right specialist")
sales   = Agents::Agent.new(name: "Sales",   instructions: "Answer questions about plans",   tools: [CreateLeadTool.new])
support = Agents::Agent.new(name: "Support", instructions: "Handle technical issues",         tools: [TicketTool.new])

runner = Agents::Runner.with_agents(triage, sales, support)
result = runner.run("I want to upgrade my plan")
# → automatically hands off triage → sales
```

Run the full interactive ISP demo:
```bash
ruby examples/isp-support/interactive.rb
```

## Links

- **Upstream repo:** https://github.com/chatwoot/ai-agents
- **GAP adoption PR:** https://github.com/chatwoot/ai-agents/pull/69
- **RubyGem:** `ai-agents`
- **Docs:** https://github.com/chatwoot/ai-agents/tree/main/docs
- **Changelog:** https://github.com/chatwoot/ai-agents/blob/main/CHANGELOG.md
