# git-agent

**git-agent** is a natural-language Git assistant built with [LangChain](https://github.com/langchain-ai/langchain) and OpenAI function calling. Instead of remembering Git commands, you just describe what you want to do — and the agent does it.

## What it does

Run `git-agent` from inside any local repository and pass a plain-English instruction as an argument. The agent reads the current repository state via `git status`, reasons about your intent, and executes the appropriate Git operation using one of its four tools:

| Tool | What it does |
|---|---|
| `git_status` | Inspects the working tree — automatically called for context before every instruction |
| `git_diff` | Shows colourised diffs between the working directory and the last commit, scoped to specific files if requested |
| `git_add` | Stages files for the next commit |
| `git_restore` | Restores specified files to their last-committed state (discards local changes) |

## Example usage

```shell
# Install
pip install git+https://github.com/jupyterjazz/git-agent.git

# Set your OpenAI key
export OPENAI_API_KEY=<your-key>

# Ask it something (run from inside a repo)
git-agent "show me what changed in the authentication module"
git-agent "stage only the files related to the login feature"
git-agent "restore the config file to its last committed version"
```

The agent maps your intent to the right Git command and executes it — colourising diff output (cyan for headers, red for deletions, green for additions) so it's easy to read at a glance.

## Model

Uses `gpt-3.5-turbo-0613` via OpenAI function calling (structured tool dispatch — no free-form shell execution).

## Compliance note

`git_restore` is a destructive, irreversible operation. The agent only restores files you explicitly ask about; it will not restore additional files unless you ask for all of them.
