---
name: product-vision-review
description: >
  Reviews and evaluates product vision documents against 4 criteria: Lofty & Inspiring,
  Realistic & Attainable, Constraint-Free, and Grounded in User Problem. Use when
  reviewing or creating product vision statements.
---

# Product Vision Review

Score a product vision against 4 proven criteria, give actionable feedback, and recommend
concrete improvements.

## When to Use
- Reviewing a newly drafted product vision statement
- Preparing for a strategic planning session
- Validating vision alignment with company OKRs and direction

## Input
- **Required:** Product vision document or statement (from `company-level-context/product-vision-and-strategy/` or user-provided)
- **Optional:** Strategic context from `company-level-context/` and OKRs from `.../okrs/` for grounding

## Output
- **Format:** Markdown — **Location:** same directory as the vision doc, or `company-level-context/product-vision-and-strategy/`
- **Filename:** `vision-review-[YYYY-MM-DD].md`

## Process

### Step 1: Evidence readiness check
Confirm a vision statement is explicitly written (not mission/strategy), references a clear
user problem, and indicates a time horizon (e.g., 3-5 years). If any are missing, set
**Status = HOLD** and prompt the user to add them.

### Step 2: Score against the 4 vision criteria (0-5 each)
1. **Lofty & Inspiring** — paints a future that excites? (0 = mundane, 5 = bold, energizing)
2. **Realistic & Attainable** — believable within the company's trajectory? (0 = fantasy, 5 = ambitious yet plausible)
3. **Constraint-Free** — written without anchoring to today's tech/org limits? (0 = limited by today, 5 = unconstrained)
4. **Grounded in User Problem** — rooted in a clear, important user problem? (0 = solution-only, 5 = crystal-clear pain)

### Step 3: Feedback, decision, and options
Write strengths, gaps, and concrete improvement options; state the decision.

## Output Template

```markdown
# Vision Review Summary
- **Strengths:** [strongest aspects]
- **Risks / Gaps:** [weaknesses, ambiguities, risks]
- **Recommendations:** [concrete suggestions for sharpening the vision]

## Scores
| Criterion | Score | Rationale |
|-----------|-------|-----------|
| Lofty/Inspiring | X/5 | ... |
| Realistic/Attainable | X/5 | ... |
| Constraint-Free | X/5 | ... |
| Grounded in User Problem | X/5 | ... |
| **Total** | **X/20** | |

## Decision
- Proceed / Needs Revision / Hold (missing essentials)

## Improvement Options
- Option A: [specific rewrite] | Option B: [alternative framing] | Recommend: [which and why]
```

## Quality bar
- All 4 criteria scored with rationale; no single dimension left weak.
- Decision stated clearly (Proceed at total ≥ 14/20; Revise; or Hold when essentials are missing).
- Recommendations are specific and actionable, referencing company strategic context — at least two.
- For borderline scores (12-14/20): strengthen the weakest criterion, rewrite from user problems up, or run a team workshop.
- Spar, don't soothe: take a position on every claim and name what evidence would change it; never hedge with "interesting" or "you might consider"; challenge the strongest version, not a strawman.

## Skill Integration
- **Before:** draft the vision using context from `company-level-context/product-vision-and-strategy/`.
- **After:** [product-strategy-review](/product-strategy-review) to validate the full strategy built on this vision.
- **Related:** [okr-sparring-partner](/okr-sparring-partner) to align OKRs with the reviewed vision.
