# claude-skills

Two Claude skills. Each one is a single `SKILL.md` file, so you can install it with one command. You do not need to clone this repo.

| Skill | What it does |
|---|---|
| `ste-write` | Write explanations, summaries, emails, docs and more in simplified technical English (ASD-STE100 style). Adds ASCII or SVG diagrams, and offers an interactive HTML page for large topics. |
| `visual-concrete-explain` | Explain a hard concept with a tiny hand-computable example plus diagrams. Written in Chinese. |

## Install (Claude Code)

Run one command per skill. It creates the skill folder and downloads the file into it.

**ste-write**

```sh
mkdir -p ~/.claude/skills/ste-write && curl -fsSL https://raw.githubusercontent.com/floydchenchen/claude-skills/main/skills/ste-write/SKILL.md -o ~/.claude/skills/ste-write/SKILL.md
```

**visual-concrete-explain**

```sh
mkdir -p ~/.claude/skills/visual-concrete-explain && curl -fsSL https://raw.githubusercontent.com/floydchenchen/claude-skills/main/skills/visual-concrete-explain/SKILL.md -o ~/.claude/skills/visual-concrete-explain/SKILL.md
```

**Both at once**

```sh
for s in ste-write visual-concrete-explain; do
  mkdir -p ~/.claude/skills/$s
  curl -fsSL https://raw.githubusercontent.com/floydchenchen/claude-skills/main/skills/$s/SKILL.md -o ~/.claude/skills/$s/SKILL.md
done
```

Then start a new Claude Code session. Claude Code loads personal skills from `~/.claude/skills/` when a session starts.

### Install for one project only

Run the same command inside the project, and replace `~/.claude/skills/` with `.claude/skills/`. Commit the folder if you want your team to get the skill too.

### Update or remove

- To update, run the install command again. It overwrites the old file.
- To remove, delete the folder: `rm -rf ~/.claude/skills/<skill-name>`.

## License

MIT. See [LICENSE](LICENSE).
