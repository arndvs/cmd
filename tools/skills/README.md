# tools/skills/

AI agent skills that operate on cmd. Each skill is a directory with a `SKILL.md` following the ctrl+shft format.

## Planned skills

| Skill | Purpose | Status |
|-------|---------|--------|
| `cmd-init` | Initialize a new cmd instance for a venture | planned |
| `ingest` | Process raw material into wiki + idea entries | planned |
| `voice-check` | Validate draft against voice samples and style guide | planned |
| `cadence-run` | Execute a cadence rhythm (daily/weekly/monthly/quarterly) | planned |
| `lint` | Check structural integrity — broken links, empty templates, stale dates | planned |

## Skill format

Each skill directory contains:
- `SKILL.md` — frontmatter (name, description, triggers) + instructions

Skills are registered in ctrl+shft and invoked from any workspace. They read from and write to cmd.
