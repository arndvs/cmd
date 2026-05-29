---
name: cmd-ingest
description: "Process new raw material into wiki pages. Use when asked to 'ingest', 'process this file', 'add to wiki', 'summarize this transcript', or '/cmd ingest [path]'."
---

# cmd-ingest

Output "Read cmd-ingest skill." to chat to acknowledge you read this file.

## Purpose

Process new files in `raw/` into structured `wiki/` pages. Extracts key information, creates or updates entity pages, maintains cross-references, and logs the operation.

## Inputs

- **Path** (optional) — specific file or directory in `raw/` to process. If omitted, scan all of `raw/` for unprocessed files.

## Steps

### 1. Resolve paths

```
CMD_DIR="${CMD_DIR:-$HOME/cmd}"
```

### 2. Identify new material

If a path argument was provided, process that file. Otherwise, scan `raw/` subdirectories for files not yet referenced in any `wiki/` page.

To check if a file has been ingested: search `wiki/` for references to the raw file path. If no wiki page references it, it's unprocessed.

### 3. Read and classify the source

Read the raw file and determine its type:

| Location | Type | Processing |
|---|---|---|
| `raw/articles/` | Article/research | Summarize key claims, extract entities, note source URL |
| `raw/transcripts/` | Meeting/conversation | Extract decisions, action items, people mentioned, key quotes |
| `raw/screenshots/` | Visual reference | Describe content, identify products/brands/patterns, note context |
| `raw/uploads/` | Misc document | Summarize content, identify entities and topics |
| `raw/data/` | Structured data | Describe schema, key metrics, date range, notable patterns |

### 4. Create or update wiki pages

For each entity (person, venture, client, concept) identified in the source:

**If wiki page exists** — append new information under a dated section:

```markdown
## Sources

### [YYYY-MM-DD] From: raw/transcripts/meeting-notes.md

- Key point 1
- Key point 2
```

**If wiki page doesn't exist** — create it:

- **People** → `wiki/people/<name-slug>.md`
- **Ventures** → `wiki/ventures/<name-slug>.md`
- **Clients** → `wiki/clients/<name-slug>.md`
- **Concepts** → `wiki/concepts/<topic-slug>.md`

Use the entity page template from `templates/wiki-page.md`:

```markdown
---
type: person | venture | client | concept
status: active
last_updated: YYYY-MM-DD
---

# <Name>

> <One-line tagline — what this is in ≤15 words>

## Summary

<2-3 sentences. What an AI session needs to know in 10 seconds.>

## Key facts

- **Source:** raw/<path>
- **First seen:** YYYY-MM-DD

## [Type-specific sections — see templates/wiki-page.md]

## Links

- **[Label]:** [[path/to/related-page]]
```

### 5. Maintain cross-references

When creating or updating wiki pages, add `[[wikilinks]]` to related pages. If page A references entity B, and page B exists, add a "Related" link on both pages.

### 6. Update index.md

Add any new wiki pages to the appropriate section in `index.md`.

### 7. Update log.md

Append:

```markdown
[YYYY-MM-DD] ingest | Processed raw/<path> → wiki/<entity>.md
```

For batch ingestion, log one line per file processed.

## Rules

1. **Never edit files in `raw/`** — raw is immutable. Read only.
2. **Discuss key takeaways with the operator** before creating wiki pages from ambiguous content. Don't silently interpret.
3. **Preserve existing wiki content** — append new information, never overwrite existing sections.
4. **Cite sources** — every wiki claim should trace back to a raw file.
5. **Keep summaries concise** — wiki pages are reference material, not full reproductions of the source.

## Output

After completion, display:

```
✓ Processed: raw/<path>
✓ Created/Updated: wiki/<entity>.md
✓ Cross-referenced: wiki/<related>.md
✓ Updated index.md
✓ Logged to log.md
```
