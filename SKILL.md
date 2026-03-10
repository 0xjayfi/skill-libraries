---
name: agent-skill-factory
description: Generates production-ready Claude Agent Skills from natural language workflow descriptions. Transforms repeatable processes into structured SKILL.md files with proper frontmatter, triggering logic, and testing plans. Use when user asks to "build a skill", "create an agent skill", "generate a Claude skill", "turn this workflow into a skill", or "package this as a reusable skill". Do NOT use for executing existing workflows, writing general code, creating documents, or one-off tasks.
license: MIT
metadata:
  version: 1.0.0
  category: workflow-automation
  tags: [skills, automation, agents, meta-skill]
---

# Agent Skill Factory

Transforms natural language workflow descriptions into distribution-ready Claude Agent Skills.

Use this skill when a user explicitly wants to CREATE, BUILD, or GENERATE a reusable Claude Agent Skill. Do NOT activate for general automation requests, one-off tasks, or requests that do not mention creating a skill.

For the full specification of YAML fields, description patterns, and file structure rules, consult `references/The-Complete-Guide-to-Building-Skill-for-Claude.pdf`.

---

## Workflow: Skill Creation Pipeline

Follow this sequence exactly. Do not skip validation gates.

---

### Step 1 -- Extract Use Case

Ask the user the following if not already answered:

1. What outcome should this skill produce?
2. What steps do you currently follow manually?
3. What tools or services are involved (MCP servers, APIs, file types)?
4. What phrases would you say to trigger this workflow?

From responses, construct this internal structure:

```
Use Case: [one-sentence outcome]
Trigger: User says "[phrase 1]", "[phrase 2]", or "[phrase 3]"
Steps:
  1. [First action]
  2. [Second action]
  ...
Result: [What the user receives when complete]
```

#### Validation Gate
Do not proceed unless Use Case, Trigger, Steps, and Result are all populated. If input is ambiguous, ask a clarifying question.

---

### Step 2 -- Classify Skill Type

Determine which category applies based on these criteria:

1. **Document & Asset Creation** -- Skill produces consistent output (docs, code, designs, reports). No external tools required. Key techniques: embedded style guides, templates, quality checklists.
2. **Workflow Automation** -- Skill executes multi-step processes with consistent methodology. Key techniques: step-by-step workflow with validation gates, iterative refinement loops.
3. **MCP Enhancement** -- Skill adds workflow guidance on top of MCP tool access. Key techniques: coordinates multiple MCP calls, embeds domain expertise, provides error handling for MCP issues.

Store the classification for frontmatter.

---

### Step 3 -- Generate Skill Folder Name

Convert the outcome into a folder name:

- lowercase
- kebab-case
- no capitals, no spaces, no underscores
- max 64 characters
- must NOT contain "claude" or "anthropic" (reserved)

Example: SEO Blog Auditor --> `seo-blog-auditor`

The folder name MUST match the `name` field in YAML frontmatter.

Create the skill at: `skills/{skill-name}/SKILL.md`

---

### Step 4 -- Generate YAML Frontmatter

Produce the frontmatter using this template:

```yaml
---
name: {skill-name}
description: {What it does}. {When to use it with trigger phrases}. Do NOT use for {negative triggers}.
license: MIT
metadata:
  version: 1.0.0
  category: {document-creation | workflow-automation | mcp-enhancement}
  tags: [{tag1}, {tag2}, {tag3}]
---
```

Field rules:

- **name**: kebab-case, matches folder name
- **description**: MUST include all three parts:
  1. What the skill does (one sentence)
  2. When to use it with 3-5 specific trigger phrases
  3. Negative triggers to prevent over-triggering
- **description**: under 1024 characters, no XML brackets (< >)

#### Validation Gate
Before proceeding, verify:
- [ ] `name` is kebab-case and matches folder name
- [ ] `description` is under 1024 characters
- [ ] `description` contains what + when + negative triggers
- [ ] No XML angle brackets (< >) anywhere in frontmatter
- [ ] Frontmatter has `---` delimiters on their own lines

---

### Step 5 -- Generate SKILL.md Body

Write the skill instructions following this exact structure:

```markdown
# {Skill Name}

{One paragraph: what this skill does and when to use it.}

## Workflow

### Step 1 -- {Name}
{Clear, specific instructions. Use imperative voice.}

#### Validation Gate
{Checklist: what must be true before proceeding.}

### Step 2 -- {Name}
{Instructions for this step.}

(Continue for all steps...)

## Examples

### Example 1 -- Common Usage
User says: "{typical trigger phrase}"
Actions:
1. {action}
2. {action}
Result: {outcome}

### Example 2 -- Alternate Phrasing
User says: "{paraphrased trigger}"
Actions:
1. {action}
Result: {outcome}

## Troubleshooting

### {Problem Title}
Cause: {why it happens}
Fix: {specific steps to resolve}

## Testing Plan

Should trigger:
- "{phrase 1}"
- "{phrase 2}"
- "{phrase 3}"

Should NOT trigger:
- "{near-miss phrase 1}"
- "{near-miss phrase 2}"
- "{near-miss phrase 3}"
```

Instruction quality rules:
- Be specific and actionable. Write `Run scripts/validate.py --input {file}` not `Validate the data`.
- Use numbered steps and bullet points.
- Put critical rules at the top with `## Important` headers.
- Include error handling for each step.
- Keep total SKILL.md body under 5,000 words.
- If the skill handles file types, include a file preparation step.

#### Validation Gate
Before proceeding, verify:
- [ ] At least 2 workflow steps with clear ordering
- [ ] Each step uses imperative voice with specific actions
- [ ] At least 2 examples with User says / Actions / Result
- [ ] Troubleshooting covers over-triggering and under-triggering
- [ ] Testing plan has at least 3 should-trigger and 3 should-NOT-trigger queries
- [ ] Total body is under 5,000 words

---

### Step 6 -- Review and Finalize

Review the complete generated SKILL.md against this checklist:

- [ ] Folder named in kebab-case
- [ ] SKILL.md file exists (exact case)
- [ ] YAML frontmatter has `---` delimiters
- [ ] `name` field: kebab-case, no spaces, no capitals
- [ ] `description` includes WHAT and WHEN and negative triggers
- [ ] No XML tags (< >) anywhere
- [ ] Instructions are clear and actionable
- [ ] Error handling included
- [ ] Examples provided with Actions and Result
- [ ] Testing plan included

Present the complete skill to the user. If any check fails, fix it before delivering.

Output location: `skills/{skill-name}/SKILL.md`

The skill is ready for:
- Upload to Claude.ai via Settings > Capabilities > Skills (zip the folder first)
- Placement in Claude Code skills directory

---

## Examples

### Example 1 -- Common Invocation

User says: "Create a skill that audits HTML pages for SEO compliance"

Actions:
1. Extract use case: SEO audit workflow with HTML input
2. Classify: Document & Asset Creation
3. Generate folder: `seo-page-auditor`
4. Generate frontmatter with SEO-specific trigger phrases
5. Build 4-step workflow: fetch page, audit meta tags, audit content structure, generate report
6. Add examples, troubleshooting, testing plan
7. Review against checklist

Result: Complete skill at `skills/seo-page-auditor/SKILL.md`

### Example 2 -- Paraphrased Invocation

User says: "Turn this compliance workflow into a Claude Agent Skill"

Actions:
1. Ask user to describe the compliance workflow steps
2. Extract use case from their description
3. Classify: Workflow Automation
4. Generate skill with compliance-specific validation gates

Result: Complete skill with embedded compliance methodology

### Example 3 -- Edge Invocation

User says: "Build a reusable skill that analyzes URLs and PDFs before regulatory review"

Actions:
1. Extract use case: multi-format input processing for regulatory review
2. Classify: Workflow Automation with file preparation
3. Include file preparation step for both URLs and PDFs
4. Add input validation for supported file types

Result: Complete skill with file-type detection and preparation logic

---

## Troubleshooting

### Generated YAML Won't Parse
Cause: Unclosed quotes, missing `---` delimiters, or XML brackets in description.
Fix:
1. Verify `---` appears on its own line before AND after frontmatter
2. Check for `<` or `>` characters in description (forbidden)
3. Ensure string values with special characters are quoted
4. Confirm indentation uses spaces, not tabs

### Description Over 1024 Characters
Cause: Too many trigger phrases or verbose explanation.
Fix: Keep what-it-does to one sentence. Limit trigger phrases to 5-7. Move details to the SKILL.md body.

### Skill Name Rejected
Cause: Name contains spaces, capitals, underscores, or reserved words (claude, anthropic).
Fix: Convert to kebab-case. Remove reserved prefixes. Ensure name matches folder name.

### Generated Skill Does Not Trigger
Cause: Description too vague or missing trigger phrases.
Fix: Add 3-5 specific trigger phrases the user would actually say. Mention file types if relevant. Test with paraphrased queries.

### Generated Skill Triggers Too Often
Cause: Description too broad or missing negative triggers.
Fix: Add "Do NOT use for..." clause. Be more specific about the domain. Add scope clarification.

---

## Testing Plan

Should trigger:
- "Create a skill for ISO auditing"
- "Turn this workflow into a Claude skill"
- "Build a reusable auditing skill"
- "Package this process as a skill"
- "Generate a SKILL.md for this workflow"
- "Help me build an agent skill"
- "Make a Claude skill from this process"

Should NOT trigger:
- "Help me automate this data pipeline" (execution, not skill creation)
- "Write a Python script for CSV processing" (code, not skill)
- "Create a document template" (document creation, not skill creation)
- "Set up my project in Linear" (using a tool, not creating a skill)
- "What is a Claude Agent Skill?" (informational, not creation)

---

## Iterative Refinement Mode

If user says "improve this skill", "fix triggering", "make it more specific", "support URLs", or "update instructions":

1. Read the existing skill from `skills/{skill-name}/SKILL.md`
2. Identify the issue (under-triggering, over-triggering, missing steps, etc.)
3. Apply the fix
4. Re-run the validation checklist
5. Increment the version in metadata (patch for fixes, minor for new features)

Version strategy:
- Patch (x.x.1): Fix typos, adjust trigger phrases, improve wording
- Minor (x.1.0): Add workflow steps, expand file-type support, add examples
- Major (1.0.0): Change the fundamental workflow or skill purpose
