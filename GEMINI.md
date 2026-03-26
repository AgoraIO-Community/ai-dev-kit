# AI-Dev Kit

Git workflow conventions and documentation generation skills for AI-assisted development.

## Skills

Read `skills/ai-dev-kit/SKILL.md` for the full skill reference.

| Command          | What It Does                                                   |
| ---------------- | -------------------------------------------------------------- |
| `/git:ship`      | Commit staged changes and push (enforces conventions)          |
| `/git:pr`        | Create a PR with generated title and summary                   |
| `/git:sync`      | Rebase current branch on latest main                           |
| `/docs:generate` | Generate L0/L1/L2 docs following the PD standard              |
| `/docs:update`   | Update existing docs after code changes                        |
| `/docs:test`     | Verify docs give right context at the right level              |

## Conventions

- **Commit messages:** lowercase start, present tense, no AI tool names, no Co-Authored-By
- **PR titles:** lowercase start, under 70 characters
- **Documentation:** follows the Progressive Disclosure Documentation Standard in `docs/progressive-disclosure-standard.md`
