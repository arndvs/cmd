# atlas/

Navigation maps and dashboards. Maps of the territory, not the territory itself.

## Purpose

Atlas pages route the reader (or the AI) to the actual entity pages in `wiki/`, `ventures/`, and `clients/`. They answer *"where is everything?"* without duplicating the knowledge that lives elsewhere.

Use this folder for:

- **Top-level navigation** — *"Everything I'm currently working on"*
- **Cross-cutting dashboards** — *"All recurring-revenue clients"*, *"All ventures by status"*
- **Maps of Content (MOCs)** — index pages that link out to wiki entries
- **Relationship views** — how ventures, clients, and people connect to each other

## Why a separate folder

Atlas pages don't belong in `wiki/` because they're not entity pages — they're meta-pages. A wiki page describes *one thing*. An atlas page describes *how things relate*.

## Naming convention

Name files by what they map, not by format:

```
active-engagements.md    ← all ventures + clients by status
content-calendar.md      ← what's scheduled, what's in draft
revenue-map.md           ← recurring revenue by source
tech-stack.md            ← tools, services, and where they're used
```

## Example

```markdown
# Active Engagements

## Ventures (mine)
- [[venture-a]] — building, active
- [[venture-b]] — paused
- [[venture-c]] — building, active

## Clients (paid)
- [[client-x]] — active retainer
- [[client-y]] — contract

## On deck
- [[venture-d]] — scoping
```

Links via `[[wikilinks]]` so Obsidian renders the graph.

## Rules

1. **Navigation only.** Atlas pages link and summarize status — the knowledge lives in `wiki/`, `ventures/`, and `clients/`.
2. **Keep current.** Update atlas pages when ventures or clients change state. Stale maps are worse than no map.
3. **Use `[[wikilinks]]`** to reference wiki pages so the graph stays connected.
4. **Don't duplicate.** If you're writing more than a one-line summary per entry, the detail belongs in the entity page, not here.


