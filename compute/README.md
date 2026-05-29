# compute/

What's actually running for you. Every machine, agent, and scheduled job doing work while you sleep — cataloged here so the next AI session doesn't have to guess your infrastructure.

## Structure

```
compute/
├── README.md              ← You are here (doctrine — what compute is, how to use it)
└── stacks.md              ← Technology bundles you actually run, one section per stack
```

When a stack grows complex enough to warrant its own file, spin it out (`compute/cloudflare-stack.md`, `compute/ai-coding-stack.md`, etc.) and link from `stacks.md`.

---

## What is Compute?

Compute is the engine layer of cmd. Where the knowledge base (wiki, strategy, cadence) holds the decisions, compute executes them.

Compute encompasses every machine doing work for you:

- Claude Code, VS Code Copilot, and other AI coding agents
- Cloudflare Workers running scheduled jobs
- MCPs giving the AI access to your tools (Linear, GitHub, Stripe, etc.)
- Hosted services, deployed scripts, integrations
- Automation pipelines (content, deployment, monitoring)

You don't run all of it manually. Most of it runs while you sleep. The operator's job in compute is to organize what's running, name the bundles (stacks), and decide what gets retired or upgraded.

## Stacks — the legible unit of compute

A stack is a bundle of tools configured for a specific class of problem. The Cloudflare Edge Stack (Workers + D1 + R2 + Pages + Access). The AI Coding Stack (Claude Code + VS Code Copilot + MCPs). The Content Production Stack (Claude + video tools + social scheduling).

Stacks are how compute becomes legible. Without them, "compute" is a sprawl of services you half-remember signing up for. With them, it's a list of named bundles you can reason about, upgrade, or kill.

## How AI uses this folder

When you ask Claude to add a new automated job, deploy a worker, or integrate a new service — point it at `compute/stacks.md` first. It'll know your existing infrastructure, what tools you already pay for, what conventions to match. Output gets dramatically better when the AI doesn't have to guess your stack from context-free prompts.

## Relationship to ctrl+shft

[ctrl+shft](https://github.com/arndvs/ctrlshft) is the agent configuration layer — it defines how AI agents behave, what skills they have, and how they're constrained. Compute catalogs what those agents can reach:

- **ctrl+shft** owns: agent personas, skills, instruction tiers, hooks, MCP configs
- **compute** owns: the live infrastructure those agents interact with — deployed services, stacks, scheduled jobs

ctrl+shft configures the agents. Compute catalogs what the agents touch. Neither system requires the other. Both are better together.

## What goes here vs. elsewhere

- **Compute (here):** documentation and catalog of active running infrastructure — URLs, account IDs, dependencies, stack inventories
- **Separate repos:** deployable application code (Workers, dashboards, APIs) lives in its own git repo, not inside cmd
- **tools/** — cmd-specific automation scripts and skills that operate on the knowledge base (not full applications)
- **ventures/<name>/** — operational context for a specific venture (may reference stacks but doesn't catalog them)
- **Decisions about tools you considered but didn't pick:** notes in a venture's `decisions.md`

Keep this folder honest. Only what's actually running.

## No code in compute/

This directory is a catalog, not a codebase. Deployable applications — Workers, dashboards, scheduled jobs — belong in their own git repos. `compute/` documents what's deployed and links to where the code lives.

```
compute/stacks.md           ← catalogs what's running
your-org/compute-worker     ← separate repo for Worker code
your-org/operator-dashboard ← separate repo for dashboard code
```

When you deploy a new service, add an entry here with: name, URL, what it does, what repo holds the code, what it depends on. The code ships from its own repo. The documentation lives here.
