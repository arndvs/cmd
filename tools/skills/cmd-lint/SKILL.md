---
name: cmd-lint
description: "Check cmd structural health. Use when asked to 'lint cmd', 'check structure', 'health check', 'audit cmd', or '/cmd lint'."
---

# cmd-lint

Output "Read cmd-lint skill." to chat to acknowledge you read this file.

## Purpose

Check the structural integrity of the cmd repo. Report issues with fix suggestions. Never auto-fix — the operator decides.

## Steps

### 1. Resolve paths

```
CMD_DIR="${CMD_DIR:-$HOME/cmd}"
```

### 2. Run all checks

Execute each check below. Collect issues into a report.

#### Check 1: No files at root

Scan `$CMD_DIR/` for files that aren't in the allowed set:

```
CLAUDE.md, MEMORY.md, index.md, log.md, README.md, .gitignore
```

Any other file at root is a violation.

#### Check 2: No new top-level directories

Scan `$CMD_DIR/` for directories not in the allowed set:

```
raw, wiki, ventures, clients, strategy, cadence, missions, calendar,
content, compute, atlas, templates, tools, archive, research
```

Any other directory at root is a violation (except `.git`, `.obsidian`).

#### Check 3: Orphan wiki pages

Scan `wiki/` for pages that don't reference any `raw/` source file. Pages created by `cmd-init` are exempt (they reference their venture/client directory instead).

#### Check 4: Stale ventures

Scan `ventures/` and `clients/` directories. Cross-reference with `log.md`. Flag any venture/client with zero log mentions in the last 30 days.

#### Check 5: TKTK placeholders

Scan all `.md` files for remaining `TKTK` placeholders. Template files (`_template/`) are exempt.

#### Check 6: index.md sync

Compare wiki pages on disk (`wiki/**/*.md`) against entries in `index.md`. Flag:
- Wiki pages not listed in index.md (missing entries)
- index.md entries pointing to non-existent files (dead entries)

#### Check 7: Empty required files

Check that these files have content beyond their template headers:
- `strategy/objectives.md`
- `strategy/rocks.md`
- `strategy/theme.md`
- `content/voice/samples.md`

If they still contain only TKTK placeholders, flag them as "unpopulated."

#### Check 8: Log format

Scan `log.md` for entries that don't match the expected format:

```
[YYYY-MM-DD] operation | description
```

Skip blank lines, headings (`#`), and HTML comments (`<!-- ... -->`) — these are structural scaffolding, not log entries.

Valid operations: `ingest`, `query`, `compile`, `lint`, `decision`, `build`, `deploy`, `content`, `cadence`

### 3. Generate report

Output the report grouped by severity:

```markdown
## cmd lint report — YYYY-MM-DD

### Errors (must fix)

- ❌ File at root: `stray-file.md` — move to appropriate directory
- ❌ Unknown directory: `misc/` — not in allowed set

### Warnings (should fix)

- ⚠️ Stale venture: `old-project/` — no log activity in 45 days
- ⚠️ TKTK remaining: `strategy/objectives.md` line 12
- ⚠️ Unpopulated: `content/voice/samples.md` — voice-check skill requires this

### Info

- ℹ️ Orphan wiki page: `wiki/concepts/old-topic.md` — no raw source reference
- ℹ️ index.md missing entry: `wiki/people/jane.md`

### Summary

Errors: X | Warnings: Y | Info: Z
```

### 4. Update log.md

Append:

```markdown
[YYYY-MM-DD] lint | Ran structural check — X errors, Y warnings, Z info
```

## Rules

1. **Report, don't fix** — the operator decides what to do with each issue
2. **Template files are exempt** — `_template/` directories are allowed to have TKTK
3. **No false positives** — if the structure is clean, say so: "✓ All checks passed. No structural issues found."
4. **Severity matters** — errors are violations of CLAUDE.md rules; warnings are best-practice gaps; info is nice-to-know

## Output

Display the report inline. If zero issues are found:

```
✓ cmd lint passed — no structural issues found.
```
