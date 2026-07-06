# contributing

thanks for your interest in contributing a skill. skills are simple markdown files — if you can write a good prompt, you can write a skill.

## skill format

every skill is a single `.md` file with yaml frontmatter:

```markdown
---
name: Skill Name
description: One-line description of what it does
trigger: manual
version: 1.0
author: your-github-username
---

# Skill Name

## Purpose
1-2 sentences explaining what pain this skill solves and who it's for.

## Instructions
Numbered step-by-step instructions that an AI agent can follow.
Be specific about what to search for, how to process it, and what to output.

## Example Output
A realistic example of what good output looks like.
Wrap in a code block so the agent treats it as a template, not literal output.
```

### frontmatter fields

| field | required | description |
|-------|----------|-------------|
| `name` | yes | human-readable name |
| `description` | yes | one line — shown in the skills gallery |
| `trigger` | yes | `manual` (user invokes it) or a description of when it should activate |
| `version` | yes | semver string |
| `author` | yes | your name or github handle |
| `requires` | no | mcp tool dependency, e.g. `slack`, `hubspot`, `linear` |

### folder-based skills

most skills are a single `.md` file. if a skill needs supporting material — reference docs, framework libraries, templates the agent reads on demand — it can instead be a folder:

```
skills/
  my-skill/
    SKILL.md          # the entry point (same frontmatter as above)
    references/       # optional supporting files the SKILL.md points to
      thing-a.md
      thing-b.md
```

use this form when the instructions would be too large for one file, or when the agent should load detail selectively (e.g. pick 2 of 10 frameworks) rather than reading everything up front. `SKILL.md` is the required entry point and should reference supporting files by relative path (e.g. `references/thing-a.md`). see `skills/strategy-frameworks/` for a working example.

keep single-file skills single-file — only reach for a folder when the extra material earns it.

## guidelines

### make it transcript-agnostic
- don't hardcode paths like `~/Documents/Fiddlehead/`
- say "the user's notes directory" or "search for meeting notes"
- handle common transcript formats: checkboxes, speaker labels (`**Name:**`), section headings

### be specific in instructions
- tell the agent exactly what patterns to search for (e.g., `- [ ]` for action items, `## ` for meeting headings)
- specify what to include and what to filter out
- include edge cases (e.g., "if no action items are found, say so clearly")

### write a good example
- the example output is the most important part — it shows the agent what "good" looks like
- use realistic but synthetic data (no real names, companies, or sensitive info)
- show the full structure including headers, formatting, and any special sections

### keep it focused
- one skill, one job. don't make a skill that does five things
- if you're tempted to add "optionally also do X", that's a second skill

### test it
- try your skill against the sample transcript in `examples/sample-transcript.md`
- verify the agent produces output that matches your example's structure and quality

## submitting

1. fork this repo
2. add your skill file to `skills/`
3. test it against the sample transcript
4. open a PR with a brief description of the skill and who it's for

we'll review for quality, clarity, and overlap with existing skills.
