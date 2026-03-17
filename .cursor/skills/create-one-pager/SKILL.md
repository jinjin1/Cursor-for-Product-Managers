---
name: create-one-pager
description: >
  Creates decision-focused 1-Pager documents in Amazon-style narrative format. Use when
  creating concise product proposals, verifying outcome and opportunity value, or preparing
  documents for leadership decision-making.
---

# 1-Pager Creation Guide

## Goal

Guide the AI assistant to create a **decision-focused 1-Pager** in **narrative document format** using Markdown based on initial user input.
The document should be short enough to read within 5 minutes while providing sufficient context and key points to enable **fast and high-quality decision-making**.

The core purpose is to verify whether the Outcome and Opportunity are truly valuable enough to be addressed as initiatives or projects. In other words, rather than simply selecting solutions, we must examine: **"Are this opportunity and goal important enough?"**

---

## Output Format

* **Format:** Markdown
* **Structure:** Each section is written as a narrative paragraph, with **key summary bullets** provided below the paragraph.
* **Section Division:** Outcome → Opportunity → Lessons → Solutions & Assumptions → Decision Requests
* **Style:** Amazon-style 1-pager narrative (logically connected writing, avoiding unnecessary headings/list enumerations)
* **Writing Standards:** Follow the `/writing-guide` skill rules for voice, tone, banned words, and LLM pattern avoidance.

## When to Use (활용 시나리오)
- When creating a concise product proposal for leadership decision-making
- When verifying whether an opportunity is worth pursuing as an initiative
- When preparing a decision document before committing resources
- 적용 대상: 모든 PM이 새 이니셔티브를 제안할 때 사용

## Input
- **Required:** Initiative description, target outcome, and opportunity hypothesis
- **Optional:** User research data, metrics, competitive analysis
- **Context Source:** Reference `company-level-context/product-vision-and-strategy/` and `company-level-context/okrs/` for strategic alignment

---

## Process (Step-by-Step Workflow)

1. **Clarifying Questions:** Collect detailed information about Outcome, Opportunity, Lessons, Solutions, Assumptions, and Decision Request before writing.
2. **Narrative Writing:** Write each section as a storytelling paragraph. (e.g., "Current situation is... however... therefore...")
3. **Bullet Summary Addition:** After each paragraph, organize 2-4 key points as bullets for quick scanning.
4. **Risk Framework:** In Solutions & Assumptions, always examine assumptions using the four axes: **Value, Viability, Feasibility, Usability Risk**.
5. **Emphasize Discussion Triggers:** The end of the document must clearly reveal **decision points** that leadership should discuss.

---

## Example Section Style

### Outcome (Example)

Narrative paragraph:
"Currently, TVING's recommendation and search ranking heavily depends on click-through rate (CTR). However, this is not directly connected to the completion rate of users actually watching to the end, creating limitations in platform retention and ad revenue improvement. If we reflect completion propensity in the ranking, episode completion rate could improve by +5pp and Start Rate by +3pp, which could lead to long-term ARPU and revisit rate increases."

Bullet summary:

* Current problem: CTR-centered ranking → completion rate deviation
* Goal: Episode completion rate +5pp, Start Rate +3pp
* Expected effect: Users more frequently discover "one episode worth watching to the end"
* Business impact: Increased retention time, improved ad ARPU, increased revisit rate

---

## Output

* **Format:** Markdown (`.md`)
* **Location:** `/prd/`
* **Filename:** `1-pager-[initiative-name].md`

## Success Criteria
- Document readable within 5 minutes (metric: word count < 1500)
- Clear decision request with specific options stated (score: decision clarity %)
- All 4 risk axes (Value, Viability, Feasibility, Usability) addressed
- At least 2 quantified metrics in Outcome section

## Quality Check
Before finalizing, validate:
- [ ] Narrative + bullet structure followed for all sections
- [ ] Decision points are explicit and actionable
- [ ] Risk assumptions identified with test plans
- [ ] Strategic alignment with company OKRs verified

## Decision Support
When outcome value is ambiguous, suggest options:
- **Option A:** Proceed with pilot — small scope, fast validation
- **Option B:** Gather more data — defer decision, run research
- **Option C:** Reject — opportunity does not meet threshold
- **Recommend:** Based on data confidence level and time pressure

## Skill Chaining
- **Before this skill:** Use `create-opportunities` to identify the opportunity, and `synthesize-snapshots` for user research context
- **After this skill:** If approved, proceed to `create-prd` for detailed requirements
- **Related workflow:** `create-opportunities` → this skill → `create-prd` → `generate-tasks`

## Final Instructions

1. Do not generate the 1-Pager immediately; always supplement input through Clarifying Questions first.
2. Write in **narrative + summary bullet** structure reflecting user responses.
3. **Save 1-Pager:** Save the generated document as `1-pager-[feature-name].md` inside the `/prd/` directory.
4. Verify that the completed document fulfills the purpose of **triggering discussion, revealing uncomfortable facts, and decision resolution**.

---
