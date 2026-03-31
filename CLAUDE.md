# Claude Code Vault — Conventions

This vault is the shared memory layer for all Claude Code agents. It stores session logs, research summaries, insights, and atomic notes.

## YAML Frontmatter (Required)

Every note must have this frontmatter block at the top:

```yaml
---
created: YYYY-MM-DD
modified: YYYY-MM-DD
tags: [tag1, tag2]
aliases: [Friendly Title]
---
```

## Link Syntax

- Internal link: `[[slug|Title]]`
- Embed note: `![[slug]]`
- URL link: [Title](https://example.com)

## Topic Slug Formation

- All lowercase
- Words separated by hyphens
- Max 5 words per slug
- Examples: `linkedin-scraping`, `polymarket-trading`, `claude-code-handoff`

## Tag Conventions

| Tag | Use For |
|-----|---------|
| `#agent/[name]` | Which agent was involved |
| `#project/[name]` | Which project this belongs to |
| `#mistake/[type]` | Mistake category (e.g., mistake/syntax, mistake/logic) |
| `#win/[type]` | Success category (e.g., win/automation, win/research) |
| `#deprecated` | Obsolete approach — always link to replacement |
| `#auto-captured` | Backup-logged session (incomplete) |
| `#insight` | Pattern insight note |
| `#weekly-review` | Weekly newsletter note |

## Directory Purposes

| Directory | What Goes Here |
|----------|----------------|
| `daily/` | Session logs — one file per day, multiple sessions appended |
| `research/summaries/` | Summary-only logs when no further engagement with ingested content |
| `research/videos/` | Video ingestion notes |
| `research/articles/` | Article/podcast ingestion notes |
| `notes/topics/` | Atomic notes on specific topics |
| `notes/projects/` | Project-specific notes |
| `notes/insights/repeated-mistakes/` | Pattern-detected repeated mistakes |
| `notes/insights/improvement-opportunities/` | Agent/workflow improvement suggestions |
| `notes/insights/weekly-reviews/` | Weekly newsletter outputs |
| `projects/` | Project index notes |
| `backlog/` | Deferred ideas, things to try later |
| `deprecated/` | Deprecated approach documentation |
| `tags/` | Tag index files |

## How to Deprecate an Old Approach

When a better approach is found:

1. Edit the old note:
   - Add `#deprecated` tag
   - Add `deprecated-reason: [why it's obsolete]` in frontmatter
   - Add `replaced-by: [[new-slug]]` in frontmatter
   - Add a line at the top: `> Deprecated: replaced by [[new-slug]]`

2. In the new note (or this update):
   - Document WHY the old way was replaced
   - Include the context of what prompted the change

## Daily Note Schema

Each session entry in `daily/YYYY-MM-DD.md` follows this schema:

```
## Session N — HH:MM AM/PM
**Project:** [slugified project name]
**Agent:** [claude-researcher | legion-research-agent]
**What went wrong:** [specific error or mistake; "none" if nothing]
**Root cause:** [why it failed; "n/a" if nothing]
**What worked:** [what succeeded]
**Key takeaway:** [one pattern to remember]
**Tags:** #agent/[name] #project/[name] #mistake/[type] #win/[type]
```

## Weekly Review Schema

Generated at `notes/insights/weekly-reviews/YYYY-WXX.md`:

```
# Weekly Review — YYYY Week XX

## Week Overview
[High-level summary]

## Completed
- [item]

## Mistakes Made
- [mistake]: root cause → fix applied

## Wins
- [win]

## Deprecated
- [old] → replaced by [new] (WHY)

## Recommendations for Next Week
1. [recommendation]
2. [recommendation]

## Topics Researched
- [summary] → [[link]]
```

## Coordination

When writing to the vault, check `COORDINATION.md` first. Only one agent writes at a time.
