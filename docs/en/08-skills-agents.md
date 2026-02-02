# 8. Skills & Agents Guide

[← Back to Table of Contents](../../README.md)

---

Skills and Agents are tools that extend the functionality of Claude Code.

---

## What are Skills?

Skills are additional features that help Claude Code **perform specific tasks better**.

```
┌─────────────────────────────────────────────────────────────┐
│  💡 How Skills Work                                         │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  Skills are built into Claude Code by default.              │
│  No separate installation required!                         │
│                                                             │
│  How they work:                                             │
│  • Auto-activation: Automatically applied based on request  │
│  • Manual activation: Call directly with /command           │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

## Frequently Used Skills

### Auto-Activated Skills (Applied automatically when requested)

| Skill | Purpose | Auto-activation Condition |
|-------|---------|--------------------------|
| `frontend-design` | Web UI/UX design | When requesting "webpage", "landing page", "UI", etc. |
| `web-artifacts-builder` | React web app creation | When requesting "React app", "web app", etc. |
| `security-review` | Security review | When writing auth, login, API code |

**Examples:**
```
> Create a company introduction webpage
  → frontend-design auto-applied!

> Create a dashboard with React
  → web-artifacts-builder auto-applied!
```

---

### Manually Activated Skills (Called with commands)

| Skill | Purpose | How to Call |
|-------|---------|-------------|
| `tdd-workflow` | Test-driven development | `/tdd feature description` |
| `doc-coauthoring` | Document co-authoring | When requesting document writing |

**Example:**
```
> /tdd create a login feature
  → Test code written first, then implementation
```

---

### Document-Related Skills

| Skill | Purpose | Supported Formats |
|-------|---------|-------------------|
| `pdf` | PDF creation/editing | `.pdf` |
| `docx` | Word documents | `.docx` |
| `pptx` | Presentations | `.pptx` |
| `xlsx` | Spreadsheets | `.xlsx`, `.csv` |

**Example:**
```
> Save this data as an Excel file
  → xlsx skill activated
```

---

## What are Agents?

Agents are **AI specialists that perform specialized roles**.

```
┌─────────────────────────────────────────────────────────────┐
│  💡 How Agents Work                                         │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  Agents are also built into Claude Code by default.         │
│  No separate installation required!                         │
│                                                             │
│  Claude Code automatically selects the appropriate Agent    │
│  to perform tasks as needed.                                │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

## Main Agents

| Agent | Role | When is it used? |
|-------|------|------------------|
| `planner` | Implementation planning | When requesting complex features |
| `frontend-engineer` | UI/UX development | When developing web components |
| `code-reviewer` | Code review | When reviewing code quality |
| `security-reviewer` | Security review | When writing security-related code |
| `document-writer` | Document writing | When writing README, guides |

---

## Custom Skills Folder (Advanced)

If you want to add your own Skills, add files to the following folder:

| OS | Path |
|----|------|
| Windows | `C:\Users\Username\.claude\skills\` |
| Mac | `~/.claude/skills/` |

**Folder creation commands:**

```powershell
# Windows (PowerShell)
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.claude\skills"
```

```bash
# Mac (Terminal)
mkdir -p ~/.claude/skills
```

> **Note**: Custom Skills setup is for advanced users. Using the built-in Skills is sufficient for beginners!

---

[← Previous: OpenCode Installation](07-opencode.md) | [Next: First Project →](09-first-project.md)
