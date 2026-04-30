# CLAUDE.md

Guidance for Claude Code when working in this repository.

## Project Overview

Local Claude Code plugin (dotfiles): code-focused agents, skills, commands, hooks, and rules. Not published to npm.

## Layout

- `agents/` — 37 specialized subagents (planner, code-reviewer, tdd-guide, language-specific reviewers and build-resolvers)
- `skills/` — 91 skills covering language patterns, testing, security, frontend/backend, API design, git, docker, postgres, MCP, etc.
- `commands/` — 40 slash commands (`/tdd`, `/plan`, `/e2e`, `/code-review`, `/build-fix`, `/feature-dev`, language-specific `*-build`/`*-review`/`*-test`, `/prp-*`, `/hookify-*`)
- `hooks/hooks.json` — plugin hook configuration
- `rules/` — language rules (cpp/csharp/dart/golang/java/kotlin/perl/php/python/rust/swift/typescript/web/zh + common)
- `mcp-configs/mcp-servers.json` — MCP server registry
- `scripts/hooks/` — hook scripts wired up in `hooks/hooks.json`
- `scripts/lib/` — shared helpers used by hooks
- `examples/` — CLAUDE.md templates for common project types (django/go/laravel/rust/nextjs/etc.)

## Core Principles

1. Agent-First — delegate domain work to specialized agents
2. Test-Driven — tests before implementation, 80%+ coverage
3. Security-First — validate input, protect secrets, safe defaults
4. Plan Before Execute — break complex changes into deliberate phases

## Conventions

- Agents: Markdown with YAML frontmatter (`name`, `description`, `tools`, `model`)
- Skills: SKILL.md with `name`, `description`, plus content sections
- Commands: Markdown with `description:` frontmatter
- Hooks: JSON in `hooks/hooks.json`, scripts in `scripts/hooks/*.js`
- File naming: lowercase with hyphens (e.g. `python-reviewer.md`)
