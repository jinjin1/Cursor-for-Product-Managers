---
name: identify-test-assumptions
description: >
  Identifies and tests assumptions from opportunities and solutions across desirability,
  usability, feasibility, viability, and ethical dimensions. Use when preparing to validate
  ideas, surfacing leap-of-faith assumptions, or designing lightweight tests.
---

# Identify and Test Assumptions

## When to Use
- Validating ideas before investing in development
- After [Create Opportunities](/create-opportunities) or [Synthesize Snapshots](/synthesize-snapshots), and around [Generate Solutions](/generate-solutions)
- When a new initiative needs systematic risk assessment

## Input
- **Required:** Prioritized opportunities from `opportunities/`, solution sketches from `solutions/`, interview snapshots/synthesis
- **Context:** `company-level-context/` for OKR and strategy alignment
- **Minimum:** 1 target opportunity with evidence + 2-3 candidate solutions (or 1 solution with key user journeys)

## Output
- **Format:** Markdown, saved to `assumptions/` (the initiative's `assumptions/` directory)
- **Filename:** `assumptions-[opportunity-name]-v[version].md` (kebab-case, auto-increment; never overwrite prior versions)

## Process

### Step 1: File setup
Extract the topic, check existing `assumptions-[topic]-v*.md` files, and pick the next version number.

### Step 2: Prepare context
Confirm the target opportunity and desired outcomes; identify key actors (end-users, systems, third parties).

### Step 3: Story-map candidate ideas
Assume the solution exists and map what users do to get value. Sequence steps by actor; highlight critical moments.

### Step 4: Generate assumptions (five categories)
For each pivotal step, enumerate assumptions across **Desirability, Usability, Feasibility, Viability, Ethical**.
Phrase each positively and specifically (what must be true), tie it to behavior rather than opinion, and attach evidence where available.

### Step 5: Pre-mortem
"Six months later, the launch failed. What went wrong?" Convert each reason into a testable assumption.

### Step 6: Walk OST lines (Outcome-Opportunity-Solution)
Write why the solution addresses the opportunity, and extract each inference as a testable assumption.

### Step 7: Normalize and deduplicate
Rewrite assumptions to be positive, specific, single-concept; link supporting quotes/data.

### Step 8: Map and prioritize (Assumption Mapping)
1. Plot on a 2D grid: X = Evidence (strong left, weak right), Y = Importance (high top, low bottom)
2. Select **max 3 Leap-of-Faith Assumptions (LoFA)** from the top-right quadrant (weak evidence + high importance)
3. If more than 3 qualify, prioritize by impact, test complexity, and dependencies

### Step 9: Design test cards for each LoFA
Define: simulation, method, audience, sample size, time window, and success criteria as **absolute numbers** (e.g., "3 of 10 do X"), not percentages.

### Step 10: Run, record, update
Move assumptions leftward as evidence grows. Then decide: most LoFA pass → proceed; mixed → iterate; a critical assumption fails → pivot to an alternative opportunity.

## Output Template

```markdown
# Assumptions — [Opportunity Name]
**Topic:** [topic] | **Version:** [vN] | **Target Opportunity:** [statement]

## Story Map Snapshot
- **Actors:** [types] | **Key Steps:** 1. [Actor] — [Step] ...

## Assumption Log
| ID | Category | Assumption | Evidence | Importance | Evidence Known | LoFA |
|----|----------|------------|----------|------------|----------------|------|

## Assumption Map Summary
- **LoFA (max 3):** [IDs] | **Notable clusters:** [notes]

## Test Cards (per LoFA)
- **Assumption / Simulation / Method / Audience / Sample & Window / Success Criteria / Next if Pass-Fail**

## Results and Decisions
- Outcomes / Map updates / Decisions

## Next Steps
- [ ] Run next test | [ ] Evolve idea | [ ] Share with stakeholders
```

## Quality bar
- Assumptions are specific, behavioral, and testable; all five categories covered.
- Max 3 LoFA, chosen from the weak-evidence + high-importance quadrant.
- Each test card uses absolute-number success criteria and the smallest viable simulation; scale only on positive signals.
- Evidence citations linked where available; reference prior versions to track how understanding evolved.

## Skill Integration
- **Before:** [Create Opportunities](/create-opportunities) or [Generate Solutions](/generate-solutions); [Analyze Metrics](/analyze-metrics) supplies quantitative evidence that moves assumptions off the weak-evidence axis.
- **After:** feed results back into [Generate Solutions](/generate-solutions) for refinement
- **Workflow:** Opportunities → Solutions → Assumptions → Test → Iterate
