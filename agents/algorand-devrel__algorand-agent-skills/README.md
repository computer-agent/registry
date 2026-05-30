# Algorand Agent Skills

A canonical collection of agent skills and configurations for **AI-assisted Algorand blockchain development**. Drop these skills into any AI coding assistant — Claude Code, OpenCode, Cursor, or GitHub Copilot — and it gains deep, accurate knowledge of the Algorand ecosystem.

## What it does

The agent teaches AI assistants to build correct, idiomatic Algorand applications by loading only the reference files they need (progressive disclosure):

| Skill | Purpose |
|---|---|
| `algorand-core` | AVM mental model — stack machine, `uint64`/`bytes` types, opcode budgets, resource limits |
| `algorand-project-setup` | AlgoKit project init, CLI commands, examples |
| `algorand-typescript` | Full TypeScript lifecycle: PuyaTs syntax, testing, deployment, AlgoKit Utils, ARC standards |
| `algorand-python` | Full Python lifecycle: PuyaPy syntax, testing, deployment, AlgoKit Utils, ARC standards |
| `algorand-frontend` | React dApps with `@txnlab/use-wallet-react` and the signer-handoff pattern |
| `algokit-utils-ts` / `algokit-utils-py` | Typed client setup, payments, assets, contract interaction |
| `algorand-x402-typescript` | TypeScript x402 HTTP-native payments: clients, servers, facilitators, paywalls |
| `algorand-x402-python` | Python x402 HTTP-native payments: clients, servers, facilitators, Bazaar |

## Key capabilities

- Prevents AVM mistakes caused by treating Algorand like EVM or writing TEAL by hand
- Routes to canonical AlgoKit CLI build/test/deploy pipeline
- Integrates MCP tools for live documentation search (`kapa`) and code examples (`github`)
- Covers x402, the HTTP-native payment protocol built on Algorand

## Example usage

```bash
# In an AlgoKit project, add the skills:
cp -r algorand-agent-skills/skills ./
cp algorand-agent-skills/setups/AGENTS.md ./
cp algorand-agent-skills/setups/claude-code/.mcp.json ./
cp algorand-agent-skills/setups/claude-code/CLAUDE.md ./

# Then in Claude Code:
# "Build a smart contract that holds ALGO and releases on condition"
# → agent loads algorand-core, then algorand-typescript, searches docs, writes PuyaTs
```

## Supported runtimes

Claude Code, OpenCode, Cursor, GitHub Copilot — setup guides in `setups/`.
