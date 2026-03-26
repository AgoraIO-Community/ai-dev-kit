# AI-Dev Kit

Git workflow conventions and documentation generation skills for AI-assisted development.

## Skills

### Git Workflow

Commit, push, and PR commands that enforce consistent conventions. See [git/SKILL.md](git/SKILL.md).

| Command      | What It Does                                                             |
| ------------ | ------------------------------------------------------------------------ |
| `/git:ship`  | Commit staged changes and push (enforces conventions)                    |
| `/git:pr`    | Create a PR from current branch to main with generated title and summary |
| `/git:sync`  | Pull latest from main, rebase current branch on top                      |

### Documentation

Generate, update, and test progressive disclosure documentation. See [docs/SKILL.md](docs/SKILL.md).

| Command        | What It Does                                                     |
| -------------- | ---------------------------------------------------------------- |
| `/docs:generate` | Generate L0/L1/L2 docs for the repo following the PD standard |
| `/docs:update` | Update existing docs after code changes — only what changed      |
| `/docs:test`   | Verify docs work — right context loaded at the right level       |

## Conventions

- **Commit messages:** lowercase start, present tense, no AI tool names, no Co-Authored-By
- **PR titles:** lowercase start, under 70 characters
- **Documentation:** follows the [Progressive Disclosure Documentation Standard](https://github.com/AgoraIO-Community/ai-dev-kit/blob/main/docs/progressive-disclosure-standard.md)
