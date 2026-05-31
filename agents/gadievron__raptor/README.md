# RAPTOR — Autonomous Security Research Framework

**RAPTOR** (Recursive Autonomous Penetration Testing and Observation Robot) is an autonomous
offensive/defensive security research framework built on top of Claude Code. It chains together
static analysis, binary analysis, LLM-powered vulnerability validation, exploit generation, and
patch writing into a single end-to-end workflow.

Point it at a codebase or binary and it hunts, validates, and reports exploitable vulnerabilities
— with full project management, multi-model consensus, and forensic-grade evidence handling.

## Key Capabilities

- **`/scan`** — Semgrep + language-specific static analysis
- **`/agentic`** — Full autonomous pipeline: scan → dedup → LLM analysis → validation
- **`/fuzz`** — Fuzzing campaigns
- **`/codeql`** — CodeQL dataflow and taint analysis with SMT-based path validation
- **`/validate`** — Staged exploitability validation pipeline (inventory → reachability → mitigation check → PoC)
- **`/understand`** — Adversarial code comprehension (map attack surface, trace data flows, hunt variants)
- **`/crash-analysis`** — Autonomous root-cause analysis for C/C++ crashes using deterministic record-replay (rr)
- **`/oss-forensics`** — Evidence-backed forensic investigation of public GitHub repositories
- **`/exploit`** — Proof-of-concept exploit generation
- **`/patch`** — Fix generation for confirmed vulnerabilities
- **`/diagram`** — Mermaid visual maps from analysis outputs (attack trees, data flow graphs)

## Philosophy

RAPTOR thinks like an attacker and a defender simultaneously. It is honest about exploitability
(`Unlikely` / `Difficult` / `Likely Exploitable`) and always offers next steps. Safe operations
(scan, read, generate) proceed autonomously; destructive operations (apply patches, git push)
require human confirmation.

## Quick Start

```bash
git clone https://github.com/gadievron/raptor.git
cd raptor
# Set up Claude Code with the repo as working directory
# Run: /agentic --target /path/to/target-codebase
```

## Authors

Gadi Evron, Daniel Cuthbert, Thomas Dullien (Halvar Flake), Michael Bargury, John Cartwright

## Links

- Repository: https://github.com/gadievron/raptor
- License: MIT (CodeQL has its own license — no commercial use)
