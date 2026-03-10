# CLAUDE.md

## Project Overview

This is a personal skill library and meta-skill factory for Claude Agent Skills. The root `SKILL.md` is the factory — it generates new skills. Generated skills are stored in `skills/{skill-name}/SKILL.md`.

## Conventions

### When generating a new skill:
1. Create it at `skills/{skill-name}/SKILL.md`
2. Folder name MUST match the `name` field in YAML frontmatter
3. Folder names: lowercase, kebab-case, no spaces, no underscores
4. Follow the output template defined in the root SKILL.md
5. Run the validation checklist before delivering
6. Use `references/The-Complete-Guide-to-Building-Skill-for-Claude.pdf` as the authoritative spec

### SKILL.md format rules:
- YAML frontmatter: `name` and `description` are required
- `name`: max 64 chars, lowercase kebab-case only
- `description`: max 1024 chars, no XML brackets (< >), must include WHAT it does + WHEN to use it + trigger phrases
- Body: under 5,000 words
- Use imperative voice in workflow instructions
- Include examples and a testing plan
- No README.md inside skill folders

### What NOT to do:
- Do not modify the root SKILL.md unless explicitly asked
- Do not create nested categories inside `skills/`
- Do not add npm/node dependencies — this is a pure markdown project
- Do not use "claude" or "anthropic" in skill names (reserved)
