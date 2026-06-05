---
name: create-opportunities
description: >
  Extracts and prioritizes opportunities from interview snapshots using the Opportunity
  Solution Tree structure. Use after completing interview snapshots or synthesis to identify
  customer needs, pain points, and desires worth solving.
---

# Create and Prioritize Opportunities (Continuous Discovery Habits)

Extract opportunities (customer needs, pain points, desires) from research, organize
them in an Opportunity Solution Tree, and propose a target opportunity to explore.

## When to Use
- Identifying and prioritizing customer problems worth solving for an initiative
- After [Create Interview Snapshots](/create-interview-snapshots) or [Synthesize Snapshots](/synthesize-snapshots)
- Before generating solutions, to focus on the right problem

## Input
- **Primary:** Interview snapshots from `user-interviews/snapshots/`
- **Secondary:** Synthesis documents from `user-interviews/synthesis/`
- **Context:** `company-level-context/` (Vision, Strategy, OKR, Goals) for strategic alignment
- **Minimum:** 3-5 snapshots or 1 synthesis document

## Output
- **Format:** Markdown — **Location:** `opportunities/` (the initiative's `opportunities/` directory)
- **Filename:** `opportunities-[topic]-v[version].md` (kebab-case, auto-increment; never overwrite)

## Process

### Step 1: Set up and scan context
Pick the topic and next version number. Scan `company-level-context/` for vision, goals,
OKR priorities, and constraints to use as alignment criteria.

### Step 2: Extract opportunities
Pull customer stories, needs, pain points, and desires from the snapshots. Frame each as:
- **Need:** "I want [outcome] but [barrier] makes it difficult"
- **Pain point:** "I feel frustrated in [situation] because of [problem]"
- **Desire:** "I wish I could [experience] but [constraint] prevents it"

Exclude feature suggestions — reconstruct them as the underlying need. Link evidence
(quotes, frequency, segments).

### Step 3: Map into the Opportunity Solution Tree
Place opportunities in the tree (Outcome > Parent > Child > Leaf) using parent-child and
sibling relationships. Merge duplicates; reconstruct any disguised solutions.

### Step 4: User review #1
Present the candidate table (`ID | Parent | Statement | Evidence Count | Quotes`) and
ask whether to merge/split/delete/rename any. Pause for feedback.

### Step 5: Assess sibling sets
Compare siblings across four lenses (discussion, not scoring):
1. **Opportunity Sizing** — how many customers, how often?
2. **Market** — table stakes vs differentiator?
3. **Company** — alignment with company-level context, OKR, resources?
4. **Customer** — importance, and satisfaction with alternatives?

### Step 6: User review #2
Present the priority summary (`Sibling Set | Candidates | Key Factors | Tentative Winner`).
Pause for feedback.

### Step 7: Propose target opportunity
Mark a leaf node as the Target Opportunity (a reversible, two-way-door proposal).

## Output Template

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

## Quality bar
- Every opportunity states a customer problem in customer language — no internal jargon, no feature requests, no bare emotions.
- Each is backed by 2+ participants or strong behavioral evidence, and mapped to the tree.
- Company-factor assessment references the strategic context; both user reviews completed.
- Decisions are hypothetical and reversible — explore now, gather more evidence, or deprioritize.

## Skill Integration
- **Before:** [Create Interview Snapshots](/create-interview-snapshots) / [Synthesize Snapshots](/synthesize-snapshots); [Analyze Metrics](/analyze-metrics) for the Opportunity Sizing lens.
- **After:** [Generate Solutions](/generate-solutions); also feeds [Calculate ICE Score](/calculate-ice-score)
- **Workflow:** Interviews → Snapshots → Synthesize → Create Opportunities → Generate Solutions
