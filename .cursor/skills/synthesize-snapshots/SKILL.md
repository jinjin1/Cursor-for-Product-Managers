---
name: synthesize-snapshots
description: >
  Synthesizes multiple interview snapshots to identify common patterns, integrates
  experience maps, and creates comprehensive insights. Use after completing multiple
  interviews on the same topic or when identifying shared patterns across user segments.
---

# Synthesize Interview Snapshots

## When to Use
- After 3-5+ interviews on the same initiative topic
- Identifying shared patterns across user segments
- Before creating opportunities or generating solutions
- Sharing research findings with stakeholders

## Input
- **Required:** 3-5+ interview snapshots from [Create Interview Snapshots](/create-interview-snapshots)
- **Context:** `company-level-context/` for strategic priorities and OKR alignment
- Snapshots should share a consistent format with concrete behavioral details

## Output
- **Format:** Markdown — **Location:** `user-interviews/synthesis/`
- **Filename:** `synthesis-[initiative-name]-v[version].md` (kebab-case, auto-increment; never overwrite)

## Process

### Step 1: Prepare data
Gather the relevant snapshots. If a prior synthesis exists, process only the new
snapshots and merge into it rather than re-processing everything.

### Step 2: Analyze patterns
Extract recurring themes, behaviors, and pain points across snapshots. Note how
different segments diverge, and count the frequency and intensity of each pattern.

### Step 3: Integrate experience maps
Overlay individual maps into shared stages. For each stage, document common actions,
shared thoughts, the emotional journey, pain points, workarounds, and segment
variations, with supporting quotes from multiple participants.

### Step 4: Develop insights and opportunities
Turn patterns into actionable insights with evidence. Write opportunities in the user's
voice ("I want to… but… because…") and rate each by frequency, evidence strength, and
impact. Note research gaps.

### Step 5: Review and validate
Check that patterns have multi-participant evidence and that insights are actionable.
**Actively look for contradictory evidence** to guard against confirmation bias.

## Output Template

```markdown
# What We Learned: [Topic] Discovery Research

**Date Range:** [dates] | **Participants:** [N] | **Initiative:** [name] | **Version:** [vN]
**Synthesis Type:** [Initial/Incremental] | **Processed Snapshots:** [list]

## Executive Summary
[3-5 key findings with recommendations]

## Participant Overview
| Segment | Count | Key Characteristics |

## Top Opportunities
### 1. [Title]
**Frequency:** X/Y | **Evidence:** Strong/Moderate/Weak | **Impact:** High/Med/Low
**Opportunity:** "I want to... but... because..."
**Supporting Evidence:** [quotes] | **Business Impact:** [description]

## Integrated Experience Map
### Stage [X]: [Title]
- Common Actions / Shared Thoughts / Emotional Journey / Pain Points / Workarounds / Segment Variations / Evidence

## Key Insights
### 1. [Insight]
**What / Evidence / Implications**

## Research Gaps
- [Unanswered questions]

## Next Steps
- [ ] [Actions]
```

## Quality bar
- Each insight is supported by 2+ participants and is behavioral, not a vague generalization.
- All user segments are represented; patterns connect to company OKRs and product vision.
- Confirmation bias actively checked; contradictory evidence sought, not ignored.
- When patterns conflict: deepen research, segment the findings, or proceed with documented caveats.

## Skill Integration
- **Before:** [Create Interview Snapshots](/create-interview-snapshots)
- **After:** [Create Opportunities](/create-opportunities) and [Generate Solutions](/generate-solutions)
- **Workflow:** Interviews → Snapshots → Synthesis → Opportunities → Solutions → Assumption Testing
