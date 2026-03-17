---
name: create-prd
description: >
  Creates detailed Product Requirements Documents in Markdown format. Use when writing PRDs,
  defining feature requirements, or creating specification documents for development teams.
---

# Generating a Product Requirements Document (PRD)

## Goal

To guide an AI assistant in creating a detailed Product Requirements Document (PRD) in Markdown format, based on an initial user prompt. The PRD should be clear, actionable, and suitable for a junior developer to understand and implement the feature.

## When to Use
- When defining feature requirements for development teams
- When creating specification documents from product decisions
- When translating user needs into actionable development specs
- 적용 대상: 모든 PM이 기능 요구사항을 문서화할 때 사용

## Input
- **Required:** Feature description or user request
- **Optional:** User research, 1-pager, design brief
- **Context Source:** Reference `company-level-context/product-vision-and-strategy/` for strategic alignment

## Process (단계별 워크플로우)

1.  **Receive Initial Prompt:** The user provides a brief description or request for a new feature or functionality.
2.  **Ask Clarifying Questions:** Before writing the PRD, the AI *must* ask only the most essential clarifying questions needed to write a clear PRD. Limit questions to 3-5 critical gaps in understanding. The goal is to understand the "what" and "why" of the feature, not necessarily the "how" (which the developer will figure out). Make sure to provide options in letter/number lists so I can respond easily with my selections.
3.  **Generate PRD:** Based on the initial prompt and the user's answers to the clarifying questions, generate a PRD using the structure outlined below.
4.  **Save PRD:** Save the generated document as `prd-[feature-name].md` inside the `/tasks` directory.
5.  **Writing Standards:** Follow the `/writing-guide` skill rules for voice, tone, banned words, and LLM pattern avoidance.

## Clarifying Questions (Guidelines)

Ask only the most critical questions needed to write a clear PRD. Focus on areas where the initial prompt is ambiguous or missing essential context. Common areas that may need clarification:

*   **Problem/Goal:** If unclear - "What problem does this feature solve for the user?"
*   **Core Functionality:** If vague - "What are the key actions a user should be able to perform?"
*   **Scope/Boundaries:** If broad - "Are there any specific things this feature *should not* do?"
*   **Success Criteria:** If unstated - "How will we know when this feature is successfully implemented?"

**Important:** Only ask questions when the answer isn't reasonably inferable from the initial prompt. Prioritize questions that would significantly impact the PRD's clarity.

### Formatting Requirements

- **Number all questions** (1, 2, 3, etc.)
- **List options for each question as A, B, C, D, etc.** for easy reference
- Make it simple for the user to respond with selections like "1A, 2C, 3B"

### Example Format

```
1. What is the primary goal of this feature?
   A. Improve user onboarding experience
   B. Increase user retention
   C. Reduce support burden
   D. Generate additional revenue

2. Who is the target user for this feature?
   A. New users only
   B. Existing users only
   C. All users
   D. Admin users only

3. What is the expected timeline for this feature?
   A. Urgent (1-2 weeks)
   B. High priority (3-4 weeks)
   C. Standard (1-2 months)
   D. Future consideration (3+ months)
```

## PRD Structure

The generated PRD should include the following sections:

1.  **Introduction/Overview:** Briefly describe the feature and the problem it solves. State the goal.
2.  **Goals:** List the specific, measurable objectives for this feature.
3.  **User Stories:** Detail the user narratives describing feature usage and benefits.
4.  **Functional Requirements:** List the specific functionalities the feature must have. Use clear, concise language (e.g., "The system must allow users to upload a profile picture."). Number these requirements.
5.  **Non-Goals (Out of Scope):** Clearly state what this feature will *not* include to manage scope.
6.  **Design Considerations (Optional):** Link to mockups, describe UI/UX requirements, or mention relevant components/styles if applicable.
7.  **Technical Considerations (Optional):** Mention any known technical constraints, dependencies, or suggestions (e.g., "Should integrate with the existing Auth module").
8.  **Success Metrics:** How will the success of this feature be measured? (e.g., "Increase user engagement by 10%", "Reduce support tickets related to X").
9.  **Open Questions:** List any remaining questions or areas needing further clarification.

## Target Audience

Assume the primary reader of the PRD is a **junior developer**. Therefore, requirements should be explicit, unambiguous, and avoid jargon where possible. Provide enough detail for them to understand the feature's purpose and core logic.

## Output

*   **Format:** Markdown (`.md`)
*   **Location:** `/prd/`
*   **Filename:** `prd-[feature-name].md`

## Success Criteria
- All 9 PRD sections completed (metric: section coverage score)
- Success metrics are quantified with specific targets (metric: %)
- Functional requirements numbered and unambiguous
- Junior developer can understand without additional context (metric: clarity score)

## Quality Check
Before finalizing, validate:
- [ ] All sections from template Structure are present
- [ ] Success metrics are measurable
- [ ] Non-goals clearly state boundaries
- [ ] Open questions are documented

## Decision Support
When scope is unclear, suggest options:
- **Option A:** MVP scope — core functionality only
- **Option B:** Full scope — includes nice-to-haves
- **Recommend:** Option A for time-constrained projects, Option B for strategic features

## Skill Chaining
- **Before this skill:** Use `create-one-pager` for approval, and `create-design-brief` for UX context
- **After this skill:** Use `generate-tasks` to break PRD into development tasks
- **Related workflow:** `create-one-pager` → this skill → `generate-tasks` → `process-task-list`

## Final instructions

1. Do NOT start implementing the PRD
2. Make sure to ask the user clarifying questions
3. Take the user's answers to the clarifying questions and improve the PRD
