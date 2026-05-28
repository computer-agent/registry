# superflow-builder

A git-native ([openGAP](https://github.com/open-gitagent/opengap)) agent that writes superflow JSON workflows for the superflow engine.

## What it does

Takes a process description — phase-by-phase blueprint, natural-language sketch, or feature request — and produces a single, executable workflow JSON. Designs against the real executor contracts (parameter shapes, expression semantics, durable-execution constraints) so the output runs end-to-end on the first try.

## What it produces

- The full workflow JSON printed inline in the response (fenced as ` ```json `) — copy-paste straight into your engine, pipe to a file, or hand to a Studio import
- A short narrative: trigger source, phase-by-phase data flow, what verdict the mock data lands at, and the one-line edits to flip between demo paths
- File output on request — pass an explicit target path and the agent writes it instead of (or in addition to) the inline JSON

## When to use it

- Building a new workflow from a product spec or process blueprint
- Adapting an existing workflow when the engine's executors gain new capabilities
- Debugging a workflow that "passed locally but fails in production" — the agent knows the durable-mode rules cold
- Writing demo flows for stakeholders where the verdict path must be deterministic

## Key capabilities

- **DAG composition** — fan-out, convergence, sibling parallelism, multi-output routing
- **Code node semantics** — goja sandbox, last-expression return, input identification by predicate
- **Expression engine** — `{{ }}` template substitution and the JS reference patterns it supports
- **HITL approval mechanics** — form schemas, durable awakeables, approval/rejection routing
- **HTTP body preservation patterns** — echo through body, second-parent edge
- **Demo mock-data design** — deterministic test inputs that exercise specific verdict paths

## Structure

```
superflow-builder/
├── agent.yaml          # Manifest (model, skills, runtime)
├── SOUL.md             # Identity and collaboration style
├── RULES.md            # Hard constraints (must always / must never)
├── PROMPT.md           # Default task framing and output format
├── AGENTS.md           # Framework-agnostic fallback instructions
├── README.md
└── skills/
    └── superflow/
        └── SKILL.md    # Node-type registry, contracts, patterns, gotchas
```

## Compatible runtimes

Any framework that supports openGAP-format agents. Confirmed: Claude Code (via the `superflow` skill loaded into `~/.claude/skills/` or invoked via the Skill tool). The standard's framework-agnostic fallback (`AGENTS.md`) supports OpenAI, LangChain, CrewAI, AutoGen, and others.

## License

MIT
