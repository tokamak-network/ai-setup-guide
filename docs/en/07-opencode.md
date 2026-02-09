# 7. OpenCode Installation and Usage

[← Back to Table of Contents](../../README.md)

---

OpenCode is an open-source AI coding tool that supports various AI models.
This guide covers the **Tokamak custom build** which supports automatic context compaction, custom providers, and more.

---

## Installation

### Platform Binaries

Download the binary for your platform from the [OpenCode GitHub Releases](https://github.com/anomalyco/opencode/releases/latest).

| Platform | Download |
|----------|----------|
| Mac M1/M2/M3/M4 | [opencode-darwin-arm64.zip](https://github.com/anomalyco/opencode/releases/latest/download/opencode-darwin-arm64.zip) |
| Mac Intel | [opencode-darwin-x64.zip](https://github.com/anomalyco/opencode/releases/latest/download/opencode-darwin-x64.zip) |
| Linux x64 | [opencode-linux-x64.tar.gz](https://github.com/anomalyco/opencode/releases/latest/download/opencode-linux-x64.tar.gz) |
| Windows x64 | [opencode-windows-x64.zip](https://github.com/anomalyco/opencode/releases/latest/download/opencode-windows-x64.zip) |

### Mac

**Step 1: Install Binary**

```bash
# Create installation directory
mkdir -p ~/.opencode/bin

# Extract downloaded zip (Mac Apple Silicon example)
unzip ~/Downloads/opencode-darwin-arm64.zip -d ~/.opencode/bin/

# Grant execute permission
chmod +x ~/.opencode/bin/opencode
```

**Step 2: Add to PATH**

```bash
echo 'export PATH="$HOME/.opencode/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```

### Windows

```
┌─────────────────────────────────────────────────────────────┐
│  Notice for Windows Users                                    │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  Windows users should choose from below:                     │
│                                                             │
│  Method 1: Use Claude Code (Recommended)                     │
│  Method 2: Install OpenCode via WSL (Linux env)              │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

**Method 1: Use Claude Code (Recommended)**

Windows users are **strongly recommended** to use **Claude Code**.
→ Go to [Claude Code Installation Guide](06-claude-code.md)

**Method 2: Install via WSL**

1. **Install WSL** (PowerShell with admin rights):
```powershell
wsl --install
```

2. **Restart** your computer

3. Open **Ubuntu Terminal** (search "Ubuntu" in Start menu)

4. Download the `opencode-linux-x64` binary and follow the Mac installation steps above
   (use `~/.bashrc` instead of `~/.zshrc`)

---

## Configuration

### Create Configuration File

```bash
mkdir -p ~/.config/opencode
nano ~/.config/opencode/opencode.json
```

Enter the following content (**modify API key**):

```json
{
  "$schema": "https://opencode.ai/config.json",
  "model": "tokamak/gpt-5.2-pro",
  "permission": {
    "external_directory": "allow"
  },
  "compaction": {
    "auto": true,
    "prune": true
  },
  "provider": {
    "tokamak": {
      "npm": "@ai-sdk/openai-compatible",
      "name": "Tokamak AI",
      "options": {
        "baseURL": "https://api.ai.tokamak.network",
        "apiKey": "sk-enter-your-api-key-here"
      },
      "models": {
        "gpt-5.2-pro": {
          "name": "GPT 5.2 Pro",
          "limit": {
            "context": 131072,
            "input": 131072,
            "output": 16384
          }
        }
      }
    }
  }
}
```

Save with `Ctrl + X` → `Y` → `Enter`

### Key Configuration Options

| Setting | Description |
|---------|-------------|
| `model` | Default model to use (`provider/model` format) |
| `compaction.auto` | Automatically compresses conversation when nearing token limit |
| `compaction.prune` | Cleans up unnecessary earlier messages |
| `limit.input` | Must be set for proper token calculation |
| `permission.external_directory` | Allows reading files outside the project directory |

---

## Verify Installation

```bash
opencode --version
```

If a version number appears, **success!**

---

## First Run and Usage

1. Navigate to your working folder in Terminal:

```bash
cd ~/Documents
```

2. Run OpenCode:

```bash
opencode
```

---

## Main Commands

| Command | Description |
|---------|-------------|
| `opencode` | Start OpenCode |
| `opencode --help` | View help |
| `opencode --version` | Check version |
| `/help` | Help while running |
| `/clear` | Clear conversation |
| `/compact` | Manually compress conversation |
| `Ctrl + C` | Stop execution |
| `/quit` or `exit` | Exit |

---

## Usage Examples

```
> Show me the list of files in the current folder

> Read the contents of index.html

> Create a simple button component with React
```

---

[← Previous: Claude Code Installation](06-claude-code.md) | [Next: Skills & Agents →](08-skills-agents.md)
