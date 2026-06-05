---
name: create-one-pager
description: >
  Creates decision-focused 1-Pager documents in Amazon-style narrative format. Use when
  creating concise product proposals, verifying outcome and opportunity value, or preparing
  documents for leadership decision-making.
---

# 1-Pager Creation Guide

Create a decision-focused 1-Pager in Amazon-style narrative format. Its purpose is to
test whether the Outcome and Opportunity are valuable enough to pursue — not to pick a
solution. Keep it short enough to read quickly while giving leadership what they need to
decide.

## When to Use
- A concise product proposal for a leadership decision
- Testing whether an opportunity is worth pursuing as an initiative
- A decision document before committing resources

## Input
- **Required:** Initiative description, target outcome, opportunity hypothesis
- **Recommended:** Selected solution from `solutions/` and the validated/open assumptions from `assumptions/` — these feed the Solutions & Assumptions section
- **Optional:** User research, metrics, competitive analysis
- **Context:** `company-level-context/product-vision-and-strategy/` and `.../okrs/` for alignment

## Output
- **Format:** Markdown — **Location:** `prd/` (the initiative's `prd/` directory)
- **Filename:** `1-pager-[initiative-name].md`
- **Structure:** Each section is a narrative paragraph followed by 2-4 key summary bullets.
  Sections: Outcome → Opportunity → Lessons → Solutions & Assumptions → Decision Requests.
  Amazon-style prose (logically connected), not heading/list dumps. Apply the
  [writing-guide](/writing-guide) rules.

## Process
1. **Clarifying questions** — gather Outcome, Opportunity, Lessons, Solutions, Assumptions,
   and the Decision Request before writing.
2. **Narrative writing** — each section as a story ("Current situation is… however… therefore…").
3. **Bullet summary** — 2-4 scannable key points under each paragraph.
4. **Risk framework** — in Solutions & Assumptions, examine assumptions on four axes:
   **Value, Viability, Feasibility, Usability Risk**.
5. **Decision triggers** — end with the explicit decision points leadership should discuss.

## Example (Outcome section)

> Currently, TVING's recommendation and search ranking depends heavily on click-through
> rate (CTR), which isn't tied to whether users actually finish what they start — limiting
> retention and ad revenue. Reflecting completion propensity in ranking could lift episode
> completion rate +5pp and Start Rate +3pp, raising long-term ARPU and revisit rate.

- Current problem: CTR-centered ranking → completion-rate deviation
- Goal: completion rate +5pp, Start Rate +3pp
- Business impact: more retention time, better ad ARPU, higher revisit rate

## Quality bar
- Narrative + bullet structure in every section; reads fast and aids a real decision.
- The decision request is explicit, with specific options to choose between.
- All four risk axes addressed, each with a test plan; Outcome backed by quantified metrics.
- Surfaces the uncomfortable facts rather than burying them; aligns with company OKRs.
- Ask clarifying questions first; when value is ambiguous, offer pilot / gather-more-data / reject and recommend one.

## Skill Integration
- **Before:** [create-opportunities](/create-opportunities) for the opportunity, [generate-solutions](/generate-solutions) for the selected solution, [identify-test-assumptions](/identify-test-assumptions) for validated/open assumptions.
- **After:** if approved, [create-prd](/create-prd) for detailed requirements.
- **Workflow:** create-opportunities → this skill → create-prd → generate-tasks
