# Wiki Page

> Template for `wiki/` entity pages. All four types share the same bones — type-specific sections go in the middle.

---

## Structure

```markdown
---
type: venture | client | person | concept
status: active | paused | archived
last_updated: YYYY-MM-DD
---

# [Name]

> [One-line tagline — what this is in ≤15 words]

## Summary

[2-3 sentences. What an AI session needs to know in 10 seconds.]

## Key facts

- **[Field]:** [value]
- **[Field]:** [value]

## [Type-specific sections — see below]

## Links

- **[Label]:** [[path/to/related-page]]
```

---

## Type-specific sections

### venture

- **Architecture** — how it's built
- **Key differentiators** — what makes it different

### client

- **Key people** — contacts with wikilinks to `wiki/people/`
- **Active work** — current scope or retainer activity

### person

- **Context** — relationship history, how you met, last interaction

### concept

- **The pattern** — what the concept is
- **Why it matters** — why it's worth a wiki page
- **Where it's used** — concrete implementations
- **Related** — wikilinks to connected pages

---

## Rules

- **Frontmatter is required.** `type`, `status`, `last_updated` — every page gets all three.
- **Summary is the hook.** If the summary doesn't tell an AI session what it needs in 10 seconds, rewrite it.
- **Key facts use bold labels.** Consistent formatting makes grep and AI parsing reliable.
- **Wikilinks connect the graph.** Every page should link to at least one other wiki page. Orphan pages are dead pages.
- **Don't over-structure.** Add sections only when you have content for them. An empty "Architecture" section is worse than no section.
