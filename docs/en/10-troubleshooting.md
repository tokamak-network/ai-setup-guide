# 10. Troubleshooting

[← Back to Table of Contents](../../README.md)

---

## Node.js Installation Verification Failed

**Symptom**: "Command not found" error when running `node --version`

```
PS C:\Users\Username> node --version
node : The term 'node' is not recognized as the name of a cmdlet...
```

**Solution**:
1. **Completely close** the current terminal window (X button)
2. Open a **new terminal window**
3. Try `node --version` again

If it still doesn't work → **Reinstall** Node.js

---

## npm Permission Error (Mac)

**Symptom**: "EACCES" error when running `npm install -g`

```
npm ERR! Error: EACCES: permission denied
```

**Solution**:
```bash
sudo npm install -g @anthropic-ai/claude-code
```
Enter Mac login password → Press Enter

---

## Claude Code Won't Run

**Symptom**: "Command not found" when typing `claude`

**Solution Steps**:

1. Check Node.js installation:
```bash
node --version
```
If version doesn't appear → Reinstall Node.js first

2. Check Claude Code installation:
```bash
npm list -g @anthropic-ai/claude-code
```
If installed, version info will appear

3. Check npm global path:
```bash
npm config get prefix
```

4. Check if that path is in the system PATH
   - If not in PATH, add to environment variables

---

## API Connection Error

**Symptom**: Errors like "API key invalid", "Connection refused"

**Solution**:

1. Check environment variables:

```powershell
# Windows
echo $env:ANTHROPIC_API_KEY
echo $env:ANTHROPIC_BASE_URL
```

```bash
# Mac
echo $ANTHROPIC_API_KEY
echo $ANTHROPIC_BASE_URL
```

2. If values are empty → Redo [Chapter 5 API Key Setup](05-api-key-setup.md)

3. If values exist but still not working:
   - Check with Kevin if API key is correct
   - Verify server address is correct
   - Check if connected to company network (VPN)

---

## Claude Code 401/404 Error (Model Name Mismatch) ⚠️ Important

**Symptom**: 401 (Unauthorized) or 404 (Not Found) error while using Claude Code

```
Error: 401 Key model access denied
```

**Root Cause Analysis**:

Claude Code performs **Task Splitting** internally for complex tasks. During this, it automatically uses the cost-effective Haiku model for background tasks (file indexing, planning, syntax checking, etc.).

The problem is that the model name Claude Code requests is a **specific version name** (e.g., `claude-haiku-4-5-20251001`), but the proxy server only allows **aliases** (e.g., `claude-haiku-4.5`), causing a mismatch.

```
┌─────────────────────────────────────────────────────────────┐
│  🔍 Error Structure                                         │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  Claude Code requests: claude-haiku-4-5-20251001            │
│           ↓                                                 │
│  Proxy server allows: claude-haiku-4.5 (alias only)         │
│           ↓                                                 │
│  Result: 401 Key model access denied error!                 │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

**Solution**:

Set additional environment variables to force Claude Code to use alias model names.

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

**Verify Setup**:

```bash
# Mac
echo $ANTHROPIC_DEFAULT_HAIKU_MODEL
# Output: claude-haiku-4.5 means success!
```

```powershell
# Windows
echo $env:ANTHROPIC_DEFAULT_HAIKU_MODEL
# Output: claude-haiku-4.5 means success!
```

**Environment Variable Explanation**:

| Environment Variable | Purpose |
|---------------------|---------|
| `ANTHROPIC_DEFAULT_OPUS_MODEL` | Opus model alias for main tasks |
| `ANTHROPIC_DEFAULT_HAIKU_MODEL` | Haiku model alias for background tasks |
| `CLAUDE_CODE_SUBAGENT_MODEL` | Model alias for sub-agents |

> **Note**: This issue doesn't occur with OpenCode. It's a problem specific to Claude Code's Task Splitting feature.

---

## Environment Variables Not Applied

**Symptom**: Set environment variables are not recognized

**Solution**:
- **Windows**: **Close all PowerShell windows and open a new one**
- **Mac**: Run `source ~/.zshrc` or **restart terminal**

---

## "Permission denied" Error

**Symptom**: File/folder access permission error

**Solution (Mac)**:
```bash
sudo command
```
Example: `sudo npm install -g @anthropic-ai/claude-code`

**Solution (Windows)**:
1. Run PowerShell with **administrator privileges**
2. Search "PowerShell" in Start menu → Right-click → **Run as administrator**

---

[← Previous: First Project](09-first-project.md) | [Next: FAQ →](11-faq.md)
