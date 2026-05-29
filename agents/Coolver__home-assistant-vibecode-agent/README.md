# HA Vibecode Agent

**HA Vibecode Agent** is a Home Assistant MCP server and AI agent that enables
[Claude Code](https://claude.ai/code), Cursor, VS Code, and any MCP-enabled IDE
to safely manage your smart home using natural language.

## What it does

You describe your goal → the agent inspects your *actual* Home Assistant setup
(entities, devices, HA version, existing automations) → designs a solution that
fits your environment → and deploys it with automatic git versioning so you can
roll back in one command.

### Key capabilities

| Capability | Details |
|---|---|
| **Automation creation** | Generates version-correct YAML, deploys, reloads, and verifies |
| **Dashboard design** | Builds Lovelace layouts with cards, themes, and conditional logic |
| **Config management** | Read/write configuration files with validation before every reload |
| **HACS & add-on management** | Install integrations, custom repositories, and add-ons |
| **Log analysis** | Surfaces structured summaries from raw HA logs |
| **Git versioning & rollback** | Checkpoint before every change; roll back with a single command |

## Architecture

The project has two modules:

- **Home Assistant Agent** — runs inside or alongside HA with native access to
  its REST API, entity state, and file system.
- **Home Assistant MCP Server** — runs on your machine alongside your AI IDE,
  communicating with the Agent over a stable, structured API.

This replaces fragile SSH-based scripting with predictable, context-efficient
automation.

## Safety model

- ✅ Creates a git checkpoint **before** any write operation.
- ✅ Validates `configuration.yaml` **before** any reload.
- ✅ Explains each planned tool call to the user **before** executing.
- ✅ Rolls back with a **full HA restart** (not just a config reload) to ensure
  all file changes take effect.
- ✅ Incremental changes — one component at a time.

## Deployment

| Mode | For whom | How it runs |
|---|---|---|
| **Add-on** | Home Assistant OS / Supervised | Managed add-on in HA Add-on Store |
| **Standalone Docker** | HA Container / Proxmox / NAS | Separate Docker container |

## Quick start

```bash
# Add repository in HA UI → Settings → Add-ons → Add-on Store → Repositories
https://github.com/Coolver/home-assistant-vibecode-agent
```

Then configure your MCP-enabled IDE to connect to the agent's API and start
describing automations in plain language.

## Example

> *"Install smart climate control"*
>
> Agent analyses 7 TRVs → creates 10 automations + 9 helpers + 10 sensors +
> 5 scripts → deploys everything → it just works.

## Links

- **Repository:** https://github.com/Coolver/home-assistant-vibecode-agent
- **Demo:** https://coolver.github.io/home-assistant-vibecode-agent/
- **MCP Package:** https://www.npmjs.com/package/@coolver/home-assistant-mcp
