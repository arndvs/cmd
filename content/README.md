# content/

First-class content production system. Voice, ideas, drafts, posts — structured so AI agents produce content that sounds like you, not like ChatGPT.

## Structure

```
content/
├── voice/              ← Your voice definition
│   ├── samples.md      ← 10+ real writing samples (highest-leverage file in cmd)
│   ├── style-guide.md  ← Explicit rules: dos, don'ts, banned phrases
│   └── anti-samples.md ← Examples of what NOT to sound like
│
├── ideas/              ← Idea backlog
│   ├── vault.md        ← Tagged idea backlog with pillar labels
│   └── inbox.md        ← Quick capture — messy is fine
│
├── drafts/             ← Work in progress
├── posts/              ← Published content archive
├── series/             ← Multi-post arcs (content sequences)
│
└── prompts/            ← Prompt templates by content type
    ├── reach-post.md   ← Wide distribution, draws new audience
    ├── trust-post.md   ← Deep expertise, proof nouns, credibility
    └── conversion-post.md ← Clear ask, case study, proof of results
```

## Content types

Three types, balanced across the week:

| Type | Goal | Frequency | Signal |
|------|------|-----------|--------|
| **Reach** | Wide distribution, new audience | 2/week | Impressions, new followers |
| **Trust** | Deep expertise, credibility | 2/week | Saves, shares, DMs |
| **Conversion** | Clear ask, proof of results | 1/week | Replies, inbound, applications |

## Workflow

1. Ideas land in `ideas/inbox.md` (quick capture) or `ideas/vault.md` (tagged backlog)
2. Sunday batch: pick 5 ideas (2 reach, 2 trust, 1 conversion), draft each
3. Voice-check runs against `voice/` before approval
4. Approved drafts queue for publishing
5. Published content archives to `posts/`
6. Multi-post arcs tracked in `series/`

## Rules

- **Voice samples are the highest-leverage file.** Seed with 10+ real samples before running any content skill.
- **Prompt templates are platform-agnostic.** Adapt for LinkedIn, blog, newsletter, etc.
- **Drafts are disposable.** Kill bad drafts. Don't polish mediocre into mediocre.
