# missions/

Context sidecars for project management tickets. One file per active mission.

> **Optional.** This directory is useful if you use a PM tool (Linear, Todoist, Notion, etc.). If you track work directly in `ventures/` and `clients/`, skip this.

## Why this exists

PM tools track status, assignment, and due dates. They don't hold the "why" — the strategic context, the decisions that shaped the approach, the links to `raw/` material that informed the work. Mission files bridge that gap.

## Structure

```
missions/
├── README.md           ← You are here
├── PROJ-42-short-name.md
├── PROJ-43-short-name.md
└── ...
```

**Naming convention:** `<ticket-id>-<slug>.md` — e.g., `CMD-12-wiki-buildout.md`

## What goes in a mission file

- Link back to the PM ticket (required)
- Strategic context: which rock or objective this serves
- Decisions made during execution
- Links to `raw/` source material
- Notes the PM tool can't hold

## What does NOT go here

- Status updates (that's your PM tool's job)
- Task breakdowns (that's your PM tool's job)
- Deliverables or artifacts (those go in `ventures/` or `clients/`)

## Lifecycle

1. **Create** when a ticket needs context beyond what the PM tool holds
2. **Update** as decisions are made during execution
3. **Archive** when the ticket closes — move to `archive/missions/`

Not every ticket needs a mission file. Only create one when there's context worth preserving.

## How AI uses this folder

When you ask "what's the context on PROJ-42?" — the AI reads the mission file, follows links to `raw/` sources and wiki pages, and gives you the full picture. When running the daily brief, active missions surface alongside `log.md` and venture status.

## Rules

- **Every mission file must link to its PM ticket.** A mission without a ticket link is an orphan.
- **Don't duplicate your PM tool.** If it's in the PM tool, don't repeat it here. This is for what the tool can't hold.
- **Archive, don't delete.** When a mission closes, move the file to `archive/missions/`.
