---
name: generate-figma-prompt
description: >
  Generates Figma Make-ready prompts based on design briefs and design systems. Use when
  creating automated design generation prompts for Figma Make, with character limit
  optimization and design token mapping.
---

# Generate Figma Make Prompt

## Goal
Generate **Figma Make-ready prompts** based on design briefs and design systems. Output follows `tool`, `setup`, `pages` structure reflecting brand identity and design tokens. **Critical constraint**: maximum 5000 characters.

## When to Use
- Use when a PM or product manager needs Figma Make auto-generation prompts from a design brief for an initiative
- When converting design system tokens to Figma Make format
- When automating prototype, ad, or social media design generation
- When consistent JSON specifications are needed for design tooling

## Input
- **Primary**: Design brief JSON from `initiatives/[initiative-name]/design/`
- **Context source**: company-level-context/ (brand guidelines, strategic direction)
- **Design system**: Current repo's design-system/ tokens and components
- **Required**: At least a design brief JSON or product/campaign objectives

## Output
- **Location:** `initiatives/[initiative-name]/design/`
- **Filename:** `figma-make-prompt-[feature-name].json`

## Process

1. Validate inputs and gather context
2. Execute core analysis
3. Generate output and review results
4. Iterate based on feedback


### Step 1: Design Brief Intake
Collect objectives, audience, components, and patterns from existing design brief JSON. Complete within 10 minutes.

### Step 2: Design System Reference
Reference tokens and components from the repo's design system.

### Step 3: Structural Constraint Application
Apply limits: max 2 pages, 6 components/page, 8 copy items/page.

### Step 4: Token Mapping
Map design system tokens to Figma Make format with abbreviations (backgroundColor > bg, width > w).

### Step 5: Component Optimization
Select core variants. Limit props to essentials (bg, color, borderRadius).

### Step 6: Balanced Formatting
Apply 2-space indentation. Compress props/position to single lines.

### Step 7: Character Validation
Ensure total JSON is under 5000 characters. If over, reduce pages to 1 or components to 4/page.

### Step 8: File Storage
Save to `initiatives/[initiative-name]/design/` folder.

## JSON Schema Template

Required structure with sections and fields:

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

## Character Limits
- **Total**: 5000 chars max | **Pages**: 2 max | **Components/page**: 6 max
- **Copy/page**: 8 max | **Layout desc**: 200 chars | **Theme**: 50 chars

## Generation Rules
- **Naming**: component name + variant only
- **Props**: limit to 3 core (bg, color, borderRadius)
- **Position**: abbreviated (x, y, w, h)
- **Indentation**: 2-space throughout
- **Compression**: props and position on single lines; consolidate repeated props
- **Abbreviations**: backgroundColor > bg, textColor > color, width > w, height > h

## Success Criteria
- JSON under 5000 characters with 100% compliance
- All required keys present (tool, setup, pages) with valid structure
- Design system tokens correctly mapped at 95% accuracy or higher
- Brand values and identity consistent across all components

## Design System Mapping
- **Token**: `color.semantic.accent.brand` > `"primary": "<color>"`
- **Spacing**: `spacing.6` > `"w": 24`
- **Typography**: `typography.fontSize.base` > `"16px"`
- **Components**: Use only core variants, limit props to 3

## Decision Support

- **Option A — Full Fidelity**: Recommend for final design handoff. Max 2 pages, 6 components each, detailed token mapping.
- **Option B — Single Page Focus**: Suggest for rapid prototyping. 1 page, 4 core components for faster iteration.
- **Option C — Minimal Skeleton**: Recommend for early concept exploration. 1 page, 2-3 components, minimal copy.

Selection depends on project phase, character budget, and review purpose.

## Quality Review
Before finalizing, validate and evaluate:
- Character count under 5000; required keys present
- Design tokens correctly mapped; component names match design system
- Brand alignment consistent; indentation and compression correct
- Iterate to improve compression if over character limit

## Troubleshooting
- **Over 5000 chars**: Reduce to 1 page, 4 components, compress descriptions
- **Invalid JSON**: Verify required keys and proper nesting
- **Missing tokens**: Map to existing tokens or use fallback values

## Workflow Integration

**Before** this skill: [Create Design Brief](/create-design-brief) for design brief JSON input.
**After** this skill: Import JSON directly into Figma Make for automated design generation.

```
Opportunities → ICE Score → Design Brief → Figma Prompt → Figma Make
```
