# cmd

> A markdown-first, AI-navigable business operating system. Strategy, ventures, content, knowledge — structured so your AI agents understand your business as well as you do.

cmd is the operational companion to [ctrl+shft](https://github.com/arndvs/ctrlshft). ctrl+shft configures how agents code; cmd configures what agents know about your business. Together: **ctrl+shft+cmd**.

---

## What it is

A folder you build your business out of. Plain markdown, opinionated structure, git-versioned. One operator, AI agents, the same knowledge base both navigate.

It's not a SaaS. Clone it, drop it in your home directory, and it becomes the context layer for every AI session you run. Switch models, switch tools — the folder still works.

## Why it exists

When AI output feels junior, the diagnosis is almost always junior context. Not a junior model — a junior context window.

cmd is how you give your AI senior context. Put your strategy, decisions, voice, and active ventures into a structure your AI can read, and every prompt gets dramatically better.

## What's inside

```
~/cmd/
├── CLAUDE.md           ← Schema layer — you author this
├── MEMORY.md           ← AI-maintained observations
├── index.md            ← Machine-maintained catalog of wiki/ pages
├── log.md              ← Append-only activity log
│
├── raw/                ← IMMUTABLE source material (you add, AI reads)
├── wiki/               ← AI-COMPILED knowledge (AI maintains, you review)
│
├── ventures/           ← Things you own (ops + decisions, not code)
├── clients/            ← Paid engagements
│
├── strategy/           ← Objectives, rocks, themes, reviews
├── cadence/            ← Daily / weekly / monthly / quarterly / yearly rhythms
├── missions/           ← Context sidecars for PM tickets (optional)
├── calendar/           ← Daily notes, journal (human-authored)
├── content/            ← Content engine — voice, ideas, drafts, posts
│
├── compute/            ← Active infrastructure catalog
│   └── stacks.md
│
├── atlas/              ← Navigation maps + dashboards
├── templates/          ← Reusable patterns
├── tools/              ← Scripts + skills
└── archive/            ← Old / done / deprecated
```

## Quick start

```bash
git clone https://github.com/arndvs/cmd.git ~/cmd
cd ~/cmd
# Open in Claude Code, Cursor, or any AI tool that reads CLAUDE.md
```

The AI reads `CLAUDE.md` first and immediately knows how to navigate.

### With ctrl+shft (recommended)

If you run [ctrl+shft](https://github.com/arndvs/ctrlshft), cmd integrates automatically. Add `cmd-venture: <slug>` to your `client.instructions.md` files and ctrl+shft routes venture context into every coding session.

### Without ctrl+shft

cmd works standalone. Open `~/cmd/` in any AI tool with filesystem access. The folder structure and `CLAUDE.md` are self-documenting.

## How to work in here

Six operations, inherited from [Karpathy's filesystem-as-AI-interface](https://karpathy.ai) pattern and extended for operators:

| Operation | What happens |
|-----------|-------------|
| **Ingest** | New material lands in `raw/`. AI summarizes, creates/updates `wiki/` pages, logs to `log.md` |
| **Query** | You ask a question. AI searches `wiki/` and `raw/` first, synthesizes with citations |
| **Compile** | Periodic rebuild of `wiki/` from `raw/`. Cross-references maintained |
| **Lint** | Structural health check. Files in wrong places, orphan pages, stale entries |
| **Build** | Spin up scripts in `tools/`, scaffold ventures, create content |
| **Deploy** | Push artifacts to your cloud (Cloudflare, etc.) — optional compute layer |

## How to extend

- **Add ventures:** `ventures/<name>/` with `README.md` + `decisions.md` + `links.md`
- **Add clients:** `clients/<name>/` — same shape, different relationship
- **Add wiki entities:** drop a markdown file in `wiki/ventures/`, `wiki/people/`, etc.
- **Add templates:** reusable patterns in `templates/`
- **Add skills:** Claude Skills in `tools/skills/<name>/SKILL.md`

## What's NOT in here

- **No credentials.** Secrets live outside the repo. Always. See the "Rules" section in `CLAUDE.md`.
- **No project code.** Venture codebases live in their own repos, referenced from `ventures/<name>/links.md`.
- **No proprietary formats.** Plain markdown in version control beats every knowledge base SaaS.

## Compute layer (optional)

cmd works as pure local markdown. For operators who want to catalog their running infrastructure, the `compute/` directory tracks technology stacks, deployed services, and active agents. No code lives here — deployable applications belong in their own repos. See `compute/README.md` for details.

## License

MIT. Fork it, customize it, ship on top of it.

## Credits

Structure inspired by [Andrej Karpathy](https://karpathy.ai)'s filesystem-as-AI-interface thinking, [Max Ship](https://github.com/shipwithmax/command)'s Command Kit, and [Peter Naur](https://pages.cs.wisc.edu/~remzi/Naur.pdf)'s *Programming as Theory Building*.
