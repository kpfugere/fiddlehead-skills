# fiddlehead-skills

a collection of skills that turn meeting transcripts into useful things. works with [claude code](https://claude.com/claude-code), [fiddlehead](https://fiddleheadai.com), and any markdown-formatted meeting notes.

skills are markdown files. drop one in your notes folder and your ai agent knows what to do.

## skills

| skill | what it does |
|-------|-------------|
| **meeting follow-up** | drafts follow-up emails from action items and decisions |
| **decision log** | extracts decisions across meetings into a running log |
| **meeting prep** | reviews past meetings with a contact to prep you for the next one |
| **weekly summary** | aggregates a week of meetings into a digest with themes and open items |
| **linear issue creator** | turns action items into structured linear issues |
| **stakeholder update** | generates a polished status update for leadership or investors |
| **accountability tracker** | tracks who committed to what and flags overdue items |
| **topic tracker** | traces how a topic evolved across meetings over time |
| **meeting debrief** | structured post-mortem with dynamics, signals, and suggested follow-ups |
| **meeting roi** | scores your meetings by outcomes and identifies time sinks |
| **personal 360** | analyzes your communication patterns to surface strengths, blind spots, and growth areas |
| **strategy frameworks** | applies proven business frameworks (SWOT, Porter's, BCG, Blue Ocean, JTBD, etc.) to evaluate companies, products, and markets |
| **trend impact analysis** | projects the cascading, second-order impacts of an emerging trend on markets and incumbents |

the last two are folder-based skills (a `SKILL.md` plus a `references/` directory) rather than single files. install them by copying the whole skill folder.

## install

download any `.md` file from the `skills/` directory and drop it into your meeting notes folder — the same folder your transcripts live in.

when you open that folder with claude code, the skill is available. just ask for it by name:

```
> run the stakeholder update skill on this week's meetings
> use the accountability tracker for the last 14 days
> debrief my last meeting
```

alternatively, copy the skill file into `~/.claude/skills/<skill-name>/SKILL.md` to make it available globally across all projects.

for folder-based skills (e.g. **strategy frameworks**, **trend impact analysis**), copy the entire skill folder from `skills/<skill-name>/` — keep the `SKILL.md` and its `references/` directory together.

## transcript format

skills work with any markdown meeting notes. the expected format is daily documents with meetings as `##` sections:

```markdown
---
date: 2026-03-18
---

# Tuesday, March 18, 2026

## Meeting Title
*10:00 AM · 28m · 3 speakers · tags: topic1, topic2*

### Summary
What happened in the meeting.

### Action Items
- [ ] Do the thing (@person, by date)

### Key Points
- Important detail

### Transcript
**Speaker:** What they said...
```

see `examples/sample-transcript.md` for a complete example with multiple meetings.

if your transcripts use a different format (granola, otter, etc.), most skills will still work — they search for common patterns like checkboxes, speaker labels, and section headings.

## write your own

skills are just markdown with yaml frontmatter. see [CONTRIBUTING.md](CONTRIBUTING.md) for the format spec and guidelines.

```markdown
---
name: My Custom Skill
description: What it does in one line
trigger: manual
version: 1.0
author: your-name
---

# My Custom Skill

## Purpose
Why this skill exists.

## Instructions
Step-by-step guide for the agent.

## Example Output
What good output looks like.
```

## about

built by [fiddlehead](https://fiddleheadai.com) — a macos meeting recorder that captures, transcribes, and structures your meetings as local markdown files.

skills work with transcripts from any source. fiddlehead just happens to produce them automatically.
