# ventures/

Things you own. Ops notes, decisions, and external links — not source code.

Each venture gets a directory with a standard shape. Use `_template/` as the starting point.

## Structure

```
ventures/
├── _template/          ← Copy this to start a new venture
│   ├── README.md       ← Entry point: name, one-liner, audience, state
│   ├── decisions.md    ← Append-only decision log
│   ├── timeline.md     ← Chronological activity log
│   └── _links.md       ← External URL registry (repos, deploys, tools)
│
├── my-venture/
│   ├── README.md
│   ├── decisions.md
│   ├── timeline.md
│   └── _links.md
```

## Rules

- **Code lives elsewhere.** Venture codebases live in their own git repos. Reference them from `_links.md`.
- **One venture = one directory.** Don't nest ventures inside each other.
- **decisions.md is append-only.** Never rewrite a decision. Add a new entry explaining why the direction changed.
