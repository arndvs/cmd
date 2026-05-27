# CLAUDE.md — cmd schema

> The schema layer for `cmd` — a markdown-first business operating system built for a human operator and AI agents.
>
> Claude (or any AI tool with filesystem access) reads this first to know where files go, how to navigate, and what operations are available.

---

## Structure

```
cmd/
├── CLAUDE.md           ← You are here (schema layer — operator authors)
├── MEMORY.md           ← Auto-memory (AI maintains)
├── index.md            ← Machine-maintained catalog of wiki/ pages
├── log.md              ← Append-only activity log — one line per operation
│
├── raw/                ← IMMUTABLE source material (you add, AI reads, never edits)
│   ├── articles/       ← Research docs, web clips, agreements
│   ├── transcripts/    ← Meeting transcripts, voice notes
│   ├── screenshots/    ← Images, design inspiration, competitor screenshots
│   ├── uploads/        ← Files dropped here for AI context
│   └── data/           ← CSVs, JSON exports, datasets
│
├── wiki/               ← AI-COMPILED knowledge (AI maintains, you review)
│   ├── ventures/       ← One entity page per venture you own
│   ├── clients/        ← One entity page per paid client
│   ├── people/         ← One entity page per person in your orbit
│   └── concepts/       ← Cross-cutting topics, syntheses, research
│
├── ventures/           ← Things you own — ops, decisions, links (not code)
├── clients/            ← Paid engagements — scope, access, decisions
│
├── strategy/           ← Quarterly objectives, 13-week rocks, annual themes
├── cadence/            ← Rhythms — daily, weekly, monthly, quarterly, yearly
│   ├── _template/      ← Fillable checklists (copy to reviews/ when running a cadence)
│   └── reviews/        ← Completed review documents
├── missions/           ← Context sidecars for PM tickets (optional)
├── calendar/           ← Daily notes, journal (human-authored)
│
├── compute/            ← Active infrastructure — stacks, deployed services, agents
│   └── stacks.md
│
├── content/            ← Content engine
│   ├── voice/          ← Voice samples, style guide, anti-patterns
│   ├── ideas/          ← Idea vault + inbox
│   ├── drafts/         ← Work in progress
│   ├── posts/          ← Published content archive
│   ├── series/         ← Multi-post arcs
│   └── prompts/        ← Prompt templates by content type
│
├── atlas/              ← Navigation maps + dashboards (MOCs)
├── templates/          ← Reusable patterns (meeting notes, decisions, etc.)
├── tools/              ← Reusable scripts, utilities, AI skills
│   └── skills/         ← Claude Skills — invokable workflows
└── archive/            ← Deprecated, completed, or one-off material
    ├── strategy/       ← Past quarters' objectives, rocks, and themes
    ├── ventures/       ← Paused or killed ventures
    ├── clients/        ← Completed engagements
    ├── concepts/       ← Superseded wiki concepts
    └── people/         ← Inactive contacts
```

---

## File placement decision tree

When creating or saving a new file:

```
Is it source material (PDF, transcript, screenshot, CSV, raw doc)?
  → raw/  (pick: articles, transcripts, screenshots, uploads, or data)

Is it compiled knowledge (summary, entity page, research synthesis)?
  → wiki/  (pick: ventures, clients, people, or concepts)

Is it operational context for something you own?
  → ventures/<name>/

Is it operational context for a paid engagement?
  → clients/<name>/

Is it strategic direction (objectives, rocks, themes)?
  → strategy/

Is it a cadence template or rhythm?
  → cadence/

Is it a PM ticket that needs context the PM tool can't hold?
  → missions/  (must link to a PM ticket)

Is it a daily note or journal entry?
  → calendar/  (one file per day, human-authored)

Is it about running infrastructure, deployed services, or technology stacks?
  → compute/

Is it content-related (voice, ideas, drafts, posts)?
  → content/  (pick the right subfolder)

Is it a navigation/dashboard page?
  → atlas/

Is it old, done, or one-off?
  → archive/

None of the above?
  → Ask the operator where it should go.
```

**NEVER place new files at the repo root.** Only these files live at root: `CLAUDE.md`, `MEMORY.md`, `index.md`, `log.md`, `README.md`, `.gitignore`.

**NEVER create new top-level directories without the operator's approval.** The set is fixed for portability across machines, AI tools, and future-you.

---

## The six operations

### Ingest
When the operator adds new source material to `raw/`:
1. Read the new source.
2. Discuss key takeaways with the operator.
3. Create or update relevant `wiki/` pages (entity pages, concept pages).
4. Update `index.md` with new/changed wiki pages.
5. Append a log entry to `log.md`.

### Query
When the operator asks a question against the knowledge base:
1. Search relevant `wiki/` and `raw/` pages first.
2. Synthesize answer with citations to specific files.
3. If the answer produces valuable new knowledge, create a wiki page for it.

### Compile
Periodically rebuild or update wiki pages from raw sources:
1. Read from `raw/` (articles, transcripts, data).
2. Build/update structured `wiki/` pages — entity pages, concept syntheses.
3. Maintain cross-references with `[[wikilinks]]`.
4. Update `index.md`.

### Lint
Check structural health periodically:
1. Find files in wrong locations.
2. Find orphan files not in `index.md`.
3. Find stale wiki pages (no raw source reference).
4. Find ventures with no log activity in 30+ days.
5. Find TKTK placeholders still present.
6. Report issues with suggested fixes — do not auto-fix.

### Build
The operator says "build me a thing." The AI reads `CLAUDE.md` + relevant `wiki/` pages, then:
1. Scaffolds in `tools/` or `ventures/<name>/`.
2. Writes a `decisions.md` entry capturing what was built and why.
3. Logs to `log.md`.

### Deploy
For cloud-side artifacts (Workers, scheduled jobs, etc.):
1. Execute deploy from inside the folder.
2. Capture the live URL or status in `ventures/<name>/links.md`.
3. Log to `log.md` with the deploy timestamp.

---

## Content engine

The `content/` directory is a first-class content production system.

### Voice
- `content/voice/samples.md` — 10+ real writing samples that define your voice. **This is the highest-leverage file in cmd.** Without good voice samples, every content skill produces generic output.
- `content/voice/style-guide.md` — explicit rules (dos, don'ts, banned phrases).
- `content/voice/anti-samples.md` — examples of what your writing should NOT sound like.

### Content types
Three types, balanced across the week:
- **Reach** — wide distribution, accessible, draws new audience
- **Trust** — deep expertise, proof nouns, technical credibility
- **Conversion** — clear ask, case study, proof of results

### Workflow
1. Ideas land in `content/ideas/inbox.md` (quick capture) or `content/ideas/vault.md` (tagged backlog)
2. Drafts move to `content/drafts/<slug>.md`
3. Voice-check runs against `content/voice/` before approval
4. Published content archives to `content/posts/<slug>.md`
5. Multi-post arcs tracked in `content/series/`

### Prompt templates
`content/prompts/` contains prompt templates for each content type. Platform-agnostic — adapt for LinkedIn, blog, newsletter, etc.

---

## Strategy layer

The `strategy/` directory holds the operator's strategic direction:

- `objectives.md` — 3 quarterly objectives × 3 key results each. Plus the kill-list (what's NOT an objective).
- `rocks.md` — 3 thirteen-week delivery targets with week-level milestones.
- `theme.md` — annual direction. What it rules in, what it rules out, 3 big bets.
- `review.md` — monthly strategic review (5 questions).

Strategy cascades: theme → objectives → rocks → weekly cadence. Each layer references the layer above.

---

## Cadence layer

The `cadence/` directory holds operational rhythms:

- `daily.md` — morning scan + build block + EOD ritual
- `weekly.md` — 5 review questions, content shipped, carryovers
- `monthly.md` — strategic alignment check, pattern spotting
- `quarterly.md` — OKR setting, rock definition, kill-list
- `yearly.md` — full retrospective, theme setting, big bets

Reviews generated by cadence skills land in `cadence/reviews/YYYY-MM-DD-<freq>.md`.

---

## Skills — invokable workflows

`cmd` ships with Claude Skills in `tools/skills/`. Each skill is a self-contained workflow the AI invokes when the operator asks for it. Read `tools/skills/<skill-name>/SKILL.md` for instructions.

Invoke a skill by phrasing — "run the X skill", "use X to do Y", or just describing the task. Match the closest skill from `tools/skills/` and follow the SKILL.md instructions.

### ctrl+shft integration

If you run [ctrl+shft](https://github.com/arndvs/ctrlshft), cmd skills are discovered automatically via symlinks in `~/dotfiles/skills/_local/`. The `/cmd` slash command dispatches to cmd skills from any workspace.

---

## index.md maintenance

`index.md` is a machine-maintained catalog. Format:

```markdown
# Index

## wiki/ventures/
- example-venture.md — One-line description

## wiki/clients/
- example-client.md — One-line description

## wiki/concepts/
- example-concept.md — One-line description

## wiki/people/
- example-person.md — Role + relationship
```

Update `index.md` after every Ingest or Compile operation. Keep it under 200 lines.

---

## log.md maintenance

Append-only. One line per operation. Newest entries at the bottom.

```markdown
[YYYY-MM-DD] operation | description
```

Operations: `ingest` · `query` · `compile` · `lint` · `decision` · `build` · `deploy` · `content` · `cadence`

Example:

```markdown
[2026-05-26] ingest | Added meeting transcript with potential client
[2026-05-27] compile | Built venture entity page from raw sources
[2026-05-28] deploy | Pushed v0.1 of publish-post worker to Cloudflare
[2026-05-29] content | Drafted 5 posts for week of June 2
```

---

## Rules — non-negotiable

1. **No new files at root.** The root set is fixed.
2. **No new top-level directories** without explicit operator approval.
3. **Append-only for logs and decisions.** Never rewrite history.
4. **Markdown first.** No proprietary formats for knowledge.

---

## ctrl+shft composition

cmd is the operational layer. [ctrl+shft](https://github.com/arndvs/ctrlshft) is the agent configuration layer. They compose:

| ctrl+shft owns | cmd owns |
|----------------|----------|
| Agent config, rules, secrets, shell hooks | Business knowledge, strategy, content, ops |
| `detect-context.sh`, `.env.agent`, skills | `wiki/`, `ventures/`, `strategy/`, `content/voice/` |

Runtime wiring:
- `CMD_DIR` env var (set in `.env.agent`) → tells scripts where cmd lives
- `detect-context.sh` → adds `cmd` context when working inside `$CMD_DIR`
- `cmd-venture:` field in `client.instructions.md` → bridges a client to a cmd venture folder
- cmd skills follow ctrl+shft SKILL.md format → symlink into `~/dotfiles/skills/_local/` for cross-discovery

Neither system requires the other. Both are better together.

---

*Schema v0.1 · MIT*
