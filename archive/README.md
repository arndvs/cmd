# archive/

Deprecated, completed, or one-off material. Where finished work goes to rest.

## Structure

```
archive/
├── strategy/       ← Past quarters' objectives, rocks, and annual themes
├── ventures/       ← Paused or killed ventures
├── clients/        ← Completed engagements
├── concepts/       ← Superseded wiki concepts
└── people/         ← Inactive contacts
```

## Rules

- Move items here instead of deleting. Git history preserves everything, but archive/ keeps the active directories clean.
- Preserve the original directory structure: `archive/ventures/old-thing/`, `archive/clients/old-client/`.
- Add a one-liner at the top of archived files explaining why it was archived and when.

## Strategy archive

Strategy files are living documents that get overwritten at quarter/year boundaries. Archive the outgoing version first:

- **Quarterly:** `archive/strategy/YYYY-Q_-objectives.md`, `archive/strategy/YYYY-Q_-rocks.md`
- **Yearly:** `archive/strategy/YYYY-theme.md`

See `strategy/README.md` for the full archive workflow.
