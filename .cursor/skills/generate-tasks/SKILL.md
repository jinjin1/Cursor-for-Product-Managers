---
name: generate-tasks
description: >
  Creates detailed step-by-step task lists from user requirements or PRDs. Use when
  breaking down feature requests into actionable implementation tasks for developers.
---

# Generating a Task List from a PRD

Break a PRD or feature request into a step-by-step task list a developer can implement.
Written for a junior developer: explicit and actionable.

## When to Use
- Breaking a PRD or feature request into development tasks
- Creating an implementation plan or organizing work for sprint planning

## Input
- **Required:** Feature request, PRD, or requirements document
- **Optional:** Existing codebase context, tech stack
- **Context:** `company-level-context/` for alignment, `prd/` for requirements

## Output
- **Format:** Markdown — **Location:** `tasks/` (the initiative's `tasks/` directory)
- **Filename:** `tasks-[feature-name].md` (e.g., `tasks-user-profile-editing.md`)

## Process

1. **Analyze requirements** — functional requirements, user needs, implementation scope.
2. **Phase 1 — parent tasks:** generate the high-level tasks (about 5; use judgment).
   Always include task `0.0 Create feature branch` first, unless the user opts out.
   Present parent tasks only, then ask: "Ready to generate the sub-tasks? Respond 'Go' to proceed."
3. **Wait for "Go"** before expanding — this confirms the high-level plan first.
4. **Phase 2 — sub-tasks:** break each parent task into specific, atomic sub-tasks.
5. **Relevant Files** — list files likely created/modified, with their test files, matching
   the project's conventions and test framework.
6. **Assemble** the final list using the format below.

## Output Format

```markdown
## Relevant Files

- `path/to/component` - Why this file is relevant (e.g., main component for the feature).
- `path/to/component.test` - Tests for the component.
- `path/to/api-handler` - e.g., API route handler for data submission.

### Notes
- Co-locate tests with the code they cover, following the project's conventions.
- Run tests with the project's test command (see the repo's README / config).

## Tasks

- [ ] 0.0 Create feature branch
  - [ ] 0.1 Create and checkout a new branch (e.g., `git checkout -b feature/[feature-name]`)
- [ ] 1.0 Parent Task Title
  - [ ] 1.1 [Sub-task description]
  - [ ] 1.2 [Sub-task description]
- [ ] 2.0 Parent Task Title
  - [ ] 2.1 [Sub-task description]
- [ ] 3.0 Parent Task Title (may need no sub-tasks if purely structural/config)
```

As each task is completed, check it off in the file (`- [ ]` → `- [x]`) after every
sub-task, not just at the end of a parent task.

## Quality bar
- Numbered format (0.0, 1.0, 2.0…); sub-tasks specific and atomic; task 0.0 present.
- Relevant Files section accurately identifies affected areas, with test files.
- Each task is actionable by a junior developer; task count fits the feature's complexity.
- Pause for "Go" after parent tasks; offer minimal vs full scope when scope is ambiguous.

## Skill Integration
- **Before:** [create-prd](/create-prd) for requirements, or [create-one-pager](/create-one-pager) for scope.
- **After:** execute the task list, checking off each sub-task as you complete it.
- **Workflow:** create-prd → this skill → task execution
