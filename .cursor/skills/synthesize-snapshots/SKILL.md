---
name: synthesize-snapshots
description: >
  Synthesizes multiple interview snapshots to identify common patterns, integrates
  experience maps, and creates comprehensive insights. Use after completing multiple
  interviews on the same topic or when identifying shared patterns across user segments.
---

# Synthesize Interview Snapshots

## When to Use
- Use when a PM or product manager has completed 3-5+ interviews on the same initiative topic
- When identifying shared patterns across different user segments
- Before creating opportunities or generating solutions in the discovery workflow
- When sharing research findings with stakeholders

## Input
- **Required:** Minimum 3-5 interview snapshots from [Create Interview Snapshots](/create-interview-snapshots)
- **Context:** Reference `company-level-context/` for company-level strategic priorities and OKR alignment
- **Quality gate:** All snapshots must follow consistent format with concrete behavioral details

## Output
- **Format:** Markdown, saved to `user-interviews/synthesis/`
- **Filename:** `synthesis-[initiative-name]-v[version].md` (kebab-case, auto-increment)
- **Template structure:** Required sections include Executive Summary, Participant Overview, Top Opportunities, Integrated Experience Map, Key Insights, Research Gaps, Next Steps
- **Version management:** Check existing files before creation; never overwrite previous synthesis versions

## Process

### Step 1: Data preparation
1. Gather all relevant interview snapshots for the initiative
2. Check for existing synthesis files (support incremental updates)
3. If previous synthesis exists, identify only new/unprocessed snapshots
4. Standardize format and verify completeness

### Step 2: Pattern analysis
1. Extract recurring themes, behaviors, and pain points across snapshots
2. Review each snapshot's experience map for overlaps and divergences
3. Document how different segments behave differently
4. Count frequency and assess intensity of each pattern

### Step 3: Experience map integration
1. Overlay individual experience maps; identify common stages
2. Consolidate similar activities into shared stages with logical flow
3. For each stage, document: common actions, shared thoughts, emotional journey, pain points, workarounds, segment variations
4. Attach supporting quotes from multiple participants

### Step 4: Insight development and opportunity identification
1. Synthesize patterns into actionable insights with supporting evidence
2. Write opportunities in user perspective: "I want to... but... because..."
3. Rate each opportunity by frequency, evidence strength, and impact
4. Identify research gaps and unanswered questions

### Step 5: Review and validate
1. Evaluate whether patterns have sufficient multi-participant evidence
2. Check for confirmation bias; actively look for contradictory evidence
3. Validate that insights are actionable, not just descriptive
4. Improve synthesis quality by iterating on weak evidence areas

## Success Criteria
- Minimum 3 common patterns identified across participants (target: 80% coverage)
- Each insight supported by evidence from 2+ participants
- All identified user segments have pattern analysis coverage
- At least 2 actionable opportunities identified per synthesis
- Data quality assessment average score of 70/100 or higher

## Decision Support
When synthesis reveals conflicting patterns, recommend options:
- **Option A: Deepen research** — Suggest additional interviews to resolve ambiguity
- **Option B: Segment the findings** — Recommend splitting insights by user segment
- **Option C: Proceed with caveats** — Document uncertainty and flag for future validation

## Context Preservation
- Reference `company-level-context/` strategy documents to align research direction
- Prioritize patterns that connect to company-level OKR and product vision
- Track which snapshots were included in each synthesis version for context continuity
- Preserve existing synthesis insights when doing incremental updates

## Self-Evaluation
- Review pattern quality: Are they behavioral and specific, or vague generalizations?
- Evaluate evidence strength: Multiple sources? Concrete examples?
- Validate segment coverage: Are all user types represented?
- Improve by checking for common mistakes: over-generalization, confirmation bias, jumping to solutions
- Iterate: Use feedback from opportunity creation to refine future synthesis

<<<<<<< Updated upstream
**Initiative Name Process:**
1. Use current initiative folder name as primary identifier
2. Ensure initiative name is kebab-case format (e.g., "live-sports-vod-conversion")
3. Maintain consistency across all synthesis files for same initiative
=======
## Skill Integration
- **Before this skill:** Complete interviews using [Create Interview Snapshots](/create-interview-snapshots)
- **After this skill:** Use synthesis to feed [Create Opportunities](/create-opportunities) and [Generate Solutions](/generate-solutions)
- **Workflow:** Interviews > Snapshots > Synthesis > Opportunities > Solutions > Assumption Testing
>>>>>>> Stashed changes

## Output Template Structure

<<<<<<< Updated upstream
**Initiative Name Usage:**
- **Folder-Based**: Use current initiative folder name directly
- **Consistency**: Use same initiative name across all synthesis versions
- **Kebab-Case Format**: Ensure initiative name is kebab-case (e.g., "live-sports-vod-conversion")
- **Uniqueness**: Each initiative has its own synthesis files
- **No Extraction**: No need to extract or analyze content for naming

### Pattern Recognition Guidelines
- **Focus on Behavioral Patterns**: Look for concrete actions, not opinions
- **Identify Emotional Journeys**: Map frustration, delight, confusion patterns
- **Document Workarounds**: Note how users currently solve problems
- **Preserve Context**: Maintain when/where/why details from individual stories

### Quality Standards
- **Evidence Strength**: Multiple participants supporting each pattern
- **Behavioral Specificity**: Concrete examples, not generalizations
- **Segment Clarity**: Clear understanding of user group differences
- **Actionable Insights**: Patterns that inform product decisions
- **Writing Standards**: Follow the `/writing-guide` skill rules for voice, tone, banned words, and LLM pattern avoidance

---

## Framework Structure

### 1. Data Preparation
- **Interview Collection**: Gather all relevant interview snapshots
- **Existing Synthesis Check**: Look for previous synthesis files in the same initiative area
- **New Snapshot Identification**: Compare current snapshots with previously processed ones
- **Data Standardization**: Ensure consistent format and structure across snapshots
- **Quality Check**: Verify all snapshots are complete and accurate
- **Context Documentation**: Note any relevant background information

### 1.1 Incremental Processing (Efficiency Mode)
- **Processed Snapshot Tracking**: Identify which snapshots were already analyzed in previous synthesis
- **New Data Focus**: Analyze only new snapshots that haven't been processed
- **Pattern Comparison**: Compare new patterns with existing synthesis patterns
- **Merge Strategy**: Determine how to integrate new insights with existing synthesis

### 2. Pattern Analysis
- **Extract Common Elements**: Identify recurring themes, behaviors, and pain points
- **Map Individual Journeys**: Review each snapshot's experience map
- **Find Overlaps**: Discover where individual stories intersect
- **Identify Variations**: Document how different segments behave differently

### 2.1 Incremental Pattern Analysis
- **New Pattern Detection**: Identify patterns that emerge only from new snapshots
- **Existing Pattern Validation**: Check if new data confirms or contradicts existing patterns
- **Frequency Updates**: Update pattern frequency counts with new data
- **Segment Variation Updates**: Add new segment variations discovered in new snapshots

### 3. Pattern Integration
- **Group Similar Patterns**: Cluster related insights and behaviors
- **Merge Experience Maps**: Combine individual journey stages into shared stages
- **Preserve Unique Elements**: Maintain important segment-specific details
- **Create Shared Narrative**: Develop a comprehensive story that represents all users

### 3.1 Incremental Integration
- **Merge with Existing Synthesis**: Integrate new patterns with previously identified patterns
- **Update Experience Maps**: Add new journey stages or modify existing ones based on new data
- **Preserve Previous Insights**: Maintain valuable insights from previous synthesis
- **Update Evidence Base**: Add new supporting quotes and observations to existing patterns

### 4. Insight Development
- **Common Patterns**: What patterns emerge across interviews?
- **User Segments**: Are there distinct groups with different needs?
- **Pain Point Clusters**: What problems appear most frequently?
- **Behavior Patterns**: What consistent behaviors do you observe?

---

## Process Flow

### Continuous Discovery Workflow
```
Individual Interviews → Create Snapshots → Synthesize Patterns → Generate Opportunities → Create Solutions
     ↓                    ↓                    ↓                    ↓                    ↓
[Raw Data]        [Structured Stories]   [Shared Patterns]    [Problem Statements] [Product Ideas]
```

### Incremental Synthesis Workflow (Efficiency Mode)
```
New Snapshots → Use Initiative Name → Check Existing Synthesis → Process Only New Data → Merge with Existing → Updated Synthesis
     ↓              ↓                    ↓                        ↓                    ↓                    ↓
[New Data]    [Initiative Analysis]    [Previous Analysis]      [Pattern Comparison]   [Integration]      [Enhanced Output]
```

### Input-Output Relationship
- **Input:** 3-5 completed interview snapshots from create-interview-snapshots
- **Process:** Initiative name usage, pattern recognition, experience map integration, insight synthesis
- **Output:** Comprehensive synthesis document with integrated experience map
- **Next Step:** Use synthesis to create opportunities and generate solutions

### Recommended Folder Structure
```
initiatives/
├── live-sports-vod-conversion/
│   └── user-interviews/
│       ├── synthesis/
│       │   ├── synthesis-live-sports-vod-conversion-v1.md
│       │   ├── synthesis-live-sports-vod-conversion-v2.md
│       │   └── synthesis-live-sports-vod-conversion-v3.md
│       ├── snapshots/
│       │   └── [individual snapshot files]
│       └── opportunities/
│           └── opportunities-live-sports-vod-conversion-v1.md
├── newsletter-creation/
│   └── user-interviews/
│       ├── synthesis/
│       │   ├── synthesis-newsletter-creation-v1.md
│       │   └── synthesis-newsletter-creation-v2.md
│       └── snapshots/
│           └── [individual snapshot files]
└── user-onboarding/
    └── user-interviews/
        ├── synthesis/
        │   └── synthesis-user-onboarding-v1.md
        └── snapshots/
            └── [individual snapshot files]
```

### Efficiency Guidelines
- **1-2 New Snapshots**: Process immediately with incremental synthesis
- **3-5 New Snapshots**: Consider batch processing for efficiency
- **5+ New Snapshots**: Evaluate if full re-synthesis is needed
- **Topic Shift**: Always perform full synthesis when research focus changes

---

## Synthesis Template

### Standard Synthesis Template
=======
>>>>>>> Stashed changes
```markdown
# What We Learned: [Topic] Discovery Research

**Date Range:** [dates] | **Participants:** [N] | **Initiative:** [name] | **Version:** [vN]
**Synthesis Type:** [Initial/Incremental] | **Processed Snapshots:** [list]

## Executive Summary
[3-5 key findings with recommendations]

## Participant Overview
| Segment | Count | Key Characteristics |

## Top Opportunities
### 1. [Title]
**Frequency:** X/Y | **Evidence:** Strong/Moderate/Weak | **Impact:** High/Med/Low
**Opportunity:** "I want to... but... because..."
**Supporting Evidence:** [quotes] | **Business Impact:** [description]

## Integrated Experience Map
### Stage [X]: [Title]
- Common Actions / Shared Thoughts / Emotional Journey / Pain Points / Workarounds / Segment Variations / Evidence

## Key Insights
### 1. [Insight]
**What / Evidence / Implications**

## Research Gaps
- [Unanswered questions]

## Next Steps
- [ ] [Actions]
```

## Time Efficiency
- Incremental synthesis (1-2 new snapshots) should complete within 30 minutes
- Full synthesis (3-5 snapshots) should complete within 60 minutes
- Avoid re-processing previously analyzed snapshots; focus time on new data only
