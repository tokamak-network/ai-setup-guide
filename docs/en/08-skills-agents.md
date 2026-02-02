# 8. Skills & Agents Guide

[← Back to Table of Contents](../../README.md)

---

Skills and Agents are tools that extend the functionality of Claude Code.

> **Purpose of this document**: Focuses on features useful for non-developers such as researchers and HR teams.

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

## 📊 Practical Skills for Non-Developers

### Excel/Spreadsheet Work (xlsx)

The most useful feature for researchers and HR teams.

| Feature | Description | Example Request |
|---------|-------------|-----------------|
| Create new Excel | Save data to Excel | "Create an Excel file from this data" |
| Analyze existing files | Read and analyze Excel data | "Analyze this Excel file" |
| Auto-generate formulas | Write complex formulas | "Create a VLOOKUP formula" |
| Data cleanup | Remove duplicates, standardize format | "Clean up duplicate data" |
| Pivot tables | Create summary tables | "Summarize sales data by month" |
| CSV conversion | Convert between formats | "Convert CSV to Excel" |

**Practical Examples - Researchers:**
```
> Read survey_results.xlsx and calculate average scores by age group
  → xlsx skill analyzes file and creates statistical table

> Perform correlation analysis on this data and save results to a new sheet
  → Statistical analysis and result storage

> Convert research data to SPSS-compatible format
  → Convert to CSV or compatible format
```

**Practical Examples - HR Team:**
```
> Count employees by department from the staff list
  → Creates aggregate results in pivot table format

> Calculate mean, median, and standard deviation from salary data
  → Statistical analysis and results summary

> Create monthly work hours report from attendance records
  → Data processing into report format

> Merge two Excel files based on employee ID
  → VLOOKUP/merge operation
```

---

### Word Document Work (docx)

For reports, proposals, contracts, and other document work.

| Feature | Description | Example Request |
|---------|-------------|-----------------|
| Create new document | Write Word documents | "Create a report in Word" |
| Edit existing document | Modify/add content | "Add a summary to this document" |
| Apply formatting | Headers, tables, TOC | "Add a table and format it" |
| Use templates | Write to specific format | "Write according to this template" |
| Track changes | Record modifications | "Edit with track changes enabled" |

**Practical Examples:**
```
> Create meeting minutes. Attendees: John, Jane. Agenda: Q2 Planning
  → Generates document matching meeting minutes template

> Write this research result as a paper-style report
  → Structured with Introduction, Methods, Results, Conclusion

> Create an employee evaluation form template
  → Generates Word form with evaluation criteria
```

---

### PDF Work (pdf)

For PDF document processing and form work.

| Feature | Description | Example Request |
|---------|-------------|-----------------|
| Extract PDF text | Read/analyze content | "Summarize this PDF" |
| Create PDF | Write new PDF | "Create report as PDF" |
| Fill forms | Input PDF forms | "Fill out this application" |
| Merge/split | File management | "Merge these PDFs into one" |
| Extract tables | Get table data | "Convert PDF table to Excel" |

**Practical Examples:**
```
> Summarize the key points from this research paper PDF
  → PDF analysis and summary provided

> Extract important clauses from the contract PDF
  → Key clauses organized

> Merge department reports PDFs into one file
  → PDF merge operation
```

---

### Presentation Work (pptx)

For creating presentations and training materials.

| Feature | Description | Example Request |
|---------|-------------|-----------------|
| Create new presentation | Write PPT | "Create a presentation" |
| Edit slides | Modify/add content | "Add a chart to slide 5" |
| Apply layouts | Design organization | "Clean up slide design" |
| Speaker notes | Write scripts | "Add speaker notes" |

**Practical Examples:**
```
> Create a 10-slide quarterly results presentation
  → Generates structured PPT

> Create new employee orientation materials
  → Creates training slides

> Visualize this data as charts and insert into slides
  → Data visualization and PPT insertion
```

---

## 📈 Data Analysis and Visualization

### Analysis Request Examples

| Analysis Type | Example Request |
|--------------|-----------------|
| Descriptive Statistics | "Calculate mean, standard deviation, and quartiles" |
| Correlation Analysis | "Analyze correlations between variables" |
| Group Comparison | "Compare differences between Group A and Group B" |
| Trend Analysis | "Analyze trends over time" |
| Text Analysis | "Extract keywords from survey responses" |

**Advanced Analysis for Researchers:**
```
> Calculate Cronbach's Alpha from survey data
  → Reliability analysis performed

> Run regression analysis and organize results in a table
  → Regression analysis and result table generation

> Cluster this data to classify types
  → Clustering analysis
```

---

### Chart/Graph Creation

| Chart Type | Use Case | Example Request |
|-----------|----------|-----------------|
| Bar Graph | Comparison | "Sales by department as bar graph" |
| Line Graph | Trends | "Monthly changes as line graph" |
| Pie Chart | Proportions | "Composition ratio as pie chart" |
| Scatter Plot | Relationships | "Relationship of two variables as scatter plot" |
| Heatmap | Patterns | "Correlations as heatmap" |

---

## 📝 Document Co-authoring (doc-coauthoring)

A workflow that helps with systematic document creation.

**Use Cases:**
- Research reports
- Proposals/planning documents
- Policy documents
- Manuals/guides

**How It Works:**
```
1. Define document purpose and target audience
2. Design structure (table of contents)
3. Draft sections
4. Review and revise
5. Final review
```

**Example:**
```
> Create a new employee onboarding guide
  → doc-coauthoring guides step-by-step document creation
```

---

## 🔍 Web Search and Information Gathering

### Research/Investigation Use

| Feature | Description | Example Request |
|---------|-------------|-----------------|
| Web search | Search latest info | "Search AI trends 2024" |
| Web scraping | Extract page content | "Summarize this URL content" |
| Information synthesis | Organize multiple sources | "Synthesize information on this topic" |

**Practical Examples:**
```
> Research competitors A, B, C product prices and create comparison table
  → Web search and comparison table creation

> Summarize key contents from these papers into a literature review table
  → Literature analysis and organization

> Research recent HR trends and write a report
  → Search, analyze, document creation
```

---

## Development Skills

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

## Agents for Non-Developers

| Agent | Role | Usage Example |
|-------|------|---------------|
| `librarian` | Document/research analysis | "Analyze these materials" |
| `document-writer` | Document writing | "Write a report" |
| `explore` | Fast file search | "Find related files" |
| `multimodal-looker` | Image/chart analysis | "Analyze this chart" |
| `planner` | Work planning | "Create a plan for this project" |

**Practical Examples for Researchers/HR:**
```
> Analyze these 5 paper PDFs and compare key contents
  → librarian performs literature analysis

> Look at this survey result chart image and summarize insights
  → multimodal-looker analyzes visual materials

> Create a plan for improving the recruitment process
  → planner establishes step-by-step plan
```

---

## Agents for Developers

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

## 💼 Quick Reference by Role

### Researchers

| Task | Example Request |
|------|-----------------|
| Data Analysis | "Analyze this Excel data statistically" |
| Literature Review | "Summarize these papers into a comparison table" |
| Survey Analysis | "Analyze and visualize survey results" |
| Report Writing | "Write analysis results as a research report" |
| References | "Create a bibliography from these sources" |

### HR Team

| Task | Example Request |
|------|-----------------|
| Employee Data | "Organize staff list by department" |
| Salary Analysis | "Calculate salary data statistics" |
| Recruitment | "Create candidate evaluation sheet" |
| Training Materials | "Create new employee orientation PPT" |
| Evaluation Forms | "Create performance review template" |
| Attendance | "Create monthly attendance report" |

### General Office

| Task | Example Request |
|------|-----------------|
| Meeting Minutes | "Organize meeting content into minutes" |
| Email Drafts | "Draft announcement email" |
| Scheduling | "Organize project schedule" |
| Expense Reports | "Create travel expense report" |
| Report Formatting | "Format this content to report template" |

---

## 💡 Tips for Effective Requests

### Characteristics of Good Requests

1. **Be specific**
   ```
   ❌ "Analyze data"
   ✅ "Analyze monthly sales trends in sales_2024.xlsx and visualize as bar graph"
   ```

2. **Specify desired output**
   ```
   ❌ "Organize employee info"
   ✅ "Classify employee info by department and position into a pivot table"
   ```

3. **Specify file format**
   ```
   ❌ "Create a report"
   ✅ "Write analysis results as Word document and save data separately as Excel"
   ```

### For Complex Tasks

```
> Please do the following in order:
> 1. Read survey_data.xlsx file
> 2. Calculate response averages by age group
> 3. Visualize results as bar graph
> 4. Write analysis results as a report
```

---

## 🔗 Related Documents

- [First Project](09-first-project.md) - How to start your first project
- [Troubleshooting](10-troubleshooting.md) - Problem solutions
- [FAQ](11-faq.md) - Frequently asked questions

---

[← Previous: OpenCode Installation](07-opencode.md) | [Next: First Project →](09-first-project.md)
