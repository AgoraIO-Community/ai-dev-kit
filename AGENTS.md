# Agent Conventions

This repo provides skills (slash commands) for AI-assisted development. The skills are plain markdown files — one skill (`ai-dev-kit`) with git and docs sub-skills.

## Repo Structure

| Path                          | Purpose                                          |
| ----------------------------- | ------------------------------------------------ |
| `skills/ai-dev-kit/`          | Skill entry point and sub-skills                 |
| `skills/ai-dev-kit/git/`      | Git workflow commands (ship, pr, sync)            |
| `skills/ai-dev-kit/docs/`     | Documentation generation commands                |
| `commands/`                    | Claude Code slash command files                  |
| `docs/`                        | Standards and guides                             |
| `.claude-plugin/`              | Claude Code plugin metadata                      |
| `.cursor-plugin/`              | Cursor plugin metadata                           |
| `.codex/`                      | Codex install instructions                       |

## Conventions

1. **Commit messages:** lowercase start, no AI tool names, present tense, no Co-Authored-By.
2. **PR titles:** lowercase start, under 70 characters.
3. **Slash commands are simple markdown.** A command is a prompt with `$ARGUMENTS` placeholder. No scripts, no execution logic.

## Skills

| Skill       | Entry Point                      | Commands                                                          |
| ----------- | -------------------------------- | ----------------------------------------------------------------- |
| ai-dev-kit  | `skills/ai-dev-kit/SKILL.md`     | `/git:ship`, `/git:pr`, `/git:sync`, `/docs:generate`, `/docs:update`, `/docs:test` |
