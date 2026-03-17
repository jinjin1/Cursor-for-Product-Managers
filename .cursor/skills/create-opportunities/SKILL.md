---
name: create-opportunities
description: >
  Extracts and prioritizes opportunities from interview snapshots using the Opportunity
  Solution Tree structure. Use after completing interview snapshots or synthesis to identify
  customer needs, pain points, and desires worth solving.
---

# Create and Prioritize Opportunities (Continuous Discovery Habits)

## Goal
Extract opportunities from interview snapshots based on customer needs, pain points, and desires. Organize them in an Opportunity Solution Tree structure and propose target opportunities for exploration.

## When to Use
- Use when a PM or product manager needs to identify and prioritize customer problems worth solving for an initiative
- After completing interview snapshots with [Create Interview Snapshots](/create-interview-snapshots)
- After synthesizing multiple snapshots with [Synthesize Interview Snapshots](/synthesize-snapshots)
- Before generating solutions to ensure focus on the right opportunities

## Input
- **Primary**: Interview snapshots from `user-interviews/snapshots/`
- **Secondary**: Synthesis documents from `user-interviews/synthesis/`
- **Context source**: company-level-context/ (Product Vision, Strategy, OKR, Goals — for strategic alignment)
- **Minimum**: 3-5 interview snapshots or 1 synthesis document

## Output
- **Format:** Markdown — **Location:** `opportunities/[topic]/`
- **Filename:** `opportunities-[topic]-v[version].md` (kebab-case, auto-incrementing version)
- Never overwrite existing files; always create new version

## Process

### Step 1: File Management (Pre-step)
Extract topic from content. Check existing files with pattern `opportunities-[topic]-v*.md`. Auto-increment version. Complete within 2 minutes.

### Step 2: Context Analysis (Pre-step)
Scan company-level-context/ for strategic materials. Extract vision, goals, OKR priorities, constraints. Set evaluation criteria for strategic alignment.

### Step 3: Extract Opportunities
Extract customer stories, needs, pain points, desires from snapshots. Format as:
- **Need-based**: "I want [outcome] but [barrier] makes it difficult"
- **Pain point-based**: "I feel frustrated in [situation] because of [problem]"
- **Desire-based**: "I wish I could [experience] but [constraint] prevents it"

Exclude feature suggestions; reconstruct as underlying needs. Link evidence (quotes, frequency, segments).

### Step 4: Map Opportunities
Place in Opportunity Solution Tree (Outcome > Parent > Child > Leaf). Use parent-child and sibling relationships. Merge duplicates; reconstruct disguised solutions.

### Step 5: User Review #1
Present opportunity candidate table: `ID | Parent | Statement | Evidence Count | Quotes`. Ask: "Merge/split/delete/rename any?" PAUSE for feedback.

### Step 6: Assess Opportunities
Compare sibling sets across four lenses:
1. **Opportunity Sizing** — How many customers, how frequently?
2. **Market Factors** — Table stakes vs differentiator?
3. **Company Factors** — Strategic alignment with company-level context, OKR, resource availability
4. **Customer Factors** — Importance to customers, satisfaction with alternatives?

Use discussion-based recording, not scoring.

### Step 7: User Review #2
Present priority summary: `Sibling Set | Candidates | Key Factors | Tentative Winner`. PAUSE for feedback.

### Step 8: Propose Target Opportunity
Mark a leaf node as Target Opportunity (Proposal). This is a reversible, two-way door decision.

## Success Criteria
- Coverage: 90% or more of identifiable opportunities extracted from interview data
- Evidence strength: Each opportunity backed by 2+ participants or strong behavioral evidence
- Customer language: 80% or more of statements use customer terminology
- Solution-free: 0 feature requests in opportunity statements
- Strategy alignment: Measured against company-level-context OKR/strategy

## Output Template Structure

Required sections and fields:

```markdown
# Opportunities — [Topic Name]
**Topic / Version / Source Documents / Context Sources / Total Opportunities**

## Opportunity Solution Tree (Snapshot)
- Outcome > Parent > Child > Target

## Candidate Opportunities (Pre-Review)
| ID | Parent | Statement | Evidence Count | Quotes | Notes |

## Review Notes #1
## Assessment (Sibling Comparisons)
- Candidates, Factors (Sizing, Market, Company with context reference, Customer), Discussion, Winner

## Review Notes #2
## Proposed Target Opportunity
- Rationale, Supporting Evidence, Next Steps
```

## Decision Support

- **Option A — Explore immediately**: Recommend when multiple participants mention it, strategic alignment is high, and product changes can address it. Proceed to solution generation.
- **Option B — Gather more evidence**: Suggest when evidence exists but sample is insufficient. Conduct additional interviews.
- **Option C — Deprioritize**: Recommend when evidence is weak or strategic alignment is low. Revisit next quarter or merge with other opportunities.

## Quality Review
Before finalizing, review and evaluate:
- Each opportunity describes a customer problem in customer language
- Evidence supports each opportunity; opportunities are actionable
- All mapped to solution tree; user reviews completed
- Company factors include strategic alignment analysis from context
- Iterate to improve weak opportunity statements with better evidence

## Guardrails
- Opportunities must use customer language (no internal jargon)
- Feature suggestions are NOT opportunities; reconstruct as underlying needs
- Emotions alone are not opportunities; reconstruct as actionable problems
- Use problem-focused statement format; no precise scoring
- All decisions are hypothetical and reversible

## Workflow Integration

**Before** this skill: [Create Interview Snapshots](/create-interview-snapshots) for input data.
**After** this skill: [Generate Solutions](/generate-solutions) to explore solutions for target opportunities. Also feeds into [Calculate ICE Score](/calculate-ice-score).

```
Interviews → Snapshots → Synthesize → Create Opportunities → Generate Solutions
```
