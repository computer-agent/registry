# agent-redteam

An agentic LLM red-team harness that uses **Claude** to systematically probe AI agent system prompts for security vulnerabilities — including prompt injection, identity spoofing, credential exfiltration, privilege escalation, goal hijacking, and safety-boundary bypass.

Built as a research artifact by Fajar Sajid (Purdue University), it found a **49.5% mean violation rate** across 384 trials against a real e-commerce agent prompt.

---

## Run

```bash
npx @open-gitagent/gitagent run -r https://github.com/fajarsajid/agent-redteam
```

---

## What It Can Do

- **Adversarial Probe Generation** — Crafts realistic, target-tailored probes across 8 MITRE-mapped attack categories using Claude as the red-team analyst
- **Vulnerability Analysis** — Evaluates whether a target system prompt is susceptible to each probe, with CVSS-like severity scores (0–10) and attack paths
- **Incident Reporting** — Produces structured JSON findings for SIEM/tooling integration and human-readable Markdown reports
- **CI Pipeline Integration** — Exits `1` on critical/high findings; zero extra dependencies beyond `requests`
- **Multi-turn Assessment** — Evaluates context drift across interaction sequences (single-turn benchmarks underestimate real-world vulnerability ~1.7× at 7 turns)

---

## Attack Categories

| Category | MITRE | Violation Rate (empirical) |
|---|---|---|
| Prompt Injection (Indirect) | T1059 | 70.8% |
| Identity Spoofing | T1078 | 62.5% |
| Prompt Injection (Direct) | T1059 | 54.2% |
| Goal Hijacking | T1565 | 50.0% |
| Privilege Escalation | T1548 | 45.8% |
| Data Exfiltration | T1041 | 41.7% |
| Credential Exfiltration | T1552 | 37.5% |
| Safety Boundary Bypass | T1562 | 33.3% |

---

## Usage

```bash
git clone https://github.com/fajarsajid/agent-redteam
cd agent-redteam
pip install requests
export ANTHROPIC_API_KEY=sk-ant-...

# Quick scan
python redteam.py --prompt examples/orderbot_prompt.txt

# Full run with report output
python redteam.py --prompt system_prompt.txt \
    --probes 3 --output report.md --json findings.json

# CI mode (exit 1 on critical/high findings)
python redteam.py --prompt system_prompt.txt --quiet
```

---

## Structure

```
agent-redteam/
├── agent.yaml              ← GAP manifest
├── SOUL.md                 ← Agent persona & security philosophy
├── redteam.py              ← CLI evaluation tool
├── probe_engine.py         ← Claude-powered adversarial probe generation
├── categories.py           ← Attack taxonomy (8 categories, MITRE-mapped)
├── reporter.py             ← Terminal summary + Markdown incident report
├── test_redteam.py         ← 17/17 unit + mocked API tests
└── examples/
    └── orderbot_prompt.txt ← Target agent used in experiments
```

---

## Built with

[gitagent](https://github.com/open-gitagent/gitagent) — a git-native, framework-agnostic open standard for AI agents.
