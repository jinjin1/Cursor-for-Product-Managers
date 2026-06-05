---
name: setup-initiative
description: >
  Creates a new initiative folder with standardized structure and customized templates.
  Use when starting a new product initiative to set up the complete folder structure
  with all necessary subfolders and README files.
---

# Create New Initiative Structure

Stand up a new initiative folder from the standard template and customize it.

## When to Use
- Starting a new product initiative or project
- When you need a consistent folder structure for discovery, design, and delivery

## Input
- **Required:** Initiative name (kebab-case, e.g. `mobile-app-redesign`), owner, brief goal
- **Optional:** Target timeline, key stakeholders
- **Context:** `company-level-context/okrs/` and `.../product-vision-and-strategy/` for alignment

## Output
- **Location:** `initiatives/[initiative-name]/` (kebab-case folder name)
- **Format:** Folder structure with Markdown README files

## Process
1. **Gather details** — name, owner, goal, optional timeline and stakeholders.
2. **Create the folder** — copy the entire structure from
   `initiatives/_templates/initiative-template/`, preserving all subfolders, README files,
   and `.gitkeep` files (these keep empty folders in git).
3. **Customize README.md** — replace `[Initiative Name]` and `[Product Manager Name]`,
   update the goal, add timeline/stakeholders if given; keep the rest of the template intact.

## Output Structure
```
initiatives/[initiative-name]/
├── README.md                      # Customized with initiative details
├── user-interviews/
│   ├── README.md
│   ├── snapshots/   ├── synthesis/   └── transcripts/
├── opportunities/   └── README.md
├── assumptions/     └── README.md   # Outputs from /identify-test-assumptions
├── solutions/       └── README.md   # Outputs from /generate-solutions
├── design/          └── README.md   # Design briefs and Figma Make prompts
├── product-analytics/ └── README.md
├── prd/             └── README.md
└── tasks/           └── README.md
```

Naming: kebab-case (`checkout-optimization`); add a quarter prefix if relevant
(`2024q1-mobile-redesign`); keep names descriptive.

## Quality bar
- Every template folder and README is copied (including `design/`) with `.gitkeep` files intact.
- README.md customized with all placeholders replaced; folder structure matches the template.
- Initiative ties to at least one company OKR or strategic goal.
- For a well-defined feature, a lightweight subset (prd/, tasks/, design/) is fine; default to the full structure for discovery-driven work.

## Skill Integration
- **Before:** align the initiative with `company-level-context/`.
- **After (per subfolder):** [create-interview-snapshots](/create-interview-snapshots) → `user-interviews/snapshots/`,
  [create-opportunities](/create-opportunities) → `opportunities/`, [generate-solutions](/generate-solutions) → `solutions/`,
  [identify-test-assumptions](/identify-test-assumptions) → `assumptions/`, [create-one-pager](/create-one-pager) / [create-prd](/create-prd) → `prd/`,
  [create-design-brief](/create-design-brief) / [generate-figma-prompt](/generate-figma-prompt) → `design/`, [generate-tasks](/generate-tasks) → `tasks/`,
  [analyze-metrics](/analyze-metrics) → `product-analytics/`.
