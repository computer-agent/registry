# Claude Code Agents Collection

A curated set of **seven specialized QA and verification sub-agents** for
[Claude Code](https://claude.ai/code). Each agent owns a distinct quality-assurance
discipline so your team has the right expert for every review scenario.

## Agents

| Agent | File | What it does |
|---|---|---|
| **Jenny** | `Jenny.md` | Compares the live codebase against written specifications, file-by-file, line-by-line. Surfaces gaps with severity levels and file references. |
| **Karen** | `karen.md` | Goes and *runs* the thing. Validates claimed completions by executing the code path, not by reading it. Blunt about what is and isn't working. |
| **Claude MD Compliance Checker** | `claude-md-compliance-checker.md` | Ensures every change obeys the project's `CLAUDE.md` conventions. Catches drift before it becomes habit. |
| **Code Quality Pragmatist** | `code-quality-pragmatist.md` | Hunts over-engineering: enterprise abstractions in MVPs, unnecessary caches, infinite middleware. Pushes toward simple, maintainable code. |
| **Task Completion Validator** | `task-completion-validator.md` | Verifies "done" means "actually works". Looks for TODOs, empty catch blocks, tests that only test mocks, and fake integrations. |
| **UI Comprehensive Tester** | `ui-comprehensive-tester.md` | Systematic UI validation across web and mobile. Auto-selects Puppeteer, Playwright, or Mobile MCP. Tests flows and edge cases. |
| **Ultrathink Debugger** | `ultrathink-debugger.md` | Deep root-cause analysis when other attempts have failed. Traces execution end-to-end, fixes causes not symptoms. |

## How to use

Copy any `.md` file into your project's `.claude/agents/` directory. Claude Code
will pick it up as a sub-agent. Invoke it by name when you need its specialty.

### Example workflow

```
# After implementing a feature:
task-completion-validator → confirm it works
code-quality-pragmatist   → check for over-engineering
claude-md-compliance-checker → verify project rules
```

```
# When something is "done" but feels off:
karen → reality-check the completion
jenny → spec-vs-implementation audit
```

## Cross-agent collaboration

The agents are designed to delegate to each other:
- Jenny calls Karen for end-to-end validation
- Karen calls Jenny when spec complexity is high
- All agents use `file_path:line_number` format and shared severity levels (`Critical | High | Medium | Low`)

## GAP compatibility

This collection ships with an `agent.yaml` + `SOUL.md` at the repo root, making it
fully compatible with the [GitAgent Protocol](https://gitagent.sh). Drop it into
any GAP-compatible runtime and it works out of the box.

## Repository

https://github.com/darcyegb/ClaudeCodeAgents
