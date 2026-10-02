# claude-skills

Two Claude skills. Each skill is a folder under `skills/` with a `SKILL.md`.

| Skill | What it does |
|---|---|
| `ste-write` | Write explanations, summaries, emails, docs and more in simplified technical English (ASD-STE100 style), with ASCII or SVG diagrams and an optional interactive HTML page. |
| `visual-concrete-explain` | Explain a hard concept with a tiny hand-computable example plus diagrams (Chinese-language skill). |

## Install

Claude Code (personal skills):

```
cp -r skills/<skill-name> ~/.claude/skills/
```

Restart the session so Claude Code loads the new skill.
