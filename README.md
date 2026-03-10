# Agent Skill Factory

A personal skill library and meta-skill for generating Claude Agent Skills from natural language workflow descriptions.

## What This Does

The root `SKILL.md` is a meta-skill — describe a workflow you want Claude to automate, and it generates a complete, reusable Agent Skill for it. Generated skills are stored in the `skills/` directory.

Instead of manually writing YAML frontmatter, trigger conditions, and workflow instructions, you describe what you want and get a properly structured `SKILL.md` ready for distribution.

## Repo Structure

```
agent-skill-factory/
  SKILL.md              # The factory (meta-skill)
  CLAUDE.md             # Claude Code project conventions
  README.md             # This file
  LICENSE               # MIT
  references/           # Official Anthropic skill-building guide
  skills/               # Generated skills live here
    {skill-name}/
      SKILL.md
```

## Installation

### Claude.ai
1. Download or clone this repo
2. Zip the root folder
3. Upload via **Settings > Capabilities > Skills**

### Claude Code
Place the skill folder in your Claude Code skills directory.

### Cross-machine usage
Clone this repo on any machine to access all your generated skills:
```
git clone https://github.com/0xjayfi/skill-libraries.git
```

Individual skills in `skills/` can be zipped and uploaded to Claude.ai independently.

## Usage

After installing, say:

```
Create a skill that audits HTML pages for SEO compliance
```

or

```
Turn this workflow into a reusable Claude Agent Skill:
[paste your workflow]
```

The factory generates a complete skill with:
- YAML frontmatter with trigger phrases
- Sequential workflow instructions
- Validation gates
- Examples
- Troubleshooting section
- Testing plan

Output goes to `skills/{skill-name}/SKILL.md`.

## Iterative Mode

Improve generated skills by saying:

```
Improve this skill
Fix triggering
Make it less broad
Support URLs and PDFs
```

## Acknowledgements

Forked from [agent-skill-factory](https://github.com/agharsallah/agent-skill-factory) by [Abderrahmen Gharsallah](https://github.com/agharsallah). Original work licensed under MIT.
