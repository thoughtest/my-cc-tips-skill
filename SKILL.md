---
name: cc-tips
description: Claude Code configuration and advanced usage guide. Provides practical examples for agents, skills, hooks, commands, rules, and MCP configurations. Use when users ask about "Claude Code setup", "create agent", "hook configuration", "MCP setup", "slash commands", "writing rules", "creating skills", "subagents", or "context window management".
---

# Claude Code Tips

Guide for advanced Claude Code configuration. Reference practical examples in `references/everything-claude-code/`.

## Reference Structure

| Directory | Purpose | File Pattern |
|-----------|---------|--------------|
| `agents/` | Subagent definitions | `references/everything-claude-code/agents/*.md` |
| `skills/` | Workflows & domain knowledge | `references/everything-claude-code/skills/**/*` |
| `commands/` | Slash commands | `references/everything-claude-code/commands/*.md` |
| `rules/` | Always-follow guidelines | `references/everything-claude-code/rules/*.md` |
| `hooks/` | Tool event automation | `references/everything-claude-code/hooks/` |
| `contexts/` | Dynamic system prompts | `references/everything-claude-code/contexts/*.md` |
| `mcp-configs/` | MCP server configs | `references/everything-claude-code/mcp-configs/` |
| `examples/` | Configuration examples | `references/everything-claude-code/examples/` |

## Workflow

1. Identify user question type
2. Read relevant files from the appropriate directory
3. Answer based on practical examples

## Reference Files by Topic

### Agents
- Triggers: "create subagent", "agent definition", "task delegation"
- Read: `references/everything-claude-code/agents/planner.md`, `code-reviewer.md`, `tdd-guide.md`
- Frontmatter fields: `name`, `description`, `tools`, `model`

### Hooks
- Triggers: "hook setup", "PreToolUse", "PostToolUse", "automation"
- Read: `references/everything-claude-code/hooks/hooks.json`
- Hook types: PreToolUse, PostToolUse, PreCompact, SessionStart, Stop

### Rules
- Triggers: "writing rules", "security rules", "coding style"
- Read: `references/everything-claude-code/rules/security.md`, `testing.md`, `git-workflow.md`

### Commands
- Triggers: "slash command", "/tdd", "/plan", "/code-review"
- Read: `references/everything-claude-code/commands/*.md`

### Skills
- Triggers: "create skill", "workflow definition"
- Read: `references/everything-claude-code/skills/tdd-workflow/SKILL.md`, `security-review/SKILL.md`

### MCP
- Triggers: "MCP setup", "external service integration"
- Read: `references/everything-claude-code/mcp-configs/mcp-servers.json`

### Examples
- Triggers: "CLAUDE.md example", "project configuration"
- Read: `references/everything-claude-code/examples/CLAUDE.md`, `user-CLAUDE.md`

## Key Concepts

### Agents
Subagents handle delegated tasks with limited scope. Define in frontmatter: `name`, `description`, `tools`, `model`.

```yaml
---
name: code-reviewer
description: Reviews code for quality, security, and maintainability
tools: Read, Grep, Glob, Bash
model: opus
---
```

### Hooks
Automation triggered by tool events. Use `matcher` for conditions, `command` for script execution.

```json
{
  "matcher": "tool == \"Edit\" && tool_input.file_path matches \"\\.(ts|tsx)$\"",
  "hooks": [{ "type": "command", "command": "..." }]
}
```

### Rules
Always-follow guidelines. Separate by module: security, testing, coding style.

### Commands
Quick execution via slash commands: `/tdd`, `/plan`, `/code-review`.

### Skills
Workflows and domain knowledge. Define frontmatter and procedures in SKILL.md.

## Context Window Management

- Never enable all MCPs simultaneously (200k can shrink to 70k)
- Keep under 10 MCPs and 80 tools per project
- Use `disabledMcpServers` to disable unused MCPs
