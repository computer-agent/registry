# Ouroboros — Agent OS

> *Stop prompting. Start specifying.*

**Ouroboros** is a specification-first Agent OS for AI coding workflows. It replaces ad-hoc
prompting with a structured, mathematically-gated workflow that exposes hidden assumptions
*before* any code is written.

## What It Does

Ouroboros enforces two mathematical gates that turn non-deterministic AI coding into
a replayable, auditable process:

**Gate 1 — Ambiguity ≤ 0.2** (Wonder → Ontology)
Before writing a single line of code, Ouroboros conducts a Socratic interview scoring
clarity across Goal (40%), Constraints (30%), and Success Criteria (30%). If the
weighted ambiguity score exceeds 0.2, the interview continues — because unclear specs
produce wasteful code.

**Gate 2 — Similarity ≥ 0.95** (Evolutionary Convergence)
After each evaluate–evolve cycle, Ouroboros compares the new ontology to the previous
generation. It stops when the design has mathematically stabilized, preventing endless
churn and scope creep.

## The Workflow Loop

```
Interview → Seed → Execute → Evaluate
    ↑                           ↓
    └─────── Evolutionary Loop ──┘
```

| Step | Command | What happens |
|---|---|---|
| 1 | `ooo interview` | Socratic dialogue — surfaces hidden assumptions |
| 2 | `ooo seed` | Crystallizes the verified spec into a replayable Seed |
| 3 | `ooo run` | Executes against the Seed via MCP-bound runtime |
| 4 | `ooo evaluate` | Scores outcomes against the Seed's success criteria |
| 5 | `ooo evolve` | Feeds evaluation back into a refined spec; repeat |
| ∞ | `ooo auto` | Runs the full loop automatically end-to-end |

## Key Capabilities

- **Multi-runtime**: Works with Claude Code, Codex CLI, OpenCode, and Hermes via MCP adapters
- **Ledger-backed**: Every Seed, execution, and evaluation is committed and replayable
- **20 built-in skills**: interview, seed, run, evaluate, evolve, qa, unstuck, auto, brownfield, pm, publish, ralph, tutorial, setup, update, cancel, resume-session, welcome, status, help
- **Specialist personas**: socratic-interviewer, ontologist, seed-architect, evaluator, qa-judge, contrarian, hacker, simplifier, researcher, architect
- **Safety-first**: Destructive operations surface for human confirmation; audit logging built-in
- **Ambiguity math**: Reproducible scoring at temperature 0.1 — clarity by measurement, not vibes

## Installation

```bash
# Via Claude plugin marketplace
claude plugin marketplace add Q00/ouroboros
claude plugin install ouroboros@ouroboros

# Via PyPI
pip install ouroboros-ai
```

## Example Session

```
You: ooo interview
Ouroboros: Let's clarify what you're building. What is the core goal? ...
[Socratic dialogue until Ambiguity ≤ 0.2]

You: ooo seed
Ouroboros: ✅ Seed crystallized. Ambiguity: 0.14. Ready to run.

You: ooo run
Ouroboros: Executing against Seed v1... [MCP-bound]

You: ooo evaluate
Ouroboros: Similarity: 0.82 — evolving...

You: ooo evolve
Ouroboros: Generation 2 seeded. [loop continues until Similarity ≥ 0.95]
```

## Links

- **Repository**: https://github.com/Q00/ouroboros
- **PyPI**: https://pypi.org/project/ouroboros-ai/
- **Plugin**: `claude plugin marketplace add Q00/ouroboros`
- **License**: MIT

---

*"The beginning is the end, and the end is the beginning. The serpent does not repeat — it evolves."*
