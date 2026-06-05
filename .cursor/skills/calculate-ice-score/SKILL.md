---
name: calculate-ice-score
description: >
  Calculates ICE (Impact, Confidence, Ease) scores for idea prioritization using
  evidence-guided methodology. Use when scoring and prioritizing product ideas,
  ordering backlogs, or selecting items for exploration and experiments.
---

# ICE-based Idea Prioritization

Score an idea on **Impact, Confidence, and Ease**, compute **ICE = I × C × E**, and
propose execution priority. Score only on explicit evidence — never inferred.

## When to Use
- Ordering an idea backlog and selecting items for exploration
- Before drafting experiment plans for a leaf opportunity in an Opportunity Solution Tree
- When you have explicit evidence (interviews/data/tests) and a rough effort estimate

## Input
- **Idea**: goal, target metric, scope, hypothesis
- **Analysis**: data/user/market/test evidence, risks, effort estimate (person-weeks)
- **Context**: `company-level-context/` for strategic/OKR alignment

## Output
- **Format:** Markdown — **Location:** `solutions/` (the initiative's `solutions/` directory — same folder as generate-solutions)
- **Filename:** `ice-[slugified-idea-title]-v[version].md` (kebab-case, auto-increment; never overwrite — re-score after tests as a new version)

## Process

### Step 1: Validate input
Confirm target metric, expected change (%), evidence text, and effort (person-weeks).
Ask clarifying questions if any are missing.

### Step 2: Impact scoring
Map expected % change to the table (default: +1.5% = Impact 2).

| Target Metric Change (%) | Impact |
|--------------------------|--------|
| > 50% | 10 | 35-49.9% | 9 | 25-34.9% | 8 | 18-24.9% | 7 |
| 12-17.9% | 6 | 7-11.9% | 5 | 4-6.9% | 4 | 2-3.9% | 3 |
| 0.5-1.9% | 2 | 0.1-0.4% | 1 | <= 0% | 0 |

### Step 3: Ease scoring
Map person-weeks to the table. When uncertain, take the conservative (lower) ease.

| Duration | Ease |
|---------|------|
| < 1 wk: 10 | 1-2 wk: 9 | 3-4 wk: 8 | 5-6 wk: 7 | 6-7 wk: 6 |
| 8-9 wk: 5 | 10-12 wk: 4 | 13-16 wk: 3 | 17-25 wk: 2 | >= 26 wk: 1 |

### Step 4: Evidence classification
Count only Impact-related evidence. "Intuitively" / "gut feel" = Self-belief.

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

### Step 5: Confidence calculation
Per-type contribution = MIN(Weight × count, Max). Apply group caps. Sum = Confidence (0-10).

### Step 6: ICE computation and priority
Compute ICE = I × C × E, then bucket:
- **>= 250** — consider immediate execution (high ROI)
- **150-249** — promising; recommend additional testing
- **100-149** — proceed with mitigations
- **< 100** — on hold or needs stronger evidence

When two scores are within ~10%, break the tie on strategic alignment with
`company-level-context/` and OKR priorities.

### Step 7: Report
Write the report using the template below.

## Output Template

```markdown
# ICE Evaluation — [Idea Title]
## Overview
- **Idea / One-line Summary / Target Metric / Assumptions**
## Score Summary
- **Impact:** [I] (basis: expected % change)
- **Ease:** [E] (basis: person-weeks)
- **Confidence:** [C] (per-type details, group caps applied)
## ICE Calculation
- ICE = I × C × E = **[Score]** — **Priority:** [Bucket]
## Input Summary
- Expected Metric Change / Effort / Evidence Excerpts with classification
## Risks / Assumptions
## Recommended Next Steps
- Confidence Improvement Plan
```

## Quality bar
- Score only on explicitly stated evidence — never invent, infer, or over-credit weak signals.
- Exclude evidence not directly tied to Impact; don't double-count the same source.
- Apply group caps; when uncertain, stay conservative and note it in Risks.
- Verify the ICE arithmetic and that the priority bucket matches the score.

## Skill Integration
- **Before:** [Create Opportunities](/create-opportunities) for ideas; [Create Interview Snapshots](/create-interview-snapshots) (qualitative) and [Analyze Metrics](/analyze-metrics) (quantitative — Market Data / User-based / Test Results) for evidence.
- **After:** [Create Design Brief](/create-design-brief) for high-scoring ideas.
- **Workflow:** Opportunities → ICE Scoring → Design Brief → Figma Prompt
