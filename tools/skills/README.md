# tools/skills/

AI agent skills that operate on cmd. Each skill is a directory with a `SKILL.md` following the ctrl+shft format.

## Skills

| Skill | Purpose | Status |
|-------|---------|--------|
| `cmd-init` | Initialize a new venture or client | ready |
| `cmd-ingest` | Process raw material into wiki pages | ready |
| `cmd-voice-check` | Validate draft against voice samples and style guide | ready |
| `cmd-cadence` | Execute a cadence rhythm (daily/weekly/monthly/quarterly/yearly) | ready |
| `cmd-lint` | Check structural integrity — orphans, stale ventures, TKTK | ready |
| `cmd-sunday-batch` | Sunday content batch: pick ideas, draft, voice-check | ready |

## Skill format

Each skill directory contains:
- `SKILL.md` — frontmatter (name, description, triggers) + instructions

Skills are registered in ctrl+shft and invoked from any workspace. They read from and write to cmd.
