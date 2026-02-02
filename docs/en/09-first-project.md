# 9. Starting Your First Project

[← Back to Table of Contents](../../README.md)

---

Now all setup is complete! Let's create your first project.

---

## Step 1: Create a Project Folder

### Windows (PowerShell)

```powershell
# Navigate to Documents folder
cd $env:USERPROFILE\Documents

# Create new project folder
mkdir my-first-project

# Move to the folder
cd my-first-project
```

### Mac (Terminal)

```bash
# Navigate to Documents folder
cd ~/Documents

# Create new project folder
mkdir my-first-project

# Move to the folder
cd my-first-project
```

---

## Step 2: Run Claude Code

```bash
claude
```

---

## Step 3: Make a Request to AI

```
> Create a simple To-Do app.
> I need add, delete, and complete check features.
```

Claude will automatically:
1. Create the necessary files
2. Write the code
3. Tell you how to run it!

---

## Step 4: Check the Results

Open the generated files in your IDE:

**Open with VS Code:**
```bash
code .
```

Or run VS Code → **File** → **Open Folder** → Select project folder

---

## Useful Prompt Examples

### 🌐 Website Creation
```
Create a company introduction landing page.
The company name is "ABC Corp".
I need service introduction, team introduction, and contact sections.
Make it responsive so it looks good on mobile too.
```

### 📊 Data Analysis Tool
```
Create a simple dashboard that visualizes data
when I upload a CSV file.
I'd like bar charts and pie charts.
```

### 🤖 Work Automation
```
Create a Python script that extracts only data
matching certain conditions from an Excel file
and saves it to a new file.
The condition is to extract only rows where
the "Status" column is "Complete".
```

### 📝 Document Generation
```
Write a README.md file for this project.
It should include project description,
installation method, and usage instructions.
```

---

[← Previous: Skills & Agents](08-skills-agents.md) | [Next: Troubleshooting →](10-troubleshooting.md)
