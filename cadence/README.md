# cadence/

Operational rhythms. The clock that keeps strategy connected to daily work.

Five cadences run in parallel — daily build, weekly review, monthly retrospective, quarterly strategy, yearly retrospective. Skip any of them and the work stops compounding.

## Structure

```
cadence/
├── README.md             ← You are here (doctrine — why + how)
├── _template/            ← Fillable checklists (copy to reviews/ when running a cadence)
│   ├── daily.md
│   ├── weekly.md
│   ├── monthly.md
│   ├── quarterly.md
│   └── yearly.md
└── reviews/              ← Completed review docs (append-only)
    └── YYYY-MM-DD-<freq>.md
```

## How cadences stack

Each cadence feeds the next. Daily ships are inputs to the weekly review. Four weekly reviews stack into a monthly retrospective. Three monthly retrospectives stack into a quarterly with real signal — not vibes. Four quarters become the yearly retrospective. Skip a cadence and the rollups become hollow.

Most operators only run two of the five (usually daily + weekly). The compounding lives in the slower ones.

## How to run a cadence

1. Copy the template from `_template/<freq>.md`
2. Save to `reviews/YYYY-MM-DD-<freq>.md`
3. Fill it out
4. Template stays clean for next time

---

## Daily — the build cadence

> The smallest rhythm. Orient, ship, log.

### Morning scan (first 30 min)

Before you ship anything, orient.

- Pull latest across active repos
- Quick scan — new messages, orders, alerts?
- KPI gauge: today vs yesterday vs rolling 7-day average
- Set today's priorities — what's the one thing that moves a rock forward?

The point isn't to absorb every detail. The point is to know the shape of the day before you start.

### What to ship next

Decide using a triangle:

1. **Bug reports / fires** — does anything need stopping today?
2. **Blocked work** — what's blocking a client deliverable or a venture?
3. **Your priorities** — the directional bets only you can make

If two of three are quiet, focus on the third. Shipping with no direction is the failure mode to watch for.

### Build block

Lock in. This is when you ship.

- At least 1 meaningful PR or deliverable
- Look for things to delete as readily as things to add
- Improve a tool or pattern you use repeatedly
- Check: is what I'm building connected to a rock?
- Check that daily/weekly automation loops are still running clean

### Before noon vs after

Mornings are the scan, the planning, the meetings if any. Afternoons are focused shipping. Don't do meta-work after noon — that's when the build block matters most.

### EOD ritual (15 min)

The most important 15 minutes of the day.

- Log everything meaningful to `log.md` — one line per action
- Update any venture/client timelines that changed
- Ensure every meaningful action has a PM ticket with rich detail
- Fill out the daily review (`_template/daily.md` → `reviews/`)
- Review tomorrow's PM queue — edit priorities before bed, not after coffee
- Close laptop. Walk away.

### Why daily matters

`log.md` (and your PM tool, when active) becomes the journal of the work done. Months later, you can ask "when did I add that? why?" — and there's an entry with the answer. The discipline at end-of-day is what makes the knowledge base possible at all.

---

## Weekly — content + review

> The minimum viable rhythm. If you skip everything else, don't skip this.

### Weekly review (end of week, 30 min)

Five questions, written down:

1. **What shipped?** — list the actual artifacts (PRs, posts, deliverables)
2. **What didn't?** — and why
3. **What's blocked?** — what needs unblocking next week
4. **What surprised me?** — the unexpected signal worth tracking
5. **What rolls forward?** — concrete carryovers to next week

### Content check

- How many pieces shipped this week?
- What type? (reach / trust / conversion)
- Is the balance right? (target: 2 reach, 2 trust, 1 conversion)
- What's queued for next week?

### Content pipeline

Always rolling, always feeding the content engine:

- Video or recording → turn into 2-3 short clips
- Essay or field report → adapt to LinkedIn post + Twitter thread
- Raw insights from the week → captured as `content/ideas/inbox.md` entries
- Watch what's being read, who's reading it, how often — double down on signal

There are many idea-to-output paths. Flexibility now, double down on what analytics show is working.

### Feedback into Command

After the weekly review, type three things into the relevant wiki page or `CLAUDE.md`:

1. What worked this week and should be reinforced
2. What didn't work and should be avoided next time
3. What I learned about the customer, market, or myself that wasn't there last week

Three sentences. That's it. Now the next AI session runs on a sharper Command. Multiply by 50 weeks a year. That's how compounding works.

### Why weekly matters

The five review questions force you to name what happened — not what you think happened. Over time, the gap between those two things is where the real learning lives.

---

## Monthly — strategic checkpoint

> Zoom out. Weekly handles the work; monthly handles whether the work is the right work.

### Monthly checklist

- Run the monthly strategic review (`strategy/review.md`)
- Content retrospective — what landed this month? What flopped?
- Financial scan — burn rate, revenue, vendor costs
- System improvements — what should be automated that still isn't?
- Security review — secrets rotation if needed, dependency audit

### Strategic check (15 min, written)

Ask the questions weekly is too busy to ask:

1. **Is what I'm shipping aligned with this quarter's bets?** — if no, why
2. **What pattern is repeating that I haven't named yet?** — three weeks of the same friction = the system, not the day
3. **What did I say I'd do last month and didn't?** — kill it or commit to it. No third option

### Why monthly matters

The strategic check catches drift before it compounds — three months of the wrong direction is expensive, one month is recoverable.

---

## Quarterly — the strategic muscle

> Set direction. The strategic work nobody else can do.

### Quarterly checklist

- **Retrospective** — last quarter's rocks vs results. Not "did I feel productive" — did the metrics move?
- **Big milestones** — what 3 things would make this year a hit? Am I tracking toward them?
- **OKR setting** — 3 objectives, 3 key results each. Update `strategy/objectives.md`
- **Rock definition** — 3 thirteen-week targets. Update `strategy/rocks.md`
- **Kill-list** — what to stop doing. The hardest move
- **Content brief** — editorial direction for the next 13 weeks

### The five strategic questions

1. **What's working that I should double on?**
2. **What's not working that I should kill?**
3. **What did I learn that I hadn't planned to?**
4. **What relationship deepened that I should invest in?**
5. **What did I say I'd do that I didn't — and what's the honest reason?**

### Why quarterly matters

Weekly is too close to the work. Monthly catches drift. But quarterly is where you ask: are these the right bets? Skip it and the year-end review becomes vibes.

---

## Yearly — the retrospective

> The slowest rhythm and the one most operators skip. Don't.

A deep review — not a quick summary. 10+ hours of reflection across voice notes, writing, and conversation. Answer these across every venture:

### Wins
- What shipped that exceeded expectations?
- Which bets paid off — skill or luck?
- Which relationships compounded?
- What discipline held all year?

### Losses
- What shipped that flopped — and why?
- Which bets failed — bad bet or bad execution?
- What relationships unraveled?
- What discipline broke when things got busy?

### Learning
- What pattern showed up across multiple ventures?
- What customer surprise reshaped how I think?
- What new tool or methodology changed my work this year?

### Key partners
- Who showed up for me? How do I deepen that?
- Who didn't? What's the honest read of why?

### Per-venture assessment
- Per venture: what's compounding, what's draining?
- Per venture: what stays, what gets paused, what gets killed?

### Finance
- Revenue, burn, runway (where applicable)
- Cost / vendor review
- ROI on big bets — labor and capital

### The output

Produce a finalized review document formatted for AI consumption. Drop it in `cadence/reviews/YYYY-MM-DD-yearly.md` (same destination as all cadence reviews). Next year, every AI session has this context. This year's review becomes next year's strategy input. That's the compound.

### Set the next year

- **Annual theme** — one frame that holds the year. Update `strategy/theme.md`
- **3 big bets** — ventures or initiatives that change the shape if they hit
- **Admin chores** — schedule tax, legal, compliance into the calendar

### Why yearly matters

Most operators running quarterly cadence skip yearly because "it's just four quarterlies." It isn't. Yearly is where you ask: what kind of operator am I becoming? Quarterly can't answer that — too close to the rotor blades.

---

## Rules

- **Don't skip weekly.** It's the minimum viable cadence. Everything else is optional but weekly is not.
- **Reviews go in `reviews/`.** Named by convention: `YYYY-MM-DD-<freq>.md` (e.g. `2026-05-29-daily.md`, `2026-05-29-weekly.md`, `2026-05-29-monthly.md`, `2026-05-29-quarterly.md`, `2026-05-29-yearly.md`).
- **Templates are starting points.** Edit them to fit your rhythm. The structure is a scaffold, not a contract.
