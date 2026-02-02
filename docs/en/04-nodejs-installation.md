# 4. Node.js Installation

[← Back to Table of Contents](../../README.md)

---

Node.js is a JavaScript runtime environment. **It is required for installing Claude Code and OpenCode.**

---

## Windows

1. Go to **https://nodejs.org** in your web browser
2. Click the **LTS** (Long Term Support) button - **the green button on the left**

```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│    [ 20.x.x LTS ]      [ 21.x.x Current ]                   │
│    Recommended for        Latest Features                   │
│    Most Users                                               │
│         ↑                                                   │
│    Click this button!                                       │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

3. Double-click the downloaded `node-v*-x64.msi` file
4. Click **Next**
5. Check "I accept the terms" → **Next**
6. Confirm installation path → **Next**
7. **Next** (keep default settings)
8. Click **Install**
9. Installation complete → **Finish**

### ✅ Verify Installation

1. Open a **new PowerShell window** (must be a new window, not an existing one!)
2. Copy → Paste → Press Enter:

```powershell
node --version
```

3. If you see a version number like `v20.x.x`, **success!**

```
PS C:\Users\Username> node --version
v20.11.0   ← If you see something like this, success!
```

4. Also verify npm:

```powershell
npm --version
```

---

## Mac

### Method 1: Official Installer (Easy) ⭐ Recommended

1. Go to **https://nodejs.org** in your web browser
2. Click the **LTS** button
3. Double-click the downloaded `.pkg` file
4. Click **Continue** → **Agree** → **Install**
5. Enter your password → Installation complete

### Method 2: Using Homebrew

```bash
# Install Homebrew (if not installed)
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Install Node.js
brew install node
```

### ✅ Verify Installation

```bash
node --version
npm --version
```

If version numbers appear, you're successful!

---

[← Previous: IDE Installation](03-ide-installation.md) | [Next: API Key Setup →](05-api-key-setup.md)
