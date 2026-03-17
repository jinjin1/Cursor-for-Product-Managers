---
name: calculate-ice-score
description: >
  Calculates ICE (Impact, Confidence, Ease) scores for idea prioritization using
  evidence-guided methodology. Use when scoring and prioritizing product ideas,
  ordering backlogs, or selecting items for exploration and experiments.
---

# ICE-based Idea Prioritization

## Goal
Score an idea on **Impact, Confidence, and Ease**, compute **ICE = I x C x E**, and propose execution priority. All evaluations rely on explicit evidence only.

## When to Use
- Use when a PM or product manager needs to quickly order an idea backlog and select items for exploration
- Before drafting experiment plans for a leaf opportunity in an Opportunity Solution Tree
- When you have explicit evidence (interviews/data/tests) and a rough effort estimate for an initiative

## Input
- **Idea title and description**: goal, target metric, scope, hypothesis
- **Idea analysis**: data/user/market/test evidence, risks, effort estimate
- **Context source**: company-level-context/ (strategic goals, OKR, product strategy for alignment)
- Optional: target metric change (%), estimated effort (person-weeks)

## Output
- **Format:** Markdown — **Location:** `initiatives/[initiative]/solutions/`
- **Filename:** `ice-[YYYY-MM-DD]-[slugified-idea-title].md`

## Process

1. Validate inputs and gather context
2. Execute core analysis
3. Generate output and review results
4. Iterate based on feedback


### Step 1: Input Validation
Verify target metric, expected change (%), evidence text, and effort (person-weeks). If missing, ask clarifying questions.

### Step 2: Impact Scoring
Map % change to Impact table. Default: +1.5% = Impact 2.

| Target Metric Change (%) | Impact |
|--------------------------|--------|
| > 50% | 10 | 35-49.9% | 9 | 25-34.9% | 8 | 18-24.9% | 7 |
| 12-17.9% | 6 | 7-11.9% | 5 | 4-6.9% | 4 | 2-3.9% | 3 |
| 0.5-1.9% | 2 | 0.1-0.4% | 1 | <= 0% | 0 |

### Step 3: Ease Scoring
Map person-weeks to Ease table. If uncertain, use conservative lower ease.

| Duration | Ease |
|---------|------|
| < 1 wk: 10 | 1-2 wk: 9 | 3-4 wk: 8 | 5-6 wk: 7 | 6-7 wk: 6 |
| 8-9 wk: 5 | 10-12 wk: 4 | 13-16 wk: 3 | 17-25 wk: 2 | >= 26 wk: 1 |

### Step 4: Evidence Classification
Count only Impact-related evidence. Evidence types and weights:

| Evidence Type | Weight | Max | Group Cap |
|---|---:|---:|---|
| Self-belief | 0.01 | 0.1 | A: <= 0.1 |
| Directional Fit | 0.05 | 0.1 | A: <= 0.1 |
| Opinions of Others | 0.10 | 0.5 | B: <= 0.5 |
| Estimates & Plans | 0.30 | 0.5 | B: <= 0.5 |
| Empirical Evidence | 0.50 | 1.0 | — |
| Market Data | 1.0 | 3.0 | C: <= 3.0 |
| User-based Evidence | 2.0 | 3.0 | C: <= 3.0 |
| Test Results | 3.0 | 5.0 | — |

Use only explicitly stated evidence. "Intuitively" / "gut feel" = Self-belief.

### Step 5: Confidence Calculation
Per-type contribution = MIN(Weight x count, Max). Apply group caps. Sum = final Confidence (0-10).

### Step 6: ICE Computation
Compute ICE = I x C x E. Assign priority bucket:
- >= 250: Consider immediate execution (high ROI)
- 150-249: Promising; recommend additional testing
- 100-149: Proceed with mitigations
- < 100: On hold or needs strengthening

### Step 7: Report Generation
Generate report using the template structure below within 15 minutes of receiving complete input.

## Success Criteria
- 100% of required sections completed in output
- Evidence classification accuracy >= 90% (no inferred evidence)
- Score computation mathematically verified with 0% error rate

## Output Template Structure

Required sections and fields for the report:

```markdown
# ICE Evaluation — [Idea Title]
## Overview
- **Idea / One-line Summary / Target Metric / Assumptions**
## Score Summary
- **Impact:** [I] (basis: expected % change)
- **Ease:** [E] (basis: person-weeks)
- **Confidence:** [C] (with per-type details and group caps applied)
## ICE Calculation
- ICE = I x C x E = **[Score]** — **Priority Guidance:** [Bucket]
## Input Summary
- Expected Metric Change / Effort / Evidence Excerpts with classification
## Risks / Assumptions
## Recommended Next Steps
- Confidence Improvement Plan
```

## Decision Support

- **Option A — Execute immediately**: ICE >= 250. Recommend full implementation.
- **Option B — Test first**: ICE 100-249. Recommend focused experiment or prototype.
- **Option C — Deprioritize**: ICE < 100. Suggest shelving; revisit after gathering stronger evidence.

When scores are close (within 10%), recommend comparing strategic alignment with company-level context and OKR priorities.

## Quality Review
Before finalizing, validate and evaluate:
- All input fields present; Impact/Ease correctly mapped
- Evidence classified from explicit information only (no inference)
- Group caps correctly applied; ICE formula computed correctly
- Priority bucket matches score; risks documented
- Improve accuracy by cross-checking evidence sources

## Workflow Integration

**Before** this skill: [Create Opportunities](/create-opportunities) for input ideas, [Create Interview Snapshots](/create-interview-snapshots) for evidence.
**After** this skill: [Create Design Brief](/create-design-brief) for high-scoring ideas, [Generate Figma Prompt](/generate-figma-prompt) for design workflow.

```
Opportunities → ICE Scoring → Design Brief → Figma Prompt
                    ↑
          Interview Evidence
```

## Guardrails
- Do not invent/infer evidence or over-credit weak signals
- Exclude evidence not directly tied to Impact from Confidence
- Prevent duplicate counting of the same source
- When uncertain, apply conservative caps and document in Risks
