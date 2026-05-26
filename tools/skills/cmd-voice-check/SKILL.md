---
name: cmd-voice-check
description: "Validate a draft against voice samples and style guide. Use when asked to 'voice check', 'check my voice', 'review this draft', 'does this sound like me', or '/cmd voice-check <path>'."
---

# cmd-voice-check

Output "Read cmd-voice-check skill." to chat to acknowledge you read this file.

## Purpose

Compare a content draft against the operator's voice samples, style guide, and anti-samples. Flag specific issues and suggest targeted edits — not a full rewrite.

## Inputs

- **Draft path** — path to the draft file (typically in `content/drafts/`)

## Steps

### 1. Load voice context

```
CMD_DIR="${CMD_DIR:-$HOME/cmd}"
```

Read these files in order:

1. `$CMD_DIR/content/voice/samples.md` — the operator's real writing examples
2. `$CMD_DIR/content/voice/style-guide.md` — explicit dos, don'ts, rules
3. `$CMD_DIR/content/voice/anti-samples.md` — patterns to avoid

If `samples.md` is empty or contains only TKTK placeholders, **stop and tell the operator**: "Voice samples are empty. Populate `content/voice/samples.md` with 10+ real writing examples before running voice-check. Without samples, this skill produces generic feedback."

### 2. Read the draft

Read the draft file. Note its content type if tagged (reach, trust, conversion).

### 3. Run the voice audit

Compare the draft against voice context. Check for these categories:

#### Tone match
- Does the draft sound like the voice samples?
- Are sentence lengths consistent with the operator's style?
- Is the energy level right (e.g. punchy vs. measured)?

#### Style guide compliance
- Any violations of explicit dos/don'ts from the style guide?
- Any banned phrases or patterns present?

#### Anti-pattern detection
- Does any passage match the anti-samples?
- Generic AI tone markers: "In today's fast-paced world", "Let's dive in", "Here's the thing", "game-changer", "leverage", "utilize", "in conclusion"
- Excessive hedging: "I think", "it seems", "perhaps", "might"
- LinkedIn-isms: "I'm humbled", "Agree?", "Thoughts?", "Who else?"

#### Structure check
- Does it have a hook in the first line?
- Are there proof nouns (specific names, numbers, tools) vs. vague adjectives?
- Is the CTA clear (if applicable)?
- Is it the right length for the content type?

### 4. Produce the report

Output a structured report — **not a rewrite**:

```markdown
## Voice Check: <draft-filename>

### Score: X/10

### Issues

1. **[TONE]** Line 3: "Let's dive into..." — matches anti-sample pattern.
   → Suggestion: Lead with the specific thing. "Cast indexes 40M assets in 200ms."

2. **[STYLE]** Line 7: Sentence is 42 words — operator average is 12.
   → Suggestion: Split into 2-3 sentences.

3. **[ANTI-PATTERN]** Line 15: "game-changer" — banned phrase.
   → Suggestion: Replace with specific outcome.

### What's working

- Strong hook in line 1
- Good proof noun density (3 specific references)
- Matches operator energy level

### Summary

3 issues found. Draft is close — targeted edits, not a rewrite.
```

### 5. Do NOT rewrite

The output is always a diff-style report with line-specific suggestions. Never produce a full rewrite unless the operator explicitly asks for one after reviewing the report.

## Rules

1. **Voice samples are required** — refuse to run without populated samples
2. **Line-specific feedback** — every issue cites a line number and exact text
3. **Suggestions, not rewrites** — show what to change and why
4. **Acknowledge what's working** — the report includes positives, not just negatives
5. **No false positives** — if the draft matches the voice, say so. Don't manufacture issues

## Output

The voice check report is displayed inline. It is NOT written to a file unless the operator requests it.
