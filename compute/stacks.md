# Stacks Overview

> The technology bundles you actually run. One section per stack.
> When a stack grows complex enough, spin it out to its own file and link from here.

## Conventions

- One stack = one section
- For each stack: **name**, **what it does**, **tools in the bundle**, **what depends on it**, **last reviewed** date
- Mark deprecated stacks with `~~strikethrough~~` until you remove them — captures history

---

## Cloudflare Edge Stack

**What it does:** Hosting + edge compute + database + storage + auth + email routing.

**Tools in the bundle:**
- Cloudflare Workers (hosting + edge functions)
- Cloudflare D1 (SQLite at the edge)
- Cloudflare R2 (object storage)
- Cloudflare Pages (static sites — evaluate migration to Workers Sites)
- Cloudflare Access (auth gating for internal tools)
- Cloudflare Email Routing (email forwarding for custom domains)

**What depends on it:**
- TKTK (list ventures/sites deployed here)

**Last reviewed:** TKTK

---

## AI Coding Stack

**What it does:** Where prompts become shipped code. The agents, IDEs, and integrations that do the building.

**Tools in the bundle:**
- Claude Code (Anthropic CLI agent — primary)
- VS Code Copilot (GitHub Copilot in VS Code Insiders — secondary)
- ctrl+shft (agent configuration layer — skills, personas, hooks, instruction tiers)
- MCPs: Linear, GitHub, Cloudflare, Stripe, Sanity, GoHighLevel, Tavily

**What depends on it:**
- Every shipped change across all ventures

**Last reviewed:** TKTK

---

## Content Production Stack

**What it does:** Content creation, adaptation, and distribution pipeline.

**Tools in the bundle:**
- TKTK (list your actual content tools — video, social scheduling, newsletter, etc.)

**What depends on it:**
- Weekly content cadence

**Last reviewed:** TKTK

---

## (Add your other stacks below)

Spin out a section per stack you actively run. Keep this honest — only what's actually running, not what you considered.
