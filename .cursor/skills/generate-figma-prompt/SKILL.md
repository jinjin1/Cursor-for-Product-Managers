---
name: generate-figma-prompt
description: >
  Generates Figma Make-ready prompts based on design briefs and design systems. Use when
  creating automated design generation prompts for Figma Make, with character limit
  optimization and design token mapping.
---

# Generate Figma Make Prompt

Turn a design brief into a Figma Make-ready prompt in `tool` / `setup` / `pages` structure,
reflecting brand identity and design tokens. **Hard constraint: 5000 characters max.**

## When to Use
- Producing Figma Make auto-generation prompts from a design brief
- Converting design-system tokens to Figma Make format for prototypes, ads, or social designs

## Input
- **Primary:** Design brief JSON from the initiative's `design/` directory
- **Context:** `company-level-context/` (brand guidelines, direction)
- **Design system:** repo `design-system/` tokens and components
- **Required:** a design brief JSON, or product/campaign objectives

## Output
- **Location:** `design/` (the initiative's `design/` directory)
- **Filename:** `figma-make-prompt-[feature-name].json`

## Process
1. **Intake** — pull objectives, audience, components, and patterns from the design brief JSON.
2. **Reference the design system** — tokens and components.
3. **Apply structural limits** — max 2 pages, 6 components/page, 8 copy items/page.
4. **Map tokens** — to Figma Make format with abbreviations (`backgroundColor` → `bg`, `width` → `w`).
5. **Optimize components** — core variants only; limit props to essentials (bg, color, borderRadius).
6. **Format** — 2-space indentation; compress props/position to single lines.
7. **Validate character count** — keep total under 5000; if over, drop to 1 page or 4 components/page.
8. **Save** to the `design/` folder.

## JSON Schema Template

```json
{
  "tool": "Figma Make",
  "setup": {
    "theme": "<50 chars max>",
    "grid": "<core grid>",
    "typography": "<3 sizes>",
    "colors": ["<7 essential colors>"],
    "brand": {"name": "<>", "primary": "<>", "bg": "<>", "text": "<>"}
  },
  "pages": [{
    "name": "<page name>",
    "layout": "<200 chars max>",
    "components": [{"name": "<>", "variant": "<>", "props": {}, "position": {"x":0,"y":0,"w":100,"h":50}}],
    "copy": [{"key": "<>", "text": "<>", "component": "<>"}]
  }]
}
```

## Limits and mapping
- **Budget:** 5000 chars total · 2 pages · 6 components/page · 8 copy/page · layout 200 chars · theme 50 chars.
- **Token mapping:** `color.semantic.accent.brand` → `"primary"`, `spacing.6` → `"w": 24`, `typography.fontSize.base` → `"16px"`.
- **Compression:** component name + variant only; 3 core props (bg, color, borderRadius); abbreviate position (x, y, w, h); single-line props/position.

## Quality bar
- Under 5000 characters; required keys present (`tool`, `setup`, `pages`) with valid nesting.
- Tokens mapped correctly; component names match the design system; brand identity consistent.
- If over budget: reduce to 1 page / 4 components and compress descriptions.
- Scope to phase: full fidelity (handoff), single-page (rapid prototyping), or minimal skeleton (concept).

## Skill Integration
- **Before:** [Create Design Brief](/create-design-brief) for the design brief JSON.
- **Parallel:** [Build Prototype](/build-prototype) for a working, clickable prototype — this skill is the static-visual branch; use it for visual exploration, build-prototype for interaction/flow.
- **After:** import the JSON into Figma Make for automated design generation.
- **Workflow:** Opportunities → ICE Score → Design Brief → Figma Prompt → Figma Make
