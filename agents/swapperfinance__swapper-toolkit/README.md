# swapper-toolkit

The payment layer for AI agents. **Swapper Toolkit** gives any AI agent or coding
assistant the ability to deposit funds, bridge crypto assets, and manage wallets —
without leaving the conversation.

Handles fiat on-ramps (Mastercard, Visa, Apple Pay, Google Pay, 170+ countries),
crypto transfers, and cross-chain bridging via Chainlink CCIP into lending, staking,
and liquidity pools. Powered by Chainlink CRE for end-to-end workflow orchestration.

---

## Run

```bash
npx @open-gitagent/gitagent run -r https://github.com/swapperfinance/swapper-toolkit
```

Or install as a skill pack into any compatible agent:

```bash
npx skills add swapperfinance/swapper-toolkit
```

---

## Key Capabilities

- **`/swapper-deposit`** — Generate deposit deep-links for wallets and DeFi protocols.
  Collects destination wallet address, chain ID, and token contract, then surfaces a
  Swapper widget link the user confirms in-browser. Never auto-executes.
- **Fiat on-ramp** — Accepts Mastercard, Visa, Apple Pay, Google Pay across 170+ countries;
  converts fiat to crypto and lands it in the target wallet or protocol.
- **Cross-chain bridging** — Routes assets via Chainlink CCIP across Ethereum, Base,
  Arbitrum, Optimism, Polygon, Solana, BNB Chain, Avalanche, HyperEVM, and Fast.
- **Mid-task funding** — Detects when a wallet has insufficient funds during an agent
  workflow and proactively offers to top it up before the operation fails.

---

## Safety

- Every transaction requires **explicit user confirmation** via the Swapper widget.
- Deep-links are generated, not executed — the user always approves in their browser.
- Private keys are never stored, requested, or logged.
- Fees, slippage, and cross-chain risks are surfaced before confirmation.

---

## Supported Chains

| Chain       | Chain ID |
|-------------|----------|
| Ethereum    | 1        |
| Base        | 8453     |
| Arbitrum    | 42161    |
| Optimism    | 10       |
| Polygon     | 137      |
| Solana      | solana   |
| BNB Chain   | 56       |
| Avalanche   | 43114    |
| HyperEVM    | 999      |
| Fast        | fast     |

---

## Works With

Claude Code, Cursor, Windsurf, OpenClaw, GitHub Copilot, CrewAI, AutoGPT, LangChain,
and any AI agent framework that supports the open skills standard.

---

## Built with

[gitagent](https://github.com/open-gitagent/gitagent) — a git-native, framework-agnostic open standard for AI agents.
