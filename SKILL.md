---
name: agent-skill-factory
description: Creates production-ready Claude Agent Skills from natural language workflow descriptions. Use when user asks to "build a skill", "create an agent skill", "generate a Claude skill", "turn this workflow into a skill", or wants to automate a repeatable process into a reusable skill.
license: MIT
metadata:
  author: Abderrahmen Gharsallah
  version: 0.0.1
  category: workflow-automation
  tags: [skills, automation, agents, meta-skill]
---

# Agent Skill Factory

Agent Skill Factory is a workflow automation skill that transforms repeatable user workflows into fully packaged Claude Agent Skills.

Use this skill whenever a user:

- Wants to automate a recurring process
- Wants Claude to follow a consistent methodology
- Mentions building an agent or reusable workflow
- Says "create a skill for this"
- Wants standardized document, code, or audit generation
- Wants MCP workflows orchestrated automatically
- Wants Claude to consistently apply domain knowledge
- Wants to turn a process into a reusable behavior

This skill converts a natural language workflow description into a distribution-ready Claude Agent Skill that follows required structure and triggering logic.

---

## Workflow: Skill Creation Pipeline

Follow this sequence exactly.

---

### Step 1 — Extract Use Case

From the user input identify:

- Desired outcome
- User intent
- Multi-step workflow required
- Required tools or MCP integrations
- Domain knowledge or methodology to embed
- Input types involved (URL, HTML, PDF, CSV, Docs, Images)

Generate internally:

Use Case  
Trigger  
Steps  
Result  

---

### Step 2 — Classify Skill Type

Determine which category applies:

1. Document & Asset Creation
2. Workflow Automation
3. MCP Enhancement

Store classification for frontmatter optimization.

---

### Step 3 — Generate Skill Folder Name

Convert outcome into:

- lowercase
- kebab-case
- no capitals
- no spaces
- no underscores

Example:

SEO Blog Auditor → seo-blog-auditor

Folder name must match skill name.

---

### Step 4 — Generate YAML Frontmatter

Produce:

- name
- description
- metadata

Description MUST include:

- What the skill does
- When it should be used
- Trigger phrases users might say

Ensure:

- Under 1024 characters
- No XML brackets
- Includes user-facing invocation phrases
- Matches folder name exactly

---

### Step 5 — Generate SKILL Instructions

Instructions must include:

- Sequential workflow steps
- Validation gates before execution
- Input preparation logic
- Iterative refinement loop (if quality sensitive)
- Tool orchestration logic
- Output finalization step

If workflow may accept:

- URLs
- HTML files
- PDFs
- CSV
- Images
- Documents

Then include file preparation step.

---

### CRITICAL EXECUTION RULES

Do not skip validation steps.

Always:

- Prepare files before processing
- Normalize URLs before audit
- Validate structure before execution
- Iterate until quality threshold met

Quality is more important than speed.

---

### Step 6 — Add Examples

Include:

#### Example 1 — Common Invocation

User says:

Create a skill that generates ISO audit reports from uploaded HTML files.

Actions:

- Extract use case
- Generate frontmatter
- Build instructions
- Produce SKILL.md

Result:

Reusable auditing skill generated.

---

#### Example 2 — Paraphrased Invocation

User says:

Turn this compliance workflow into a Claude Agent Skill.

---

#### Example 3 — Edge Invocation

User says:

Build a reusable skill that analyzes URLs and PDFs before regulatory review.

---

### Step 7 — Add Troubleshooting Section

Include:

#### Skill Undertriggering

Cause:

Description too vague.

Fix:

Add:

- user-facing phrases
- workflow outcomes
- input file types

---

#### Skill Overtriggering

Cause:

Description too broad.

Fix:

Add:

- scope clarification
- domain specificity
- negative triggers

---

#### Tool or MCP Failures

Checklist:

- MCP server connected
- Authentication valid
- Tool names correct
- Retry execution

---

#### Input Preparation Issues

If audit fails:

- Confirm files are parsed
- Normalize URL formatting
- Validate HTML structure
- Ensure required fields present

---

### Step 8 — Trigger Testing Plan

Generate test cases.

Should Trigger:

- "Create a skill for ISO auditing"
- "Turn this workflow into a Claude skill"
- "Build a reusable auditing skill"

Should NOT Trigger:

- "What's the weather?"
- "Write Python code"
- "Create a spreadsheet"

---

### Step 9 — Distribution Output

Produce:

skill-name/
└── SKILL.md

Output must be ready for:

Claude.ai → Settings → Capabilities → Skills → Upload

---

## Iterative Refinement Mode

If user says:

- Improve this skill
- Fix triggering
- Make it more specific
- Support HTML or URLs
- Handle PDFs
- Update instructions

Then:

- Revise description
- Add file-type support
- Add validation logic
- Add negative triggers
- Improve orchestration
- Update metadata version