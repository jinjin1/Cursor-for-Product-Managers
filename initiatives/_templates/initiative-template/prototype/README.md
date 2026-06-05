# Prototype

This folder contains the working prototype and its companion doc for the initiative.

## Contents

- **Working Prototype**: A runnable, self-contained static app (single page or a few screens) that demonstrates the core user flow
- **Companion Doc**: A 10-question FAQ that lives next to the prototype, in place of a heavyweight PRD

## File Naming Conventions

- Companion Doc: `companion-doc-[feature-name].md`
- Prototype code: a self-contained app (e.g. `index.html`) or a small `app/` folder

## Usage

Use `/build-prototype` to generate:
- A working, clickable prototype scoped to the one flow that must work in V1
- A companion doc answering the 10 obvious questions (why, V1 must-haves, edge cases, success)
- Brand-consistent UI when a `design-system/` is present

Specify the **Input / Output / Audience** triad before the build, preview in-app, and test the
core flow before handing off — the bar is 80% with zero engineering time, with no crash on the
first click.

## Integration

- **Before**: `/generate-solutions` (selected solution), `/create-design-brief` (visual tokens), `/identify-test-assumptions` (assumption under test)
- **Parallel**: `/generate-figma-prompt` for static visual mocks — interaction test → prototype, visual exploration → Figma
- **After**: feed results back to `/identify-test-assumptions`; the prototype + companion doc become the most precise input for `/create-prd` and `/generate-tasks`

## Example Structure

```
prototype/
├── index.html                          # or app/ — the working prototype
├── companion-doc-mobile-redesign.md
└── README.md
```
