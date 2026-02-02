# 6. Claude Code Installation and Usage

[← Back to Table of Contents](../../README.md)

---

Claude Code is the official AI coding assistant made by Anthropic.

---

## ⚠️ Prerequisites: LiteLLM API Setup

You **must** complete the API key setup before running Claude Code.

> 📌 **Complete the environment variable setup in [Chapter 5: API Key Setup](05-api-key-setup.md) first!**

### Quick Checklist

Verify your setup is complete with these commands:

**Mac:**
```bash
echo $ANTHROPIC_API_KEY && echo $ANTHROPIC_BASE_URL
```

**Windows:**
```powershell
echo $env:ANTHROPIC_API_KEY; echo $env:ANTHROPIC_BASE_URL
```

If values are displayed, setup is complete! → Proceed to **Installation** below

If values are empty → Go to [Chapter 5: API Key Setup](05-api-key-setup.md)

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

2. Run Claude Code (specify model):

```bash
# Enter the model name you selected when getting your Virtual Key
claude --model claude-opus-4.5
```

> **Available Models:**
> - `claude-opus-4.5` - Highest performance, best for complex tasks
> - `claude-sonnet-4.5` - Balanced performance and speed
> - `claude-haiku-4.5` - Fast response, best for simple tasks

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
| `claude --model model_name` | Start with specific model | `claude --model claude-opus-4.5` |
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
