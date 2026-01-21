# my-cc-tips-skill

Claude Code skill that references the Claude Code best practice repository (submodule) and provides curated guidance from real examples. This project also references and cites https://github.com/anthropics/skills.git.

## Installation

1. Ensure your Claude Code skills directory exists: `~/.claude/skills`.
2. Clone this repository into that directory with submodules:

```bash
git clone --recursive https://github.com/mjaemin/my-cc-tips-skill.git ~/.claude/skills/cc-tips
```

The project root must live under `~/.claude/skills` so Claude Code can detect the skill.

## Usage

Invoke the skill from Claude Code or OpenCode with the slash command:

```text
/cc-tips
```

## Contents

- Skill definition: `SKILL.md`
- Reference examples (submodule): `references/everything-claude-code/`

## License

MIT
