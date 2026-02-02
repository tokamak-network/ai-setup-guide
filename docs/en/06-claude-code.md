# 6. Claude Code Installation and Usage

[← Back to Table of Contents](../../README.md)

---

Claude Code is the official AI coding assistant made by Anthropic.

---

## Installation

### Windows

1. Open PowerShell (**new window!**)
2. Copy → Paste → Press Enter:

```powershell
npm install -g @anthropic-ai/claude-code
```

3. Wait for installation to complete (1-2 minutes)

4. **✅ Verify Installation**:

```powershell
claude --version
```

If a version number appears, **success!**

### Mac

1. Open Terminal
2. Copy → Paste → Press Enter:

```bash
npm install -g @anthropic-ai/claude-code
```

> **If permission error occurs**:
> ```bash
> sudo npm install -g @anthropic-ai/claude-code
> ```
> (Mac login password required)

3. **✅ Verify Installation**:

```bash
claude --version
```

---

## First Run

1. Navigate to your working folder in the terminal:

```bash
# Windows
cd $env:USERPROFILE\Documents

# Mac
cd ~/Documents
```

2. Run Claude Code:

```bash
claude
```

3. First run screen:

```
╭──────────────────────────────────────────────────────────╮
│                                                          │
│   Welcome to Claude Code!                                │
│                                                          │
│   Type your request and press Enter to start.            │
│                                                          │
╰──────────────────────────────────────────────────────────╯

>  █
   ↑
   Enter your request here
```

---

## Main Commands

| Command | Description | Example |
|---------|-------------|---------|
| `claude` | Start Claude Code | Type `claude` in terminal |
| `claude "question"` | Ask directly | `claude "python code to print hello world"` |
| `/help` | View help | Type `/help` while running |
| `/clear` | Clear conversation history | Type `/clear` while running |
| `Ctrl + C` | Stop execution | When you want to stop AI response |
| `exit` | Exit | Exit Claude Code |

---

## Usage Examples

**Simple question:**
```
> Create Python code to sum numbers from 1 to 10
```

**File creation request:**
```
> Create an index.html file that displays "Hello World"
```

**Project creation:**
```
> Create a simple To-Do app. I need add, delete, and complete check features
```

---

[← Previous: API Key Setup](05-api-key-setup.md) | [Next: OpenCode Installation →](07-opencode.md)
