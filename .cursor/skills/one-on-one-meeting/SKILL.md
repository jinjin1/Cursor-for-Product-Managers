---
name: one-on-one-meeting
description: >
  Processes and organizes 1:1 meeting notes with structured format. Use when sharing
  notes from one-on-one meetings to save them in organized Markdown format with
  action items tracking.
---

# 1:1 Meeting Notes Organizer

Turn raw 1:1 notes into a structured Markdown record with tracked action items and decisions.

## When to Use
- Saving notes after a 1:1 meeting
- Reviewing past 1:1 discussions before the next meeting
- Tracking action items and follow-ups across recurring 1:1s (manager, reports, partners)

## Input
- **Required:** Raw meeting notes (any format) + the person's name
- **Optional:** Previous notes from `meeting-notes/1-1-notes/`
- **Context:** `company-level-context/` for OKR alignment of discussion topics

## Output
- **Format:** Markdown — **Location:** `meeting-notes/1-1-notes/`
- **Filename:** `[PersonName].md` (e.g., `JohnDoe.md`)
- Append each new meeting at the **top** of the file (most recent first).

## Process
1. **Read existing context** — if `[PersonName].md` exists, review its open action items.
2. **Structure the notes** — organize raw input into the template below.
3. **Extract action items** — only the commitments assigned to *you*, each with a clear description.
4. **Update previous items** — mark completed ones; flag open items with a status.

## Template

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

## Quality bar
- Action items are assigned only to you, each specific and actionable with a deadline.
- Previous follow-ups are addressed with updated status.
- Discussion points are specific, not vague; decision rationale is captured for future context.
- For ambiguous decisions, document with a follow-up flag — or ask for clarification first when the decision is critical.

## Skill Integration
- **Before:** review previous 1:1 notes and OKRs from `company-level-context/okrs/`.
- **After:** feed action items into [generate-tasks](/generate-tasks) for tracking.
- **Related:** [writing-guide](/writing-guide) for tone and style.

# People I work with:
