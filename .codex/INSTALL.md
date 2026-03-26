# Installing AI-Dev Kit for Codex

## Prerequisites

- Git

## Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/AgoraIO-Community/ai-dev-kit.git ~/.codex/ai-dev-kit
   ```

2. **Create the skills symlink:**
   ```bash
   mkdir -p ~/.agents/skills
   ln -s ~/.codex/ai-dev-kit/skills ~/.agents/skills/ai-dev-kit
   ```

3. **Restart Codex** to discover the skills.

## Updating

```bash
cd ~/.codex/ai-dev-kit && git pull
```

## Uninstalling

```bash
rm ~/.agents/skills/ai-dev-kit
rm -rf ~/.codex/ai-dev-kit
```
