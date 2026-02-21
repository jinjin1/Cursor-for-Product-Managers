# Cursor for Product Managers

A comprehensive PM toolkit that transforms Cursor into an AI-native product management copilot. Built with **Agent Skills**, **Subagents**, and **Plugin** architecture for seamless AI-powered PM workflows.

Originally inspired by the [Maven course on AI-native PMs](https://maven.com/p/0a96cb/cursor-isn-t-just-for-coding-how-ai-native-p-ms-work), [AI Dev Tasks](https://github.com/snarktank/ai-dev-tasks/tree/main), and [Lee Robinson's demo](https://www.youtube.com/watch?v=8QN23ZThdRY).

## Quick Start

1. Clone this repository into your Cursor workspace
2. Skills are automatically discovered from `.cursor/skills/`
3. Subagents are available from `.cursor/agents/`
4. Start using skills via `/skill-name` in Agent chat, or let the agent decide automatically

## Architecture

```
.cursor/
├── skills/           → 18 specialized PM skills (auto-discovered)
├── agents/           → 3 orchestration subagents
└── rules/            → Always-apply rules (PM copilot persona)

company-level-context/ → Strategic company documents (data)
initiatives/           → Active product initiatives (workspace)
meeting-notes/         → Meeting documentation (workspace)
```

## Skills (18)

Skills are portable, version-controlled packages that teach the AI agent how to perform PM tasks. They are automatically applied when relevant, or manually invoked with `/skill-name`.

### Continuous Discovery Habits

| Skill | Description | Invoke |
|:------|:------------|:-------|
| **create-interview-snapshots** | Extract structured snapshots from interviews | `/create-interview-snapshots` |
| **synthesize-snapshots** | Find patterns across multiple interviews | `/synthesize-snapshots` |
| **create-opportunities** | Identify and prioritize opportunities (OST) | `/create-opportunities` |
| **generate-solutions** | AI-human collaborative solution ideation | `/generate-solutions` |
| **identify-test-assumptions** | Surface and test leap-of-faith assumptions | `/identify-test-assumptions` |

### Product Documents

| Skill | Description | Invoke |
|:------|:------------|:-------|
| **create-prd** | Create Product Requirements Documents | `/create-prd` |
| **create-one-pager** | Amazon-style decision-focused 1-Pagers | `/create-one-pager` |
| **create-design-brief** | Design briefs (JSON + Markdown) | `/create-design-brief` |
| **generate-figma-prompt** | Figma Make-ready prompts (manual only) | `/generate-figma-prompt` |

### Task Management

| Skill | Description | Invoke |
|:------|:------------|:-------|
| **generate-tasks** | Break PRDs into actionable task lists | `/generate-tasks` |
| **process-task-list** | Execute task lists with verification | `/process-task-list` |

### Strategic Review

| Skill | Description | Invoke |
|:------|:------------|:-------|
| **product-strategy-review** | PRISM-based strategy assessment | `/product-strategy-review` |
| **product-vision-review** | 4-criteria vision evaluation | `/product-vision-review` |
| **okr-sparring-partner** | OKR coaching and sparring | `/okr-sparring-partner` |

### Evidence-Guided

| Skill | Description | Invoke |
|:------|:------------|:-------|
| **calculate-ice-score** | ICE prioritization scoring | `/calculate-ice-score` |

### Meetings & Writing

| Skill | Description | Invoke |
|:------|:------------|:-------|
| **one-on-one-meeting** | 1:1 meeting notes organization | `/one-on-one-meeting` |
| **writing-guide** | Writing style and tone standards | `/writing-guide` |

### Initiative Management

| Skill | Description | Invoke |
|:------|:------------|:-------|
| **setup-initiative** | Create new initiative folder structure (manual only) | `/setup-initiative` |

## Subagents (3)

Subagents are specialized AI assistants that handle complex, multi-step workflows autonomously. They orchestrate multiple skills in sequence and maintain their own context window.

| Subagent | Description | Use When |
|:---------|:------------|:---------|
| **discovery-researcher** | Full CDH workflow: snapshots → synthesis → opportunities → solutions → assumptions | Running user research and discovery |
| **strategy-reviewer** | Combined PRISM strategy + vision + OKR review | Reviewing strategic documents |
| **initiative-planner** | End-to-end initiative planning: setup → 1-pager → PRD → design → tasks | Starting a new product initiative |

### Invoke subagents

```
/discovery-researcher analyze these interview transcripts
/strategy-reviewer review our Q3 product strategy
/initiative-planner set up a new initiative for checkout optimization
```

## Rules

| Rule | Scope | Description |
|:-----|:------|:------------|
| **pm-strategic-copilot** | Always Apply | Sets the AI as your expert product coach and strategic advisor |

## Company Level Context

Store your organization's strategic documents in `company-level-context/`:

```
company-level-context/
├── okrs/                          → OKR documents
├── product-vision-and-strategy/   → Vision and strategy docs
└── team-structure/                → Team organization models
```

## Initiative Structure

Each initiative follows a standardized structure. Use `/setup-initiative` to create one:

```
initiatives/[initiative-name]/
├── user-interviews/
│   ├── snapshots/      → Interview snapshots
│   ├── synthesis/      → Cross-interview synthesis
│   └── transcripts/    → Raw transcripts
├── opportunities/      → Opportunity maps
├── assumptions/        → Assumption tests
├── solutions/          → Solution ideation
├── design/             → Design briefs & Figma prompts
├── prd/                → Product Requirements Documents
├── product-analytics/  → Analytics frameworks
└── tasks/              → Task breakdowns
```

## Common Workflows

### Discovery Research
```
Interview data → /create-interview-snapshots → /synthesize-snapshots
→ /create-opportunities → /generate-solutions → /identify-test-assumptions
```
Or use the `/discovery-researcher` subagent to run the full flow.

### Initiative Planning
```
/setup-initiative → /create-one-pager → /create-prd
→ /create-design-brief → /generate-tasks → /process-task-list
```
Or use the `/initiative-planner` subagent to run the full flow.

### Strategic Review
```
/product-strategy-review (PRISM) + /product-vision-review + /okr-sparring-partner
```
Or use the `/strategy-reviewer` subagent for a combined review.

### Idea Prioritization
```
/calculate-ice-score → Score and rank ideas → Select for exploration
```

## Installation

### As a Cursor Plugin
This repository is structured as a Cursor Plugin. Install via:
1. Cursor Settings (Cmd+Shift+J) → Rules → Add Rule → Remote Rule (GitHub)
2. Enter this repository's URL

### Manual Installation
Clone the repository and open in Cursor. Skills and agents are auto-discovered.

## Migration from v1

This v2 release migrates from `.mdc` rules to the Agent Skills standard:
- `.mdc` files with `alwaysApply: false` → `.cursor/skills/[name]/SKILL.md`
- `.mdc` files with `alwaysApply: true` → `.cursor/rules/[name].mdc`
- Complex workflows → `.cursor/agents/[name].md` (Subagents)
- Legacy folders (`copilots/`, `frameworks/`, `guides/`) have been removed
- Directory typo fixed: `product-vision-and-strateggy/` → `product-vision-and-strategy/`

## Acknowledgments

- **[Cursor isn't just for coding: how AI-native PMs work](https://maven.com/p/0a96cb/cursor-isn-t-just-for-coding-how-ai-native-p-ms-work)** - Tal Raviv and Hilary Gridley's course
- **[AI Dev Tasks](https://github.com/snarktank/ai-dev-tasks/tree/main)** - Structured workflow framework
- **[Cursor AI Agents Work Like 10 Developers](https://www.youtube.com/watch?v=8QN23ZThdRY)** - Lee Robinson's demo
- **[Continuous Discovery Habits](https://www.youtube.com/watch?v=9RFaz9ZBXpk)** - Teresa Torres' framework
- **[Evidence-Guided](https://www.youtube.com/watch?v=aJWSn-tz3jQ)** - Itamar Gilad's framework
- **[Agent Skills Standard](https://agentskills.io)** - Open standard for extending AI agents
