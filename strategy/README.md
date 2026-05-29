# strategy/

The operator's strategic direction. Slow-cadence decisions that shape everything downstream.

## Files

- `objectives.md` — 3 quarterly objectives × 3 key results each, plus kill-list
- `rocks.md` — 3 thirteen-week delivery targets with milestones
- `theme.md` — annual direction: what it rules in, what it rules out
- `review.md` — monthly strategic review (5 questions)

## Cascade

Strategy cascades downward:

```
theme.md (annual)
  → objectives.md (quarterly)
    → rocks.md (13-week)
      → cadence/_template/weekly.md (weekly review)
        → cadence/_template/daily.md (daily priorities)
```

Each layer references the layer above. If your daily work doesn't connect to a rock, something is misaligned.

## These are living documents, not templates

`objectives.md` holds your actual objectives. `rocks.md` holds your actual rocks. You edit them in place — you don't copy a template and fill it out. The cadence system (`cadence/_template/`) handles the repeatable review cycle; strategy holds the current state.

## Archive workflow

When a quarter or year ends, archive the outgoing files before updating:

**At quarter boundary:**
1. Copy `objectives.md` → `archive/strategy/YYYY-QN-objectives.md`
2. Copy `rocks.md` → `archive/strategy/YYYY-QN-rocks.md`
3. Fill in the end-of-quarter retrospective in `rocks.md` before archiving
4. Update the living docs for the new quarter

**At year boundary:**
1. Copy `theme.md` → `archive/strategy/YYYY-theme.md`
2. The yearly cadence review produces `cadence/reviews/YYYY-MM-DD-yearly.md` (same destination as all cadence reviews)
3. Update `theme.md` for the new year

**Naming convention:**
```
archive/strategy/
├── 2026-Q3-objectives.md
├── 2026-Q3-rocks.md
├── 2026-Q4-objectives.md
├── 2026-Q4-rocks.md
├── 2026-theme.md
└── ...
```

This preserves full strategic history without bloating the working files. When an AI session needs to reference last quarter's direction, point it at `archive/strategy/`.

## Rules

- **Three objectives max.** More means none get real focus.
- **The kill-list matters as much as the objectives.** What you say no to defines the quarter as much as what you say yes to.
- **Review monthly.** `review.md` is the checkpoint. If you skip it, objectives drift without anyone noticing.
- **Archive before overwriting.** Never lose a quarter's strategic record.
