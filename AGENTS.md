# AGENTS.md - XKSkills

This file provides guidelines for agentic coding agents operating in the XKSkills repository.

## Project Overview

XKSkills is a personal collection of Agent Skills - reusable prompt templates that guide AI agents to perform specific tasks. Skills are stored as Markdown files with YAML frontmatter.

## Project Structure

```
XKSkills/
├── skills/
│   └── *.md              # Skill definition files
├── AGENTS.md             # This file
├── README.md             # Project documentation
└── LICENSE.txt           # MIT License
```

## Build / Test Commands

This is a documentation/repository project - there is no build system, tests, or linting to run.

- **No build commands required** - Skills are plain Markdown files
- **No tests** - Manual verification by reading skill content
- **No linting** - YAML frontmatter should be valid YAML

## Skill File Format

Each skill is a Markdown file with YAML frontmatter. Follow this exact structure:

```yaml
---
name: skill-name
description: Brief description of what this skill does (1-2 sentences)
license: Complete terms in LICENSE.txt
tags:
  - tag1
  - tag2
version: "1.0.0"
author: XKSkills
---

# Skill content in Markdown format
```

### Required Frontmatter Fields

| Field | Description | Example |
|-------|-------------|---------|
| `name` | Unique skill identifier (kebab-case) | `frontend-design` |
| `description` | One-sentence summary for skill selection | `Create distinctive...` |
| `license` | License reference | `Complete terms in LICENSE.txt` |
| `tags` | Array of searchable tags | `- frontend`, `- ui` |
| `version` | Semantic version string | `"1.0.0"` |
| `author` | Author name | `XKSkills` |

### Optional Frontmatter Fields

| Field | Description |
|-------|-------------|
| `instruction` | Detailed instructions (alternative to body content) |
| `examples` | Array of usage examples |
| `requires` | Dependencies or required context |

## Code Style Guidelines

Since skills are written in Markdown/YAML, follow these conventions:

### YAML Frontmatter

- Use 2 spaces for indentation (no tabs)
- Quote version strings: `"1.0.0"` not `1.0.0`
- Use kebab-case for names: `skill-name` not `skillName`
- Tags array uses hyphen prefix with 2-space indent

### Markdown Content

- Use ATX-style headers (`#`, `##`, `###`)
- Maximum line length: 100 characters
- Use fenced code blocks with language identifiers
- Use bullet lists for enumerations
- Use emphasis (`**bold**`, `*italic*`) sparingly

### Naming Conventions

- **Skill filenames**: `kebab-case.md` (e.g., `frontend-design.md`)
- **Skill names**: kebab-case
- **Tags**: lowercase, kebab-case if multiple words

### General Guidelines

1. **Be concise** - Skills should be focused and actionable
2. **Avoid agent-specific references** - Use "the agent" instead of "Claude", "ChatGPT", etc.
3. **Include examples** - Show, don't just tell
4. **Version bump** - Increment version when updating skills (follow semver)
5. **Write in English** - Skill content should be in English for broad compatibility

## Git Workflow

1. Create a new branch for each skill addition/modification
2. Use descriptive commit messages:
   - `Add new skill: <skill-name>`
   - `Update skill: <skill-name> to v1.1.0`
   - `Fix: <skill-name> - description of fix`
3. Pull request before merging to main
4. Never commit sensitive information

## Adding a New Skill

1. Create file: `skills/<skill-name>.md`
2. Add required frontmatter with proper formatting
3. Write skill content in Markdown
4. Update `README.md` to list the new skill
5. Commit and push following Git Workflow

## Error Handling

- **YAML syntax errors**: Use a YAML validator to check frontmatter
- **Broken links**: Verify all internal links work
- **Missing fields**: Ensure all required frontmatter fields are present

## Related Files

- `README.md` - Project documentation and skill listing
- `LICENSE.txt` - MIT License full text
