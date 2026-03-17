---
name: create-design-brief
description: >
  Generates consistent design briefs with machine-readable JSON specifications and
  stakeholder-friendly Markdown summaries. Use when creating design specifications for
  Figma, prototyping tools, or design handoff documents.
---

# Create a Design Brief

## Goal
Generate consistent design briefs outputting both **machine-readable JSON** (for Figma/Make and prototyping tools) and **stakeholder-friendly Markdown**. Leverage the repo's design system (tokens, components) for reusability across advertising, prototyping, branding, and social media.

## When to Use
- Use when a PM or product manager needs design specifications for a new feature or initiative
- When creating Figma, prototyping, or design handoff documents
- When ensuring design consistency across ads, branding, social media, and prototypes
- When building reusable component specs from an existing design system

## Input
- **Primary**: Product/campaign objectives, constraints, deadlines, stakeholders
- **Context source**: company-level-context/ (strategic goals, brand guidelines, product vision)
- **Design system**: Existing design-system/ folder tokens and components
- **Required**: At least product objective, target audience, and key components

## Output
- **Location:** `initiatives/[initiative-name]/design/`
- **Files:** `design-brief-[feature-name].json` + `design-brief-[feature-name].md`

## Process

1. Validate inputs and gather context
2. Execute core analysis
3. Generate output and review results
4. Iterate based on feedback


### Step 1: Brief Intake
Collect product/campaign objectives, constraints (regulations, brand guidelines), deadlines, and key stakeholders. Complete within 5 minutes.

### Step 2: Design System Reference
Reference tokens and components from the repo's `design-system/` folder.

### Step 3: Library Mapping
Prioritize existing components/patterns. Minimize new creation.

### Step 4: Token-First Definition
Define color, typography, spacing variables first, then inject into components.

### Step 5: Channel Consistency
Ensure Ads/Branding/Social/Prototype share the same variables and copy principles.

### Step 6: Accessibility Gate
Check WCAG 2.2 AA, minimum 44px touch targets, RTL/multilingual support.

### Step 7: Dual-Track Output
Generate JSON (tool input) + Markdown (review) simultaneously.

### Step 8: File Storage
Save to `initiatives/[initiative-name]/design/` folder.

## JSON Schema (Required Root Keys)

`meta`, `purpose`, `audience`, `tone`, `brand_voice`, `variables`, `components`, `patterns`, `channels`, `deliverables`, `a11y`, `naming`, `file_structure`, `metrics`, `assets`

Key sections and fields:
- **meta**: version, date, locale, brand, design_system (source, paths), sources
- **audience**: primary, secondary, personas, context
- **variables**: color (semantic, neutral), typography (family, sizes, weights), spacing, radius, elevation, motion
- **components**: name, library_ref, variants, props, content_guidelines, interactions
- **channels**: ads, branding, social (formats/rules), prototype (flows/transitions)
- **a11y**: contrast (WCAG 2.2 AA), min_touch (44), focus_visible, rtl, keyboard_navigation
- **metrics**: primary, secondary, success_criteria (e.g., ">15% CTR improvement")

## Markdown Summary Structure

Required template sections:
- Purpose & Audience
- Tone & Brand Voice (Do/Don't guidelines)
- Design Variables (Tokens) Summary
- Component Library Mapping & Variant Table
- Patterns & Flows
- Channel-Specific Guidelines
- Accessibility & Internationalization
- Naming Conventions & File Structure
- Success Metrics & Experiment Plan
- Asset Guidelines

## Success Criteria
- JSON contains 100% of required root keys
- All token references map to existing design-system/ values or marked "proposed"
- Accessibility: WCAG 2.2 AA compliance verified at 100%
- Success metrics are measurable with target % defined (e.g., >15% CTR improvement)

## Generation Rules
- Use `"Button/Primary"` format for component references; mark unavailable ones as `"proposed"`
- Use `dot.case` for tokens, slash-naming for components
- Include measurable success criteria and experiment hypotheses
- Attach research/benchmark sources in `meta.sources[]`
- Include responsive breakpoints and mobile-first approach

## Decision Support

- **Option A — Full Design System**: Recommend when brand consistency is critical. All existing tokens/components, no custom elements.
- **Option B — Extended Design System**: Recommend when existing components don't cover requirements. Extend with "proposed" components.
- **Option C — Minimal Viable Design**: Suggest for rapid prototyping or MVPs. Core components only (Button, Card, Banner).

For channel selection, recommend prioritizing based on campaign objectives and strategic alignment with company-level context.

## Quality Review
Before finalizing, review and evaluate:
- JSON schema has all required root keys
- All design tokens reference existing design-system/ values
- Component library references are valid or marked "proposed"
- Accessibility requirements met; channel guidelines consistent
- Success metrics are measurable; brand voice includes Do/Don'ts
- Iterate and improve based on stakeholder feedback

## Workflow Integration

**Before** this skill: [Calculate ICE Score](/calculate-ice-score) for prioritized ideas, [Create Opportunities](/create-opportunities) for design objectives.
**After** this skill: [Generate Figma Prompt](/generate-figma-prompt) — design brief JSON feeds into Figma Make prompt generation.

```
Opportunities → ICE Score → Design Brief → Figma Prompt
```
