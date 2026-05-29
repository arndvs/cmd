---
name: cmd-init
description: "Initialize a new venture or client in cmd. Use when asked to 'init a venture', 'add a venture', 'create a client', 'set up a new project in cmd', or '/cmd init <name>'."
---

# cmd-init

Output "Read cmd-init skill." to chat to acknowledge you read this file.

## Purpose

Scaffold a new venture or client directory from templates, create the wiki entity page, update the index, and log the operation.

## Inputs

The skill takes one required argument: the venture or client name (slug format).

If no argument is provided, ask the operator 4 questions:

1. **Name** — slug for the directory (e.g. `cast`, `acme-corp`)
2. **One-liner** — what this venture/client is in one sentence
3. **Type** — `venture` (something you own) or `client` (paid engagement)
4. **First decision** (optional) — the founding decision to seed `decisions.md`

## Steps

### 1. Resolve paths

```
CMD_DIR="${CMD_DIR:-$HOME/cmd}"
```

Determine the type (venture or client). Default to `venture` if not specified.

### 2. Check for existing directory

If `$CMD_DIR/ventures/<slug>/` or `$CMD_DIR/clients/<slug>/` already exists, ask the operator to confirm before overwriting. Never silently overwrite.

### 3. Copy templates

Copy the appropriate template directory:

- **Venture**: `$CMD_DIR/ventures/_template/` → `$CMD_DIR/ventures/<slug>/`
- **Client**: `$CMD_DIR/clients/_template/` → `$CMD_DIR/clients/<slug>/`

### 4. Populate template files

Replace TKTK placeholders in the copied files:

| Placeholder | Value |
|---|---|
| `TKTK_NAME` | The venture/client name |
| `TKTK_SLUG` | The slug |
| `TKTK_DATE` | Today's date (YYYY-MM-DD) |
| `TKTK_ONELINER` | The one-liner description |

In `README.md`, fill in the name, one-liner, and creation date.

If a first decision was provided, append it to `decisions.md`:

```markdown
## [YYYY-MM-DD] Founded

TKTK_ONELINER

**Decision:** Launch this venture.
**Rationale:** <first decision text>
```

### 5. Create wiki entity page

Create `$CMD_DIR/wiki/ventures/<slug>.md` or `$CMD_DIR/wiki/clients/<slug>.md`:

```markdown
---
type: venture | client
status: active
last_updated: YYYY-MM-DD
---

# <Name>

> <One-liner>

## Summary

TKTK — expand after initial setup.

## Key facts

- **Founded:** YYYY-MM-DD — see [decisions.md](../../ventures/<slug>/decisions.md)

## Links

- **Venture directory:** [ventures/<slug>/](../../ventures/<slug>/)
```

### 6. Update index.md

Add the new wiki page entry under the appropriate section in `$CMD_DIR/index.md`. If a `## wiki/<type>/` header already exists, insert the entry below it. If the header doesn't exist, append a new section:

```markdown
## wiki/ventures/
- <slug>.md — <One-liner>
```

### 7. Update log.md

Append to `$CMD_DIR/log.md`:

```markdown
[YYYY-MM-DD] ingest | Initialized venture: <slug> — <one-liner>
```

### 8. Optionally scaffold ctrl+shft client mapping

Ask the operator: "Do you want to create a ctrl+shft client mapping for this venture?"

If yes:

1. Create `$DOTFILES/clients/<slug>/client.instructions.md` with `cmd-venture: <slug>` in the frontmatter
2. Create `$DOTFILES/clients/<slug>/.projects` — empty, for the operator to add path mappings later

If the operator declines, skip this step.

## Idempotency

- If the venture/client directory already exists, confirm before proceeding
- If the wiki page already exists, update it rather than overwriting
- If the index.md entry already exists, skip the duplicate

## Output

After completion, display:

```
✓ Created ventures/<slug>/
✓ Created wiki/ventures/<slug>.md
✓ Updated index.md
✓ Logged to log.md
```
