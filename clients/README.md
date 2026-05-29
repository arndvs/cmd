# clients/

Paid engagements. Same shape as `ventures/`, plus scope and access tracking.

Each client gets a directory with a standard shape. Use `_template/` as the starting point.

## Structure

```
clients/
├── _template/          ← Copy this to start a new client
│   ├── README.md       ← Entry point: name, engagement type, state
│   ├── scope.md        ← What's in scope, what's not
│   ├── access-map.md   ← Who has access to what (no credentials here)
│   ├── decisions.md    ← Append-only decision log
│   ├── timeline.md     ← Chronological activity log
│   └── links.md        ← External URL registry
│
├── my-client/
│   ├── README.md
│   ├── scope.md
│   ├── access-map.md
│   ├── decisions.md
│   ├── timeline.md
│   └── links.md
```

## Rules

- **No credentials in access-map.md.** Document who has access and where credentials are stored — never the credentials themselves.
- **Client deliverables live elsewhere.** This directory holds your operational context, not client-facing work.
- **Scope is a contract with yourself.** Write it clearly so future-you (and AI agents) know what's in bounds.
