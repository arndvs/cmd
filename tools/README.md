# tools/

Automation that operates on cmd — skills, scripts, and integrations.

## Structure

```
tools/
├── skills/         ← AI agent skills (ctrl+shft SKILL.md format)
│   └── README.md
└── README.md
```

## Rules

- **Skills live in `tools/skills/<name>/SKILL.md`.** Follow the ctrl+shft skill format with YAML frontmatter.
- **Scripts that automate cmd operations** (cadence-run, content-batch, etc.) live here.
- **MCPs and agent configs live in ctrl+shft.** This directory is for cmd-specific automation only.
