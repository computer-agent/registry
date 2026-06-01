# Claude Code Subagents Collection

A comprehensive collection of **138+ production-ready, domain-expert AI subagents** for Claude Code, authored by [0xfurai](https://github.com/0xfurai).

## What it does

Each subagent in this collection is a deep specialist in one technology area. Together they turn Claude Code into a full engineering team — the right expert is automatically delegated to based on context, or you can summon any agent by name.

**Coverage includes:**

- **Programming Languages** — Python, TypeScript, Go, Rust, Java, Ruby, Elixir, Swift, Dart, C/C++, Haskell, Scala, Kotlin, PHP, Clojure, Erlang, OCaml, Perl
- **Web Frameworks** — React, Vue, Angular, Next.js, Svelte, FastAPI, Django, Rails, Laravel, NestJS, Express, Gin, Phoenix, Actix, Remix, Spring Boot, Astro
- **Mobile & Desktop** — React Native, Flutter, iOS (UIKit/SwiftUI), Android (Jetpack Compose), Electron, Tauri, Expo
- **Databases** — PostgreSQL, MySQL, SQLite, MongoDB, Redis, Cassandra, DynamoDB, Elasticsearch, CockroachDB, Neo4j
- **DevOps & Cloud** — Docker, Kubernetes, Terraform, Ansible, GitHub Actions, CircleCI, AWS, GCP, Azure, Helm, Prometheus
- **Testing** — Jest, Pytest, Bats, Cypress, Playwright, AVA, RSpec, JUnit
- **Security** — vulnerability detection, secure coding practices, auth flows, penetration testing patterns

## How to use

Drop the `agents/` directory into `.claude/agents/` in any project. Claude Code will auto-delegate to the matching expert based on file type and context, or you can invoke a specific agent by name.

```bash
# Install all agents into your current project
cp -r agents/ .claude/agents/
```

Each agent file is a self-contained Markdown+YAML file — no runtime dependencies, no infrastructure required.

## Agent philosophy

Every expert in the collection follows the same principles:
1. **Deep focus** — knows its domain completely, defers outside it
2. **Production quality** — error handling, observability, testability baked in
3. **Idiomatic** — follows the official style guide of the language/framework
4. **Explicit quality checklists** — defines "done" precisely
