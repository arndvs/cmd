---
name: cmd-sunday-batch
description: "Sunday content batch: pick ideas, draft posts, voice-check each. Use when asked to 'batch content', 'Sunday batch', 'draft this week's posts', 'content batch', or '/cmd batch'."
---

# cmd-sunday-batch

Output "Read cmd-sunday-batch skill." to chat to acknowledge you read this file.

## Purpose

Pick 5 ideas from the vault, draft each using the appropriate prompt template, voice-check every draft, and produce a ready-to-edit content queue for the week.

## When to run

Sunday afternoon. The goal is to enter Monday with 5 drafted posts that need only operator polish — not creation from scratch.

## Prerequisites

Before running, verify these files have real content (not just TKTK placeholders):

1. `content/voice/samples.md` — at least 10 writing samples
2. `content/ideas/vault.md` — at least 5 tagged ideas
3. `content/prompts/reach-post.md`, `trust-post.md`, `conversion-post.md` — prompt templates

If any prerequisite is missing, stop and tell the operator what to populate first.

## Steps

### 1. Resolve paths

```
CMD_DIR="${CMD_DIR:-$HOME/cmd}"
```

### 2. Triage the inbox

Read `$CMD_DIR/content/ideas/inbox.md`. If it has unprocessed ideas, present them to the operator:

```
Found 3 ideas in inbox. Move any to vault before picking?

1. "That thing about error boundaries nobody talks about"
2. "Why I stopped using Redux"
3. "The $5/mo Cloudflare stack"

Enter numbers to move to vault (e.g. "1,3"), or press Enter to skip.
```

For each idea the operator selects, ask for pillar and type tags, then append to `vault.md` and remove from `inbox.md`.

### 3. Pick 5 ideas

Read `$CMD_DIR/content/ideas/vault.md`. Select 5 unchecked ideas (`- [ ]`) following this distribution:

| Type | Count | Why |
|---|---|---|
| Reach | 2 | Top-of-funnel, draws new audience |
| Trust | 2 | Deep expertise, builds credibility |
| Conversion | 1 | Clear ask, proof of results |

**Selection criteria:**

1. **Pillar balance** — spread across the operator's authority pillars. Don't pick 5 ideas from the same pillar.
2. **Recency** — prefer ideas near the top of the vault (most recently added) unless the operator has starred or prioritized specific ones.
3. **Variety** — avoid 2 posts on closely related topics in the same week.

Present the picks to the operator for approval:

```
Proposed picks for this week:

1. 🎯 Reach — [Engineering] "The 3 things I delete from every PR review"
2. 🎯 Reach — [AI Products] "Why your AI wrapper is a feature, not a product"
3. 🔒 Trust — [Engineering] "How Cast embeds 10K images in 200ms"
4. 🔒 Trust — [Agent Engineering] "Building ctrl+shft: agent config as code"
5. 💰 Conversion — [Agent Engineering] "I built an autonomous coding pipeline. Here's the repo."

Approve? Or swap any picks (e.g. "swap 3 with <vault idea>")
```

Wait for operator approval before drafting.

### 4. Draft each post

For each approved idea:

1. Read the matching prompt template from `content/prompts/`:
   - `#reach` → `reach-post.md`
   - `#trust` → `trust-post.md`
   - `#conversion` → `conversion-post.md`

2. Read voice context:
   - `content/voice/samples.md`
   - `content/voice/style-guide.md`
   - `content/voice/anti-samples.md`

3. Draft the post following the prompt template structure.

4. Write to `$CMD_DIR/content/drafts/YYYY-MM-DD-<slug>.md` with frontmatter:

```markdown
---
idea: "<original idea one-liner>"
pillar: <pillar>
type: <reach|trust|conversion>
drafted: YYYY-MM-DD
status: draft
---

# <Title>

<Draft content>
```

### 5. Voice-check each draft

Run the `cmd-voice-check` skill against each draft. Append the voice-check results as a comment block at the bottom of each draft file:

```markdown
<!-- VOICE CHECK — YYYY-MM-DD
Score: 8/10

Issues:
1. [TONE] Line 5: "Let's dive in" — anti-pattern. → Lead with the specific.
2. [STYLE] Line 12: 38-word sentence. → Split.

What's working:
- Strong hook
- Good proof nouns
-->
```

### 6. Mark vault ideas as drafted

In `vault.md`, check off the 5 picked ideas:

```markdown
- [x] **Engineering** Reach — "The 3 things I delete from every PR review" #reach *(drafted 2026-05-26)*
```

### 7. Generate the batch summary

Display the summary to the operator:

```markdown
## Sunday Batch — YYYY-MM-DD

| # | Type | Pillar | Idea | Voice Score | File |
|---|---|---|---|---|---|
| 1 | Reach | Engineering | "3 things I delete..." | 8/10 | drafts/2026-05-26-delete-from-pr.md |
| 2 | Reach | AI Products | "AI wrapper is a feature..." | 7/10 | drafts/2026-05-26-ai-wrapper.md |
| 3 | Trust | Engineering | "Cast embeds 10K images..." | 9/10 | drafts/2026-05-26-cast-embedding.md |
| 4 | Trust | Agent Eng | "ctrl+shft: config as code..." | 8/10 | drafts/2026-05-26-ctrlshft.md |
| 5 | Conversion | Agent Eng | "Autonomous coding pipeline..." | 7/10 | drafts/2026-05-26-coding-pipeline.md |

### Rationale

1. **"3 things I delete..."** — relatable engineering opinion. Wide reach potential. Counterintuitive angle.
2. **"AI wrapper is a feature..."** — contrarian take in a hot space. High share potential.
3. **"Cast embeds 10K images..."** — technical depth with real numbers. Builds credibility.
4. **"ctrl+shft: config as code..."** — unique IP, nobody else is writing about this. Authority builder.
5. **"Autonomous coding pipeline..."** — ships a repo link. Direct conversion to followers + stars.

### Next steps

- Review each draft in `content/drafts/`
- Address voice-check issues
- Schedule for the week (Mon–Fri)
```

### 8. Update log.md

Append:

```markdown
[YYYY-MM-DD] content | Sunday batch — drafted 5 posts (2 reach, 2 trust, 1 conversion)
```

## Rules

1. **Operator approves picks** — never draft without confirmation of the 5 ideas
2. **2-2-1 distribution is non-negotiable** — 2 reach, 2 trust, 1 conversion. Every week.
3. **Voice-check every draft** — no draft ships without a voice audit
4. **Rationale for each pick** — explain why this idea, this week
5. **Slugs from ideas** — draft filenames derive from the idea, not generic numbers
6. **Don't over-polish** — drafts are 80% done. The operator does the final 20%.

## Output

The batch summary is displayed inline. All draft files are written to `content/drafts/`. The operator reviews, polishes, and schedules.
