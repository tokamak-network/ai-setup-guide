# 5. API Key Setup (LiteLLM)

[← Back to Table of Contents](../../README.md)

---

LiteLLM is a proxy service that allows you to use multiple AI models (Claude, GPT, etc.) through a single unified API.

---

## Step 1: Get Your API Key from LiteLLM

### 1-1. Access LiteLLM Dashboard

Open your web browser and go to:

```
https://api.ai.tokamak.network/
```

> **Note**: If you don't have an account, contact Kevin to request account creation.

### 1-2. Create Virtual Key

1. Click **Virtual Keys** in the left menu.

2. Click the **+ Create New Key** button.

![LiteLLM Virtual Keys Screen](../../images/capture%201.png)

### 1-3. Enter Key Information

**Key Ownership** section:
- **Owned By**: Select `You` (default)
- **Team**: Select your team if applicable, otherwise leave empty

**Key Details** section:
1. **Key Name** (required): Enter a key name
   - Example: `my-claude-key`, `research-team-key`
   - Use a name that's easy to identify later

2. **Models** (required): Select models to use
   - `claude-opus-4.5` - Highest performance, complex tasks
   - `claude-sonnet-4.5` - Balanced performance
   - `claude-haiku-4.5` - Fast response, simple tasks

   > **Tip**: You can select multiple models. We recommend selecting all three models.

3. **Key Type**: `Default` (keep default)

![Key Creation Screen](../../images/capture%202.png)

### 1-4. Complete Key Creation

1. Click the **Create Key** button.

2. The generated API key will be displayed:
   ```
   sk-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
   ```

3. ⚠️ **Important**: This key is shown **only once**!
   - Make sure to copy it to a safe place
   - Save temporarily in notepad, delete after setup is complete

### Server Information

| Item | Value |
|------|-------|
| **API Key** | `sk-xxxxx...` (the key you just created) |
| **Server Address** | `https://api.ai.tokamak.network/` |

---

## Step 2: API Key Security Guidelines ⚠️

```
┌─────────────────────────────────────────────────────────────┐
│  🔐 API Key Security Rules (Please follow these!)           │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  ❌ DON'T:                                                   │
│     • Share your API key with others                        │
│     • Write your API key directly in code files             │
│     • Upload to public repositories like GitHub             │
│     • Send via messengers like Slack or KakaoTalk           │
│     • Make sure API key is not visible in screenshots       │
│                                                             │
│  ✅ DO:                                                      │
│     • Only set via environment variables (see below)        │
│     • Contact IT team immediately if leak is suspected      │
│     • Delete temporary notes after setup is complete        │
│                                                             │
│  ⚠️  If your API key is leaked?                              │
│     → Contact IT team immediately to revoke and reissue!    │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

## Step 3: Set Environment Variables

Store the API key securely on your computer. **Methods differ by operating system.**

### Windows

**Method 1: Set via GUI (Easy)** ⭐ Recommended

1. Press `Windows key` and search for **"environment variables"**
2. Click **Edit the system environment variables**
3. Click the **Environment Variables** button in the opened window
4. Click **New** in the **"User variables"** section

5. Enter the first variable:
   ```
   Variable name: ANTHROPIC_API_KEY
   Variable value: (paste the API key from IT team)
   ```
   → Click **OK**

6. Click **New** again, enter the second variable:
   ```
   Variable name: ANTHROPIC_BASE_URL
   Variable value: (paste the server address from IT team)
   ```
   → Click **OK**

7. Click **OK** on all windows to close

8. **⚠️ Important**: **Close all PowerShell windows and open a new one**

**Method 2: Set via PowerShell Commands**

Open PowerShell and run the following commands (**modify the API key and URL**):

```powershell
[System.Environment]::SetEnvironmentVariable('ANTHROPIC_API_KEY', 'sk-enter-your-api-key-here', 'User')
[System.Environment]::SetEnvironmentVariable('ANTHROPIC_BASE_URL', 'https://api.ai.tokamak.network/', 'User')
```

**✅ Verify Setup** (in a new PowerShell window):

```powershell
echo $env:ANTHROPIC_API_KEY
```

If the API key value is displayed, **success!**

---

### Mac

**Permanent Setup Method** (persists after closing terminal)

1. Open Terminal

2. Run the following commands **one line at a time** (**modify the API key and URL**):

```bash
echo 'export ANTHROPIC_API_KEY="sk-enter-your-api-key-here"' >> ~/.zshrc
echo 'export ANTHROPIC_BASE_URL="https://api.ai.tokamak.network/"' >> ~/.zshrc
```

3. Apply settings:

```bash
source ~/.zshrc
```

4. **✅ Verify Setup**:

```bash
echo $ANTHROPIC_API_KEY
```

If the API key value is displayed, **success!**

> **Note**: The `~/.zshrc` file is a configuration file that is automatically read every time the terminal starts.

---

## Step 4: Model Alias Setup (Required) ⚠️

For Claude Code to communicate properly with the proxy server, you need to set **additional model alias environment variables**.

> **Why is this needed?**
> Claude Code internally uses specific model version names for background tasks.
> However, the proxy server only allows aliases, so 401 errors occur if they don't match.

### Windows (PowerShell)

```powershell
[System.Environment]::SetEnvironmentVariable('ANTHROPIC_DEFAULT_OPUS_MODEL', 'claude-opus-4.5', 'User')
[System.Environment]::SetEnvironmentVariable('ANTHROPIC_DEFAULT_HAIKU_MODEL', 'claude-haiku-4.5', 'User')
[System.Environment]::SetEnvironmentVariable('CLAUDE_CODE_SUBAGENT_MODEL', 'claude-opus-4.5', 'User')
```

**Close PowerShell window and open a new one** after setup

### Mac (Terminal)

```bash
echo 'export ANTHROPIC_DEFAULT_OPUS_MODEL="claude-opus-4.5"' >> ~/.zshrc
echo 'export ANTHROPIC_DEFAULT_HAIKU_MODEL="claude-haiku-4.5"' >> ~/.zshrc
echo 'export CLAUDE_CODE_SUBAGENT_MODEL="claude-opus-4.5"' >> ~/.zshrc
source ~/.zshrc
```

### Environment Variables Summary

| Environment Variable | Value | Purpose |
|---------------------|-------|---------|
| `ANTHROPIC_API_KEY` | `sk-xxxxx` (your issued key) | API authentication |
| `ANTHROPIC_BASE_URL` | `https://api.ai.tokamak.network/` | Proxy server address |
| `ANTHROPIC_DEFAULT_OPUS_MODEL` | `claude-opus-4.5` | Model for main tasks |
| `ANTHROPIC_DEFAULT_HAIKU_MODEL` | `claude-haiku-4.5` | Model for background tasks |
| `CLAUDE_CODE_SUBAGENT_MODEL` | `claude-opus-4.5` | Model for sub-agents |

### ✅ Verify All Settings

```bash
# Mac
echo $ANTHROPIC_API_KEY
echo $ANTHROPIC_BASE_URL
echo $ANTHROPIC_DEFAULT_HAIKU_MODEL
```

```powershell
# Windows
echo $env:ANTHROPIC_API_KEY
echo $env:ANTHROPIC_BASE_URL
echo $env:ANTHROPIC_DEFAULT_HAIKU_MODEL
```

If all values are displayed correctly, setup is complete!

---

[← Previous: Node.js Installation](04-nodejs-installation.md) | [Next: Claude Code Installation →](06-claude-code.md)
