# agent-skills

Reusable skills for AI coding agents (Claude Code, Codex, Antigravity, Cursor, and other `SKILL.md`-compatible tools).

## Included skills

| Skill | Purpose |
|---|---|
| [kiss](skills/kiss/SKILL.md) | Keep code flat, readable top-to-bottom, with plain A1-A2 English names and zero over-engineering. |
| [proof](skills/proof/SKILL.md) | Require primary evidence (`file:line` quotes, fresh command outputs, screenshots, primary docs) for every claim. |
| [grill-design](skills/grill-design/SKILL.md) | Run a one-question-at-a-time UI design interview, build three interactive variants inside the real app, and verify them across breakpoints. |
| [how](skills/how/SKILL.md) | Explain how a subsystem works with plain language, a Mermaid flow diagram, and a step-by-step code walkthrough. |

## Installation

### Copy or symlink into your agent's skills directory

Clone the repository once:

```bash
git clone https://github.com/s3rezhkaa/agent-skills.git
```

Then copy or symlink the skills you want into your agent's global or project skills folder:

- **Claude Code:** `~/.claude/skills/` (or `.claude/skills/` in a repo)
- **Codex CLI:** `~/.codex/skills/` (or `.agents/skills/` in a repo)
- **Antigravity:** `~/.gemini/antigravity/skills/` (or `.agents/skills/` in a repo)
- **Cursor:** `.cursor/skills/` or `.agents/skills/`

Example (global symlinks for Codex / Claude Code):

```bash
ln -s /path/to/agent-skills/skills/kiss ~/.codex/skills/kiss
ln -s /path/to/agent-skills/skills/proof ~/.codex/skills/proof
ln -s /path/to/agent-skills/skills/grill-design ~/.codex/skills/grill-design
ln -s /path/to/agent-skills/skills/how ~/.codex/skills/how
```
