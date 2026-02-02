# 7. OpenCode Installation and Usage

[← Back to Table of Contents](../../README.md)

---

OpenCode is an open-source AI coding tool that supports various AI models.

---

## Installation

### Windows

```
┌─────────────────────────────────────────────────────────────┐
│  ⚠️ Notice for Windows Users                                │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  OpenCode currently does not provide Windows native         │
│  binaries. Windows users should choose from below:          │
│                                                             │
│  ✅ Recommended: Use Claude Code (full Windows support)     │
│  🔧 Alternative: Install OpenCode via WSL (Linux env)       │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

**Method 1: Use Claude Code (Recommended)** ⭐

Windows users are **strongly recommended** to use **Claude Code**.
→ Go to [Claude Code Installation Guide](06-claude-code.md)

**Method 2: Install via WSL (Windows Subsystem for Linux)**

You can use OpenCode in a Linux environment through WSL.

1. **Install WSL** (PowerShell with admin rights):
```powershell
wsl --install
```

2. **Restart** your computer

3. Open **Ubuntu Terminal** (search "Ubuntu" in Start menu)

4. Follow the Mac installation method below in Ubuntu

> **Note**: If you're not familiar with WSL, using only Claude Code is sufficient!

---

### Mac

**Method 1: Using Homebrew** ⭐ Recommended

```bash
brew install opencode-ai/tap/opencode
```

**Method 2: Install via Go**

```bash
brew install go
go install github.com/opencode-ai/opencode@latest
```

---

## LiteLLM Integration Setup

Create a configuration file for OpenCode to work through LiteLLM.

### Mac / WSL (Linux)

1. Run the following command in Terminal:

```bash
nano ~/.opencode.json
```

2. Enter the following content (**modify API key and URL**):

```json
{
  "provider": "openai-compatible",
  "apiKey": "sk-enter-your-api-key-here",
  "baseUrl": "https://api.tokamak.network",
  "model": "claude-4-5-opus"
}
```

3. Save with `Ctrl + X` → `Y` → `Enter`

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
# Mac / WSL
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
