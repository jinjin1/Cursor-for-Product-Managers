---
name: generate-solutions
description: >
  Generates multiple potential solutions for identified opportunities using Teresa Torres'
  Continuous Discovery Habits framework. Use after identifying target opportunities to
  explore different solution directions through AI-human collaborative ideation.
---

# Generate Solutions (Continuous Discovery Habits)

Generate diverse solutions for a target opportunity through AI-human collaboration,
then evaluate and select the top 3.

## When to Use
- A well-defined target opportunity needs solution ideas
- After [Create Opportunities](/create-opportunities), before committing to one approach
- When exploring diverse directions after synthesizing research

## Input
- A target opportunity — from `opportunities/`, direct user input, or both
- **Context**: `company-level-context/` for strategy/OKR alignment
- Minimum: 1 target opportunity with supporting evidence

## Output
- **Format:** Markdown — **Location:** `solutions/` (the initiative's `solutions/` directory)
- **Filename:** `solutions-[topic]-v[version].md` (kebab-case, auto-increment; never overwrite)

## Process

### Step 1: Review the target opportunity
Confirm it's a leaf-node opportunity, review its evidence, and define what a good
solution must achieve.

### Step 2: Human ideates first
The human generates ideas solo before the AI contributes. Wait for the human's ideas
(a few at minimum, ideally 10-15) — if asked to generate solutions before the human
has shared theirs, explain why this step comes first rather than skipping it. This
keeps the human's thinking from being anchored by the AI.

### Step 3: Collaborate
Build on the human's ideas with variations, cross-category suggestions, and probing
questions ("What if we looked at this differently?"). Run multiple rounds.

### Step 4: Expand for diversity
Aim for breadth (15-20+ ideas) across categories rather than variations of one idea:
- **Feature** — new features, improvements, simplification
- **Process** — workflow changes, automation, integration
- **Interface** — UI/UX, accessibility, responsive
- **Business model** — pricing, distribution, partnerships

### Step 5: Evaluate and select
Filter on "Does this address the target opportunity?", then weigh feasibility,
uniqueness, and evidence basis. Select the top 3 and document why.

## Output Template

```markdown
# Solutions for [Opportunity Name]
**Topic / Version / Target Opportunity / Source Documents / Total Ideas / Final Selected: 3**

## Problem Definition
- Target Opportunity Statement
- Context: Who, When, Current Solutions, Impact
- Success Criteria (measurable outcomes)

## Ideation Process
- Individual Sessions (dates, counts)
- Collaborative Sessions (insights, new ideas)
- Total Ideas Generated

## Idea Evaluation
- Initial Filter results
- Evaluation table: | Idea | Addresses Opportunity | Feasibility | Uniqueness | Evidence-Based |

## Selected Solutions (x3)
### Solution N: [Name]
**Type / Approach / Description / Key Features / User Experience / Why Selected**
**Implementation**: Feasibility, User Value, Business Value, Risks

## Next Steps
```

## Quality bar
- Human ideates before the AI; ideas span several distinct categories, not variations of one.
- Every selected solution addresses the target opportunity and is grounded in user research.
- Top 3 chosen with documented rationale and implementation considerations.
- Per selected solution, note whether to build now, prototype-and-test, or research further.

## Skill Integration
- **Before:** [Create Opportunities](/create-opportunities) for the opportunity, [Create Interview Snapshots](/create-interview-snapshots) for evidence.
- **After:** [Calculate ICE Score](/calculate-ice-score) and [Create Design Brief](/create-design-brief).
- **Workflow:** Interviews → Snapshots → Opportunities → Generate Solutions → ICE Score → Design Brief
