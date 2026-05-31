# AISH — AI Shell

**AISH** (AI Shell) is a Rust-built command-line assistant that lets you describe what you want in plain English and executes the necessary shell commands and file operations to get it done — safely and interactively.

## What it does

- **Natural language → shell commands**: Describe a task; AISH figures out the commands.
- **Workspace-aware**: Automatically detects your project's languages, frameworks, CI/CD setup, cloud tools, databases, and more — so suggestions are always contextual.
- **Security-first**: Every operation requires explicit approval before execution (unless you opt into `--accept-all` with a whitelist). Path validation, extension blocking, and granular permission controls are built in.
- **Interactive mode**: Keep a running conversation (`-i` flag) so you can chain tasks naturally.

## Supported LLM Providers

- **OpenAI** (GPT-4, GPT-3.5-turbo, etc.)
- **OpenRouter** (access to many models)
- **Custom** — any OpenAI-compatible API endpoint

## Key capabilities

| Skill | Description |
|-------|-------------|
| `execute_shell` | Runs shell commands and captures output |
| `fs_readfile` | Reads file contents |
| `fs_writefile` | Writes or creates files |
| `fs_makedir` | Creates directories |
| `fs_listdir` | Lists directory contents |

## Example usage

```bash
# One-shot task
aish "show me disk usage and the 5 largest directories"

# File operations
aish "rename all .txt files to .md in the current directory"

# Interactive session
aish -i "let's clean up this Python project"

# Auto-approve safe commands (use carefully)
aish --accept-all "run tests and commit if they pass"
```

## Installation

```bash
git clone https://github.com/sammwyy/aish.git
cd aish
cargo build --release
./target/release/aish init   # walks you through setup
```

## Repository

[github.com/sammwyy/aish](https://github.com/sammwyy/aish) — MIT licensed, built with Rust.
