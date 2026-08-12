# ascii skill package

A tiny cross-agent skill for finding a Unicode character from a natural-language description using Compart Unicode.

## Included layouts

- `.agents/skills/ascii/SKILL.md` — Agent Skills compatible
- `.github/skills/ascii/SKILL.md` — GitHub Copilot project skill
- `.claude/skills/ascii/SKILL.md` — Claude Code project skill
- `source/ascii/SKILL.md` — canonical copy for editing/reuse

All four copies are identical.

## Usage

```text
/ascii a L shape pointing down arrow
```

Expected response:

```text
↴  
```

The skill intentionally returns only one Unicode character plus two trailing ASCII spaces.

## Install

Copy the folder matching your agent into the root of your project.

For a generic Agent Skills client:

```text
.agents/skills/ascii/SKILL.md
```

For GitHub Copilot:

```text
.github/skills/ascii/SKILL.md
```

For Claude Code:

```text
.claude/skills/ascii/SKILL.md
```

## Source

Character lookup source: Compart Unicode (`https://www.compart.com/en/unicode/`).
