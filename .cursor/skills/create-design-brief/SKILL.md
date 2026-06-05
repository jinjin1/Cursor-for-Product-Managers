---
name: create-design-brief
description: >
  Generates consistent design briefs with machine-readable JSON specifications and
  stakeholder-friendly Markdown summaries. Use when creating design specifications for
  Figma, prototyping tools, or design handoff documents.
---

# Create a Design Brief

Generate a design brief in two forms at once: **machine-readable JSON** (for Figma Make
and prototyping tools) and **stakeholder-friendly Markdown**. Build on the repo's design
system (tokens, components) for reuse.

## When to Use
- Producing design specifications for a new feature or initiative
- Creating Figma / prototyping / design-handoff documents
- Keeping design consistent across ads, branding, social, and prototypes

## Input
- **Primary:** Product/campaign objectives, constraints, deadlines, stakeholders
- **Context:** `company-level-context/` (goals, brand guidelines, vision)
- **Design system:** existing `design-system/` tokens and components
- **Required:** at least a product objective, target audience, and key components

## Output
- **Location:** `design/` (the initiative's `design/` directory)
- **Files:** `design-brief-[feature-name].json` + `design-brief-[feature-name].md`

## Process
1. **Intake** — objectives, constraints (regulations, brand), deadlines, stakeholders.
2. **Reference the design system** — tokens and components from `design-system/`.
3. **Map to existing components first** — minimize new creation; mark gaps as `"proposed"`.
4. **Token-first** — define color, typography, spacing variables, then inject into components.
5. **Channel consistency** — ads / branding / social / prototype share the same variables and copy principles.
6. **Accessibility gate** — WCAG 2.2 AA, minimum 44px touch targets, RTL/multilingual support.
7. **Dual-track output** — generate the JSON and Markdown together; save to the `design/` folder.

## JSON Schema (required root keys)
`meta`, `purpose`, `audience`, `tone`, `brand_voice`, `variables`, `components`, `patterns`,
`channels`, `deliverables`, `a11y`, `naming`, `file_structure`, `metrics`, `assets`

Key fields:
- **meta:** version, date, locale, brand, design_system (source, paths), sources
- **audience:** primary, secondary, personas, context
- **variables:** color (semantic, neutral), typography (family, sizes, weights), spacing, radius, elevation, motion
- **components:** name, library_ref, variants, props, content_guidelines, interactions
- **channels:** ads, branding, social (formats/rules), prototype (flows/transitions)
- **a11y:** contrast (WCAG 2.2 AA), min_touch (44), focus_visible, rtl, keyboard_navigation
- **metrics:** primary, secondary, success_criteria (e.g., ">15% CTR improvement")

## Markdown Summary Structure
Purpose & Audience · Tone & Brand Voice (Do/Don't) · Design Variables (Tokens) · Component
Library Mapping & Variant Table · Patterns & Flows · Channel-Specific Guidelines ·
Accessibility & Internationalization · Naming & File Structure · Success Metrics & Experiment
Plan · Asset Guidelines

## Quality bar
- JSON has all required root keys; tokens reference existing `design-system/` values or are marked `"proposed"`.
- Component references use `"Button/Primary"` format; tokens use `dot.case`.
- Accessibility (WCAG 2.2 AA, 44px touch, RTL) met; channels share the same variables.
- Success metrics are measurable with a target; brand voice includes Do/Don'ts; sources attached in `meta.sources[]`.
- Scope to fit: full design system, extended (with `"proposed"` components), or minimal (core components) for MVPs.

## Skill Integration
- **Before:** [Calculate ICE Score](/calculate-ice-score), [Create Opportunities](/create-opportunities) for objectives.
- **After:** [Generate Figma Prompt](/generate-figma-prompt) — the brief's JSON feeds Figma Make prompt generation.
- **Workflow:** Opportunities → ICE Score → Design Brief → Figma Prompt
