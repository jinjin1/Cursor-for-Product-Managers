---
name: generate-solutions
description: >
  Generates multiple potential solutions for identified opportunities using Teresa Torres'
  Continuous Discovery Habits framework. Use after identifying target opportunities to
  explore different solution directions through AI-human collaborative ideation.
---

# Generate Solutions (Continuous Discovery Habits)

## Goal
Generate multiple potential solutions for identified opportunities through structured AI-human collaboration, then evaluate and select the top 3 most promising approaches.

## When to Use
- Use when a PM or product manager has a well-defined target opportunity from an initiative and needs solution ideas
- After identifying opportunities with [Create Opportunities](/create-opportunities)
- Before committing to a single solution approach
- When exploring diverse solution directions after synthesizing user research

## Input
- **Option A**: Prioritized opportunities from `opportunities/` directory
- **Option B**: Direct opportunity input from user (ad-hoc)
- **Option C**: Mixed approach (file-based + direct input)
- **Context source**: company-level-context/ (strategy, OKR for alignment)
- **Minimum**: 1 target opportunity with supporting evidence

## Output
- **Format:** Markdown — **Location:** `solutions/[topic]/`
- **Filename:** `solutions-[topic]-v[version].md` (kebab-case, auto-incrementing version)
- Never overwrite existing files; always create new version

## Process

### Step 1: Review Target Opportunity
Ensure AI and human understand the opportunity and context. Validate it's a leaf-node opportunity. Review evidence. Define success criteria. Complete within 5 minutes.

### Step 2: Individual Ideation (Human) — MANDATORY
Human generates ideas solo first. **AI MUST WAIT** — do not proceed until human provides at least 3 ideas (recommended: 10-15). If human requests solutions without this step, STOP and explain the requirement.

### Step 3: AI-Human Collaborative Ideation
Human shares ideas. AI builds on them with variations, cross-category suggestions, and probing questions ("What if we looked at this differently?"). Multiple rounds.

### Step 4: Expand and Iterate
Continue individual + collaborative sessions. Target 15-20 total ideas. Cross-pollinate ideas across domains. Embrace diversity over variations.

### Step 5: Evaluate and Select
Filter: "Does this address the target opportunity?" Collaboratively evaluate feasibility, uniqueness, and evidence basis. Select top 3. Document rationale.

## Success Criteria
- Minimum 15 ideas generated (75% or higher of target)
- Top 3 solutions each score 3/5 or higher on opportunity fit
- Solution diversity: at least 3 different categories represented
- Evidence-based: 80% or more of selected solutions grounded in user research
- Feasibility: each selected solution scores 3/5 or higher

## Context Integration
- Reference company-level-context/ strategy documents for alignment
- Verify OKR alignment when selecting final solutions
- Ensure solutions fit within strategic priorities

## Output Template Structure

Required sections and fields:

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

## Solution Categories
Suggest exploring across these categories for diversity:
1. **Feature-Based**: New features, improvements, simplification
2. **Process**: Workflow changes, automation, integration
3. **Interface**: UI/UX improvements, accessibility, responsive
4. **Business Model**: Pricing, distribution, partnerships

## Decision Support

- **Option A — High-confidence solution**: Recommend when strong evidence supports it and feasibility is high. Proceed to implementation planning.
- **Option B — Prototype and test**: Suggest when the approach is promising but needs validation. Run focused experiment.
- **Option C — Research further**: Recommend when evidence is insufficient. Gather more user data before committing.

## Antipatterns to Avoid
- Not including diverse perspectives — AI should challenge assumptions
- Too many variations of the same idea — seek categorically different approaches
- Single-session ideation — allow incubation across multiple sessions
- Ideas that don't address the target opportunity — maintain focus

## Quality Review
Before finalizing, review and evaluate:
- 15-20 ideas generated through multiple sessions
- AI-human collaboration used effectively; ideas are diverse
- Top 3 selected with documented rationale; all address target opportunity
- Implementation considerations documented; next steps clear
- Iterate to improve solution quality based on feedback

## Workflow Integration

**Before** this skill: [Create Opportunities](/create-opportunities) for target opportunities, [Create Interview Snapshots](/create-interview-snapshots) for evidence.
**After** this skill: Use selected solutions for [Calculate ICE Score](/calculate-ice-score) scoring and [Create Design Brief](/create-design-brief) specification.

```
Interviews → Snapshots → Opportunities → Generate Solutions → ICE Score → Design Brief
```
