---
name: one-on-one-meeting
description: >
  Processes and organizes 1:1 meeting notes with structured format. Use when sharing
  notes from one-on-one meetings to save them in organized Markdown format with
  action items tracking.
---

# 1:1 Meeting Notes Organizer

## Goal
Transform raw 1:1 meeting notes into a structured, actionable Markdown document with tracked action items and decision records.

## When to Use
- Use when a PM or product manager completes a 1:1 meeting and needs to save notes
- When reviewing past 1:1 discussions for context before the next meeting
- When tracking action items and follow-ups from recurring meetings
- Applicable to all 1:1s: manager, direct reports, cross-functional partners

## Input
- **Required:** Raw meeting notes (text, bullet points, or freeform) + person's name
- **Optional:** Previous meeting context from `meeting-notes/1-1 notes/`
- **Context:** Reference `company-level-context/` for company-level strategic alignment of discussion topics and OKR context

## Output
- **Format:** Markdown (`.md`)
- **Location:** `meeting-notes/1-1 notes/`
- **Filename:** `[PersonName].md` (e.g., `JohnDoe.md`)
- **Template structure:** Each meeting entry has required sections: Notes, Decisions, Action Items, Follow-up
- Append new meeting at the **top** of existing file (most recent first)

## Process

1. Validate inputs and gather context
2. Execute core analysis
3. Generate output and review results
4. Iterate based on feedback


### Step 1: Read existing context
Check if `meeting-notes/1-1 notes/[PersonName].md` exists. If so, review previous action items for follow-up tracking.

### Step 2: Structure the notes
Organize raw input into the template format below, ensuring each field is complete.

### Step 3: Extract action items
Identify commitments assigned to you only. Each action item should have a clear description.

### Step 4: Check previous items
Mark completed items from prior meetings. Suggest follow-up options for open items.

### Step 5: Review and validate
Evaluate notes for clarity and completeness. Improve any vague discussion points with specific details.

## Template Structure
```markdown
## [YYYY-MM-DD]
### Notes
- Key discussion point 1
- Key discussion point 2
### Decisions
- Decision made and rationale
### Action Items
- [ ] Task 1 (assigned to me)
- [ ] Task 2 (assigned to me)
### Follow-up from Previous
- [x] Completed item from last time
- [ ] Open item — status update
```

## Success Criteria
- All action items have clear owners and deadlines (metric: completeness 100%)
- Previous action items are reviewed with updated status
- Notes are scannable in under 30 seconds (target: fewer than 30 lines per meeting section)
- Decision rationale is documented for future context

## Quality Check
Before saving, validate:
- [ ] All action items are assigned only to you
- [ ] Previous meeting follow-ups are addressed
- [ ] Discussion points are specific, not vague
- [ ] Format matches the template structure

## Decision Support
When notes contain ambiguous decisions, suggest options:
- **Option A:** Document as-is with a follow-up flag
- **Option B:** Ask for clarification before saving
- **Recommend:** Option A for speed, Option B for critical decisions

## Self-Evaluation
- Review whether action items are specific and actionable (not vague)
- Evaluate if decisions capture sufficient rationale for future context
- Validate that follow-ups from previous meetings are consistently tracked
- Improve by iterating on note structure based on feedback from meeting participants

## Skill Integration
- **Before this skill:** Prepare by reviewing previous 1:1 notes and company OKRs from `company-level-context/okrs/`
- **After this skill:** Use action items as input to `generate-tasks` workflow for task tracking
- **Related:** [Writing Guide](/writing-guide) for tone and style of written notes

## Time Efficiency
- Note structuring should complete within 5 minutes per meeting
- Action item extraction should take no more than 2 minutes
- Review of previous items should be done within 3 minutes

# People I work with:
