# cc — Claude Code plugin

Local Claude Code plugin (`name: cc`): code-focused agents, skills, commands, hooks, and rules. Lives in the directory `everything-claude-code/`.

## Contents

| Directory | What's in it | Count |
|---|---|---|
| `agents/` | Specialized subagents (reviewers, build-resolvers, planner, tdd-guide, security-reviewer, etc.) | 37 |
| `skills/` | Language patterns, testing, security, frontend/backend, API design, git, docker, postgres, MCP | 91 |
| `commands/` | Slash commands (`/tdd`, `/plan`, `/e2e`, `/code-review`, language-specific `*-build`/`*-review`/`*-test`, `/prp-*`, `/hookify-*`) | 40 |
| `hooks/hooks.json` | Hook config for PreToolUse / PostToolUse / Stop / SessionStart / PreCompact | — |
| `rules/` | Language rules (cpp/csharp/dart/golang/java/kotlin/perl/php/python/rust/swift/typescript/web + common/zh) | 16 |
| `mcp-configs/` | MCP server registry | — |
| `scripts/hooks/` | Hook scripts wired up by `hooks/hooks.json` | 30 |
| `examples/` | CLAUDE.md templates for common project types | 7 |

## Use

### Option A — `--plugin-dir` (simplest)

Launch Claude Code with this directory loaded as a plugin:

```bash
claude --plugin-dir /Users/iteaker/workspace/skills/everything-claude-code
```

Or set an alias:

```bash
alias ccp='claude --plugin-dir /Users/iteaker/workspace/skills/everything-claude-code'
```

Reload after editing files: `/reload-plugins` inside Claude Code.

### Option B — install from local marketplace

Inside Claude Code:

```
/plugin marketplace add /Users/iteaker/workspace/skills/everything-claude-code
/plugin install cc@cc
```

Update after editing files: `/plugin marketplace update cc`.

### Skill names

When loaded as a plugin, skills are namespaced under `cc`: `/cc:tdd-workflow`, `/cc:security-review`, etc. Run `/help` after loading to see the full list.

## Layout

```
.claude-plugin/
├── plugin.json          # plugin manifest
└── marketplace.json     # local marketplace catalog (Option B)
agents/                  # subagents
skills/                  # SKILL.md collections
commands/                # slash commands
hooks/hooks.json         # hook configuration
rules/                   # language rules
scripts/hooks/           # hook scripts (referenced by hooks.json via ${CLAUDE_PLUGIN_ROOT})
scripts/lib/             # hook helpers
mcp-configs/             # MCP server config
examples/                # CLAUDE.md templates
```

## Local development

```bash
npm install   # eslint + prettier + markdownlint dev tooling only
npm run lint
```

## License

MIT
