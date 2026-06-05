---
name: create-prd
description: >
  Creates detailed Product Requirements Documents in Markdown format. Use when writing PRDs,
  defining feature requirements, or creating specification documents for development teams.
---

# Generating a Product Requirements Document (PRD)

Create a clear, actionable PRD a junior developer can implement without extra context.

## When to Use
- Defining feature requirements for a development team
- Turning a product decision or user need into an actionable spec

## Input
- **Required:** Feature description or user request
- **Optional:** User research, 1-pager, design brief
- **Context:** `company-level-context/product-vision-and-strategy/` for alignment

## Output
- **Format:** Markdown — **Location:** `prd/` (the initiative's `prd/` directory; consumed by `generate-tasks`)
- **Filename:** `prd-[feature-name].md`

## Process

1. **Receive the prompt** — the user describes the feature.
2. **Ask clarifying questions** — only the 3-5 most essential gaps, focused on the
   "what" and "why" (not the "how"). Number them and give lettered options so the user
   can reply "1A, 2C, 3B". Only ask what isn't reasonably inferable from the prompt.
3. **Generate the PRD** using the structure below.
4. **Save** as `prd-[feature-name].md` in the initiative's `prd/` directory.
5. **Apply** the [writing-guide](/writing-guide) rules for voice, tone, and banned words.

Clarifying-question example:

```
1. What is the primary goal of this feature?
   A. Improve onboarding   B. Increase retention   C. Reduce support   D. Add revenue
2. Who is the target user?
   A. New users   B. Existing users   C. All users   D. Admins
```

## PRD Structure

1. **Introduction/Overview** — the feature, the problem it solves, the goal.
2. **Goals** — specific, measurable objectives.
3. **User Stories** — narratives of usage and benefit.
4. **Functional Requirements** — numbered, specific, clear ("The system must allow users to upload a profile picture.").
5. **Non-Goals (Out of Scope)** — what this feature will *not* include.
6. **Design Considerations (optional)** — mockups, UI/UX, relevant components.
7. **Technical Considerations (optional)** — known constraints, dependencies.
8. **Success Metrics** — how success is measured (e.g., "reduce X support tickets by 10%").
9. **Open Questions** — anything still needing clarification.

Write for a junior developer: explicit, unambiguous, low-jargon.

## Quality bar
- All applicable sections present; functional requirements numbered and unambiguous.
- Success metrics are quantified with specific targets; non-goals state boundaries.
- A junior developer can implement it without additional context.
- When scope is unclear, offer MVP (core only) vs full (with nice-to-haves) and recommend one.
- Ask the clarifying questions before writing; do not start implementing the feature.

## Skill Integration
- **Before:** [create-one-pager](/create-one-pager) for approval, [create-design-brief](/create-design-brief) for UX context.
- **After:** [generate-tasks](/generate-tasks) to break the PRD into development tasks.
- **Workflow:** create-one-pager → this skill → generate-tasks
