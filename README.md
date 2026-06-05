# Cursor for Product Managers

Transform Cursor into your AI-native product management copilot. Stop wrestling with fragmented PM tools and start building a unified, AI-powered workspace for user research, product strategy, OKR planning, PRD creation, and discovery workflows — all powered by proven frameworks like Continuous Discovery Habits, PRISM, and Evidence-Guided product development.

Originally inspired by the [Maven course on AI-native PMs](https://maven.com/p/0a96cb/cursor-isn-t-just-for-coding-how-ai-native-p-ms-work), [AI Dev Tasks](https://github.com/snarktank/ai-dev-tasks/tree/main), and [Lee Robinson's demo](https://www.youtube.com/watch?v=8QN23ZThdRY).

## Why This Toolkit?

Product management involves complex workflows across research, discovery, and delivery. This toolkit brings structure, clarity, and AI-native efficiency to the process:

1. **Unified Context Management** — Centralize all PM knowledge, frameworks, and insights in one AI-accessible workspace
2. **Structured Discovery** — Run systematic user research with Continuous Discovery Habits (Teresa Torres) built in
3. **AI-Native Workflows** — Create PRDs, 1-pagers, design briefs, and strategy reviews through natural conversation
4. **Iterative Improvement** — Documents and insights grow smarter with every AI interaction

## Quick Start

1. Clone this repository into your Cursor workspace
2. Open Cursor Agent chat and start with a workflow:

| What you want to do | Just type |
|:---------------------|:----------|
| Process interview transcripts | `/create-interview-snapshots` |
| Create a PRD | `/create-prd` |
| Review product strategy (PRISM) | `/product-strategy-review` |
| Start a new initiative | `/setup-initiative` |
| Run full discovery research | `/discovery-researcher` |

Skills are automatically discovered — no configuration needed.

## What You Can Do

### User Research & Discovery

Run the full Continuous Discovery Habits workflow, from raw interview data to testable assumptions:

```
Interview data → /create-interview-snapshots → /synthesize-snapshots
→ /create-opportunities → /generate-solutions → /identify-test-assumptions
```

Or let the `/discovery-researcher` subagent run the entire flow for you.

| Skill | What it does |
|:------|:-------------|
| `/product-diagnostic` | Sparring pressure-test of demand and premise before you build (YC office-hours style) |
| `/create-interview-snapshots` | Extract structured snapshots from qualitative interviews |
| `/synthesize-snapshots` | Find patterns and themes across multiple interviews |
| `/create-opportunities` | Build an Opportunity Solution Tree (OST) |
| `/generate-solutions` | AI-human collaborative solution ideation |
| `/identify-test-assumptions` | Surface and test leap-of-faith assumptions |
| `/analyze-metrics` | Turn product analytics into quantitative evidence for ICE and assumptions |

### Product Documents

Create professional product artifacts through guided conversation:

| Skill | What it does |
|:------|:-------------|
| `/create-prd` | Generate Product Requirements Documents with clarifying questions |
| `/create-one-pager` | Amazon-style decision-focused 1-Pagers |
| `/create-design-brief` | Design briefs in JSON + Markdown |
| `/generate-figma-prompt` | Figma Make-ready prompts (5000 char limit) |

### Product Strategy & OKRs

Review and refine your strategic direction with proven frameworks:

| Skill | What it does |
|:------|:-------------|
| `/product-strategy-review` | PRISM framework: Problem Diagnosis, Reframe, Intentional Bets, Systemized Execution, Momentum |
| `/product-vision-review` | Evaluate vision on 4 criteria: Lofty, Realistic, Constraint-Free, User-Grounded |
| `/okr-sparring-partner` | Context-aware OKR coaching and sparring partner |
| `/calculate-ice-score` | ICE prioritization scoring (Impact x Confidence x Ease) |

### Task Management

Break strategy into execution:

| Skill | What it does |
|:------|:-------------|
| `/generate-tasks` | Break PRDs into actionable, granular task lists |

### Meetings & Writing

| Skill | What it does |
|:------|:-------------|
| `/one-on-one-meeting` | Structure and organize 1:1 meeting notes |
| `/writing-guide` | Consistent writing style and tone standards |

## Subagents — Multi-Step Workflows

For complex workflows, subagents orchestrate multiple skills end-to-end:

| Subagent | What it does | Example |
|:---------|:-------------|:--------|
| `/discovery-researcher` | Full CDH workflow: interviews → synthesis → opportunities → solutions → assumptions | `/discovery-researcher analyze these interview transcripts` |
| `/initiative-planner` | End-to-end planning: setup → 1-pager → PRD → design → tasks | `/initiative-planner set up checkout optimization` |
| `/strategy-reviewer` | Combined PRISM strategy + vision + OKR review | `/strategy-reviewer review our Q3 product strategy` |

## Workflow Connections

```
                    /discovery-researcher
                           │
    ┌──────────────────────┼──────────────────────┐
    ▼                      ▼                      ▼
/create-interview   /synthesize-      /create-opportunities
  -snapshots          snapshots              │
                                      ┌──────┴──────┐
                                      ▼              ▼
                              /generate-       /calculate-
                               solutions        ice-score
                                   │
                                   ▼
                          /identify-test-
                            assumptions
                                   │
               ────────── handoff ──────────
                                   │
                    /initiative-planner
                           │
    ┌──────────┬───────────┼───────────┬──────────┐
    ▼          ▼           ▼           ▼          ▼
/setup-    /create-    /create-   /create-   /generate-
initiative  one-pager    prd     design-brief  tasks
                                      │
                                      ▼
                              /generate-figma-
                                  prompt
```

## Common Workflows

### Starting a New Product Initiative
```
/setup-initiative → /create-one-pager → /create-prd
→ /create-design-brief → /generate-tasks
```
Or use `/initiative-planner` to run the full flow.

### Reviewing Strategic Direction
```
/product-strategy-review (PRISM) + /product-vision-review + /okr-sparring-partner
```
Or use `/strategy-reviewer` for a combined review.

### Prioritizing Ideas
```
/calculate-ice-score → Score and rank ideas → Select for exploration
```

## Project Structure

```
company-level-context/        → Your organization's strategic documents
├── okrs/                     → OKR documents
├── product-vision-and-strategy/ → Vision and strategy docs
└── team-structure/            → Team organization models

initiatives/                   → Active product initiatives
├── _templates/                → Initiative template structure
└── [initiative-name]/         → Each initiative's workspace
    ├── user-interviews/       → Snapshots, synthesis, transcripts
    ├── opportunities/         → Opportunity maps (OST)
    ├── assumptions/           → Assumption tests
    ├── solutions/             → Solution ideation
    ├── design/                → Design briefs & Figma prompts
    ├── prd/                   → Product Requirements Documents
    ├── product-analytics/     → Analytics frameworks
    └── tasks/                 → Task breakdowns

meeting-notes/                 → Meeting documentation
├── 1-1 notes/                 → One-on-one meetings
├── leadership/                → Leadership meetings
├── product-trio/              → PM, Design, Engineering collaboration
└── board-n-investor/          → Board and investor meetings
```

Skills, subagents, and rules live in `.cursor/` and are auto-discovered by Cursor.

## Installation

### As a Cursor Plugin
1. Cursor Settings (Cmd+Shift+J) → Rules → Add Rule → Remote Rule (GitHub)
2. Enter this repository's URL

### Manual Installation
Clone the repository and open in Cursor. All 19 skills and 3 subagents are automatically discovered.

## Migration from v1

This v2 release migrates from `.mdc` rules to the [Agent Skills standard](https://agentskills.io):
- `.mdc` files with `alwaysApply: false` → `.cursor/skills/[name]/SKILL.md`
- `.mdc` files with `alwaysApply: true` → `.cursor/rules/[name].mdc`
- Complex workflows → `.cursor/agents/[name].md` (Subagents)
- Legacy folders (`copilots/`, `frameworks/`, `guides/`) have been removed

## Acknowledgments

- **[Cursor isn't just for coding: how AI-native PMs work](https://maven.com/p/0a96cb/cursor-isn-t-just-for-coding-how-ai-native-p-ms-work)** — Tal Raviv and Hilary Gridley's course on transforming Cursor into a PM copilot
- **[AI Dev Tasks](https://github.com/snarktank/ai-dev-tasks/tree/main)** — Structured workflow framework for AI-assisted development
- **[Cursor AI Agents Work Like 10 Developers](https://www.youtube.com/watch?v=8QN23ZThdRY)** — Lee Robinson's demo
- **[Continuous Discovery Habits](https://www.youtube.com/watch?v=9RFaz9ZBXpk)** — Teresa Torres' framework on continuous user research and discovery
- **[Evidence-Guided](https://www.youtube.com/watch?v=aJWSn-tz3jQ)** — Itamar Gilad's framework on evidence-guided product development
- **[Agent Skills Standard](https://agentskills.io)** — Open standard for extending AI agents
