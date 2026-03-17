---
name: setup-initiative
description: >
  Creates a new initiative folder with standardized structure and customized templates.
  Use when starting a new product initiative to set up the complete folder structure
  with all necessary subfolders and README files.
---

# Create New Initiative Structure

## Goal
Create a new initiative folder with standardized structure and populate with customized templates from the initiative template.

## When to Use (활용 시나리오)
- When starting a new product initiative or project
- When a PM needs a consistent folder structure for discovery, design, and delivery
- When onboarding a new initiative into the team's workflow
- 적용 대상: 구조화된 PM 아티팩트가 필요한 모든 사용 상황

## Input
- **Required:** Initiative name (kebab-case: e.g., 'mobile-app-redesign')
- **Required:** Owner/Product Manager name
- **Required:** Brief description of the initiative goal
- **Optional:** Target timeline, key stakeholders
- **Context Source:** Reference `company-level-context/okrs/` and `company-level-context/product-vision-and-strategy/` to align initiative with strategic direction

## Output
- **Format:** Folder structure with Markdown (`.md`) files
- **Location:** `initiatives/[initiative-name]/`
- **Filename convention:** kebab-case initiative name as folder

## Process (단계별 워크플로우)
1. **Gather Initiative Details**
   - Initiative name (use kebab-case: e.g., 'mobile-app-redesign')
   - Owner/Product Manager name
   - Brief description of the initiative goal
   - Target timeline (optional)
   - Key stakeholders (optional)

2. **Create Initiative Folder Structure**
   - Create `initiatives/[initiative-name]/` folder
   - Copy entire structure from `initiatives/_templates/initiative-template/`
   - Preserve all subfolders and README files

3. **Customize README.md**
   - Replace `[Initiative Name]` with the actual initiative name
   - Replace `[Product Manager Name]` with the owner's name
   - Update the goal description
   - Add timeline if provided
   - Add stakeholders if provided
   - Keep all other template content intact

4. **Initialize Placeholder Files**
   - Create `.gitkeep` files in empty folders to preserve structure
   - Ensure all subfolder README files are properly copied
   - Maintain file permissions and structure
   - **Critical:** Preserve all `.gitkeep` files from template to maintain empty folder structure

## Success Criteria
- All template folders and files are created (score: completeness 100%)
- README.md is customized with initiative-specific details (metric: all placeholders replaced)
- Folder structure matches the template exactly
- Initiative aligns with at least one company OKR or strategic goal

## Decision Support
When the user provides ambiguous initiative scope, suggest options:
- **Option A:** Full initiative structure (all subfolders)
- **Option B:** Lightweight structure (only prd/, tasks/, design/)
- **Recommend:** Option A for discovery-driven initiatives, Option B for well-defined features

## Quality Check
After creation, validate:
- [ ] All folders from template are copied (including design folder)
- [ ] README.md is properly customized
- [ ] All subfolder README files are present
- [ ] Folder structure matches the template exactly
- [ ] Initiative name follows naming conventions

## Naming Conventions
- **Initiative Folder:** Use kebab-case (e.g., `mobile-app-redesign`, `checkout-optimization`)
- **Include Quarter:** If relevant, add quarter prefix (e.g., `2024q1-mobile-redesign`)
- **Keep Descriptive:** Use clear, meaningful names that describe the initiative

## Output Structure
```
initiatives/[initiative-name]/
├── README.md                      # Customized with initiative details
├── user-interviews/
│   ├── README.md
│   ├── snapshots/
│   ├── synthesis/
│   └── transcripts/
├── opportunities/
│   └── README.md
├── assumptions/
│   └── README.md                  # Outputs from /identify-test-assumptions
├── solutions/
│   └── README.md                  # Outputs from /generate-solutions
├── design/
│   └── README.md                  # Design briefs and Figma Make prompts
├── product-analytics/
│   └── README.md
├── prd/
│   └── README.md
└── tasks/
    └── README.md
```

## Skill Chaining
- **Before this skill:** Align initiative with company strategy from `company-level-context/`
- **After this skill:** Begin discovery with `create-interview-snapshots` or define scope with `create-one-pager`

## Integration Points
After creating the initiative structure, remind the user about these workflow integrations:

- **User Research:** Use `/create-interview-snapshots` in `user-interviews/snapshots/`
- **Design Briefs:** Use `/create-design-brief` in `design/` folder
- **Figma Make Prompts:** Use `/generate-figma-prompt` in `design/` folder
- **PRD Creation:** Use `/create-prd` in `prd/` folder
- **Task Generation:** Use `/generate-tasks` with the PRD to create tasks in `tasks/` folder
- **Assumption Identification:** Use `/identify-test-assumptions`; outputs saved to `assumptions/`
- **Solution Generation:** Use `/generate-solutions`; outputs saved to `solutions/`

## Validation
Ensure the following after creation:
- [ ] All folders from template are copied (including design folder)
- [ ] README.md is properly customized
- [ ] All subfolder README files are present
- [ ] Folder structure matches the template exactly
- [ ] Initiative name follows naming conventions

## Success Message
After successful creation, provide:
- Confirmation of the new initiative folder location
- Quick start guide for next steps
- Links to relevant workflow tools (including design brief and Figma Make prompt tools)
- Reminder about folder structure and integration points

## Example Usage
```
User: "Create a new initiative for mobile app redesign, owned by Sarah Kim"

AI Response: 
- Creates: initiatives/mobile-app-redesign/
- Customizes README with "Mobile App Redesign" and "Sarah Kim"
- Provides next steps for user research, design brief creation, and PRD creation
```

---
*This script automates the tedious setup process while ensuring consistency across all initiatives.*
