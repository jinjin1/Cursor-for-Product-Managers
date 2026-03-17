---
name: create-interview-snapshots
description: >
  Extracts structured interview snapshots from qualitative interviews and user tests
  following the Continuous Discovery Habits methodology. Use when processing interview
  transcripts, creating user research snapshots, or extracting insights from user tests.
---

# Extract Interview Snapshots (Continuous Discovery Habits)

## Goal
Systematically extract meaningful insights from qualitative interviews or user test sessions, creating structured interview snapshots that capture stories, opportunities, and behavioral insights.

## When to Use
- Use when a PM or product manager needs structured insights from qualitative interviews or user tests
- When processing interview transcripts following Continuous Discovery Habits methodology
- When converting interview data into input for opportunity analysis in an initiative
- When systematically organizing multiple interviews to identify patterns

## Input
- **Primary source**: Interview transcripts, observation notes, user test recordings
- **Context source**: company-level-context/ (product strategy, OKR, strategic documents for context)
- **Required**: At least 1 interview transcript or user test recording
- **Optional**: Participant profiles, research goals, previous snapshots

## Output
- **Format:** Markdown (`.md`)
- **Location:** `user-interviews/snapshots/`
- **Filename:** `snapshot-[participant-name]-[date].md`

## Process

1. Validate inputs and gather context
2. Execute core analysis
3. Generate output and review results
4. Iterate based on feedback


### Step 1: Data Validation
Assess completeness and quality of provided interview data. Complete within 5 minutes.

### Step 2: Context Extraction
Identify session type, research goals, and participant context.

### Step 3: Story Identification
Extract specific behavioral stories, not generalizations. Focus on concrete actions.

### Step 4: Experience Mapping
Create user journey maps for key stories with actions, emotions, and pain points.

### Step 5: Opportunity Analysis
Identify pain points, needs, and improvement areas from stories.

### Step 6: Insight Synthesis
Recognize patterns and behavioral insights across stories.

### Step 7: Snapshot Creation
Compile into the structured template format below.

### Step 8: Quality Review
Validate completeness and clarity against success criteria. Improve weak areas.

## Success Criteria
- Completeness: 100% of required sections filled (Quick Facts, Stories, Experience Map, Opportunities, Insights)
- Specificity: Each story contains at least 3 concrete behavioral details
- Quote coverage: 70% or more of opportunities backed by direct quotes
- Actionability: 80% or more of opportunities are addressable through product changes

## Data Processing Guidelines
- Focus on concrete behaviors over opinions or intentions
- Extract contextual details (when, where, with whom, why)
- Identify emotional moments (frustration, delight, surprise, confusion)
- Capture workarounds and problem-solving approaches
- Distinguish between what people say vs. what they do
- Note repeated patterns indicating systematic issues

## Output Template Structure

Required sections and fields:

```markdown
# Interview Snapshot: [Participant Name]
**Date:** [YYYY-MM-DD]
**Type:** [Discovery Interview | Usability Test | Contextual Inquiry]
**Duration:** [Minutes]
**Interviewer(s):** [Name(s)]

## Quick Facts
- **Segment / Key Behaviors / Tools Used / Experience Level / Setting**

## Memorable Quote
> "[Direct quote capturing participant's voice]"

## Story Summary
### Story 1: [Title]
**Context:** [Time, place, situation, trigger]
**What Happened:** [Concrete actions, step by step]
**Outcome:** [Result or consequence]
**Key Moments:** [Behavioral insight, emotional response, workaround]

## Experience Map
**Scope / Goal / Journey Stages** (Actions, Thoughts/Feelings, Pain Points, Tools)

## Opportunities
- **[Title]**: [Customer needs, pain points, desires — chances to improve their experience]

## Insights
- **[Category]**: [Pattern or behavior beyond a single story]
```

## Decision Support

- **Option A — Full Snapshot**: Recommend for discovery interviews with rich behavioral data. All sections with detailed experience maps.
- **Option B — Quick Snapshot**: Suggest for usability tests or follow-up sessions. Quick Facts, Stories, and Opportunities only.
- **Option C — Synthesis-Ready Snapshot**: Recommend when preparing for cross-interview synthesis. Emphasize patterns, quotes, and opportunity statements.

Selection depends on interview type, data richness, and next-step purpose.

## Quality Review
Before finalizing, evaluate and validate:
- All required sections complete with concrete behavioral details
- Experience map follows logical flow; opportunities are specific and actionable
- Insights go beyond individual stories; quotes are accurate
- Iterate to improve specificity where needed

## Workflow Integration

**Before** this skill: Conduct interviews and transcription to collect raw data.
**After** this skill: [Create Opportunities](/create-opportunities) to extract and prioritize opportunities from snapshots. Also feeds into [Calculate ICE Score](/calculate-ice-score) as evidence.

```
Interview → Create Snapshots → Synthesize → Create Opportunities → Solutions
```
