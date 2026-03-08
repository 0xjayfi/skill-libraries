# 🏭 Agent Skill Factory
### A Claude Agent Skill that Creates Other Claude Agent Skills

Agent Skill Factory is a workflow automation meta‑skill that transforms natural language workflow descriptions into fully structured, production‑ready Claude Agent Skills.

Instead of manually writing:

- YAML frontmatter  
- SKILL.md logic  
- Trigger conditions  
- Folder structures  
- Testing plans  
- Troubleshooting instructions  

You simply describe the workflow you want Claude to automate — and this skill generates a reusable agent skill for it.

This allows you to move from prompting Claude to programming Claude’s behavior.

---

## 🚀 What This Skill Does

Agent Skill Factory takes:
"I want Claude to audit HTML pages or URLs for SEO compliance and prepare them for ISO content review"


And turns it into:

- A complete skill folder  
- Properly formatted SKILL.md  
- Optimized YAML frontmatter  
- Trigger phrases  
- Multi‑step workflow instructions  
- Validation gates  
- Troubleshooting section  
- Testing plan  
- Distribution‑ready structure  

You get a reusable Claude Agent Skill that can now automatically execute that workflow in future conversations without needing to re‑prompt.

---

## 🧠 Why Use This Skill

Claude Agent Skills are powerful — but creating them manually requires:

- Understanding progressive disclosure
- Writing correct YAML frontmatter
- Defining trigger conditions
- Structuring orchestration workflows
- Avoiding over‑triggering and under‑triggering
- Packaging for distribution

Agent Skill Factory automates that entire process by converting workflow intent into structured reusable behavior.

---

## 🧩 Use Cases

Use this when you want Claude to:

- Follow a repeatable methodology
- Generate structured documents consistently
- Execute multi‑step workflows
- Coordinate MCP integrations
- Audit files or URLs
- Prepare compliance reports
- Transform input files before processing
- Generate code artifacts
- Standardize internal processes

Examples:
- Create a skill that generates frontend designs from PRDs
- Build a skill that prepares uploaded PDFs for ISO audit review
- Turn this customer onboarding workflow into a Claude skill

---

## 🛠 Skill Creation Pipeline

When invoked, Agent Skill Factory performs the following steps:

### 1. Extract Use Case

Identifies:

- Desired outcome
- User intent
- Trigger phrases
- Required workflow steps
- Required tools or MCP integrations
- Embedded domain knowledge
- Input file types if present

---

### 2. Classify Skill Type

Automatically detects whether the new skill is:

- Document & Asset Creation  
- Workflow Automation  
- MCP Enhancement  

---

### 3. Generate Skill Folder

Creates:
skill-name/
└── SKILL.md

Naming rules:

- lowercase
- kebab‑case
- no spaces
- no capitals
- no underscores

---

### 4. Generate YAML Frontmatter

Includes:

- Skill purpose  
- When to trigger  
- Invocation phrases  
- Metadata  
- Versioning  

Optimized for:

- Automatic loading  
- Trigger accuracy  
- Reduced token usage  

---

### 5. Build Instructions

Adds:

- Sequential workflow orchestration  
- Validation logic  
- Input preparation steps  
- Iteration loops  
- Error handling  
- Output finalization  

Supports:

- URLs  
- HTML  
- PDFs  
- CSV  
- Images  
- Documents  

---

### 6. Add Examples

Includes:

- Common invocation  
- Paraphrased invocation  
- Edge case usage  

---

### 7. Add Troubleshooting

Handles:

- Over‑triggering  
- Under‑triggering  
- Tool failures  
- Input preparation issues  

---

### 8. Generate Testing Plan

Produces:

Should Trigger queries  
Should NOT Trigger queries  

## 📦 Installation
``` 
npx skills add https://github.com/agharsallah/agent-skill-factory
```

## ✅ Usage
After installation simply say:
```Create a skill that audits HTML pages or URLs for SEO compliance
```
or
```
Turn this workflow into a reusable Claude Agent Skill:
[paste workflow]
```
Agent Skill Factory will generate:

* Folder
* SKILL.md
* Instructions
* Trigger logic
* Testing plan

## 🔁 Iterative Mode
You can improve generated skills by saying:
```
Improve this skill
Fix triggering
Handle HTML inputs
Make it less broad
Support URLs and PDFs
```

The skill will:

* Refine frontmatter
* Improve triggers
* Add validation logic
* Expand file‑type support
* Update metadata version