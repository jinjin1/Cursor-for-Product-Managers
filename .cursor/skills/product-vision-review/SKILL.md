---
name: product-vision-review
description: >
  Reviews and evaluates product vision documents against 4 criteria: Lofty & Inspiring,
  Realistic & Attainable, Constraint-Free, and Grounded in User Problem. Use when
  reviewing or creating product vision statements.
---

# Product Vision Review

## Goal
Review and score product vision documents against 4 proven criteria, provide actionable feedback, and recommend concrete improvement options.

## When to Use (활용 시나리오)
- When reviewing a newly drafted product vision statement
- When preparing for a strategic planning session
- When validating vision alignment with company OKRs and strategic direction
- 적용 대상: 비전 리뷰가 필요한 모든 PM 사용 상황

## Input
- **Required:** Product vision document or statement (from `company-level-context/product-vision-and-strategy/` or user-provided)
- **Optional:** Company strategic context from `company-level-context/` for alignment check
- **Optional:** Current OKRs from `company-level-context/okrs/` for grounding

## Output
- **Format:** Markdown (`.md`)
- **Location:** Same directory as input vision document, or `company-level-context/product-vision-and-strategy/`
- **Filename:** `vision-review-[YYYY-MM-DD].md`

## Process (단계별 워크플로우)

### Step 1: Evidence Readiness Check
Before reviewing, verify:
- A vision statement is explicitly written (not confused with mission/strategy).
- Clear user problem(s) are referenced or implied.
- Time horizon (e.g., 3–5 years, long-term direction) is indicated.

If missing → **Status = HOLD**. Prompt the user to add missing pieces.

### Step 2: Score Against 4 Vision Criteria (0–5 each)

1. **Lofty & Inspiring**
   - Does it paint a future that excites and motivates?
   - Score 0 = mundane, 5 = bold, energizing.

2. **Realistic & Attainable**
   - Is the future state believable within the company's trajectory?
   - Score 0 = fantasy, 5 = ambitious yet plausible.

3. **Constraint-Free**
   - Is it written without being anchored to today's technology/org limits?
   - Score 0 = limited by today, 5 = unconstrained future vision.

4. **Grounded in User Problem**
   - Is it rooted in a clear, important user problem?
   - Score 0 = solution-driven only, 5 = crystal clear user pain.

### Step 3: Generate Feedback and Options

## Output Template Structure

```markdown
# Vision Review Summary
- **Strengths:** [list strongest aspects]
- **Risks / Gaps:** [list weaknesses, ambiguities, risks]
- **Recommendations:** [concrete suggestions for sharpening vision]

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
- Option A: [specific rewrite suggestion]
- Option B: [alternative framing]
- Recommend: [which option and why]
```

## Success Criteria
- Total vision score ≥ 14/20 for "Proceed" status (metric: 70%)
- All 4 criteria scored ≥ 3/5 (no single weak dimension)
- At least 2 concrete improvement suggestions provided
- Review completed within 5 minutes of receiving the document

## Quality Check
Before finalizing the review:
- [ ] All 4 criteria are scored with rationale
- [ ] Recommendations are specific and actionable (not generic)
- [ ] Strategic context from company documents is referenced
- [ ] Decision (Proceed/Revise/Hold) is clearly stated

## Decision Support
When vision scores are borderline (12–14/20), suggest options:
- **Option A:** Minor revisions — strengthen the weakest criterion only
- **Option B:** Major rewrite — reimagine the vision from user problems up
- **Option C:** Workshop session — facilitate team alignment before rewriting
- **Recommend:** Based on time pressure and score distribution

## Skill Chaining
- **Before this skill:** Draft vision using company strategic context from `company-level-context/product-vision-and-strategy/`
- **After this skill:** Use `product-strategy-review` to validate the full strategy built on this vision
- **Related workflow:** `okr-sparring-partner` to ensure OKRs align with the reviewed vision
