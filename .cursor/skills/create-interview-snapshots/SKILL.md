---
name: create-interview-snapshots
description: >
  Extracts structured interview snapshots from qualitative interviews and user tests
  following the Continuous Discovery Habits methodology. Use when processing interview
  transcripts, creating user research snapshots, or extracting insights from user tests.
---

# Extract Interview Snapshots (Continuous Discovery Habits)

Turn a qualitative interview or user test into a structured snapshot that captures
concrete behavioral stories, opportunities, and insights.

## When to Use
- Extracting structured insights from interview transcripts or user tests
- Converting interview data into input for opportunity analysis
- Organizing multiple interviews to identify patterns

## Input
- **Primary:** Interview transcripts, observation notes, user test recordings (at least 1)
- **Context:** `company-level-context/` for product strategy / OKR
- **Optional:** Participant profiles, research goals, previous snapshots

## Output
- **Format:** Markdown — **Location:** `user-interviews/snapshots/`
- **Filename:** `snapshot-[participant-name]-[date].md`

## Process

### Step 1: Validate and frame
Assess the data's completeness; identify session type, research goals, and participant context.

### Step 2: Identify stories
Extract specific behavioral stories (concrete actions), not generalizations. Capture
contextual details (when/where/with whom/why), emotional moments, and workarounds.
Distinguish what people **say** from what they **do**.

### Step 3: Map the experience
For key stories, map the journey: actions, thoughts/feelings, pain points, tools.

### Step 4: Surface opportunities and insights
Identify pain points, needs, and improvement areas from the stories, then the patterns
that hold across stories.

### Step 5: Compile the snapshot
Write it up using the template below. Pick the depth that fits:
- **Full** — discovery interviews with rich data: all sections + detailed experience map.
- **Quick** — usability tests / follow-ups: Quick Facts, Stories, Opportunities only.
- **Synthesis-ready** — when prepping for cross-interview synthesis: emphasize patterns, quotes, opportunity statements.

## Output Template

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

## Quality bar
- Stories are concrete and behavioral, with specific details — not opinions or intentions.
- Opportunities are backed by direct quotes and are addressable through product changes.
- Insights go beyond a single story; quotes are accurate.

## Skill Integration
- **Before:** conduct and transcribe interviews to collect raw data.
- **After:** [Create Opportunities](/create-opportunities) to extract and prioritize; also feeds [Calculate ICE Score](/calculate-ice-score) as evidence.
- **Workflow:** Interview → Snapshots → Synthesize → Opportunities → Solutions
