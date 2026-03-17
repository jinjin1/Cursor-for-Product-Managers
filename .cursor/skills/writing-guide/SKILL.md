---
name: writing-guide
description: >
  Writing style guide with voice and tone rules, banned words, LLM pattern avoidance,
  and formatting standards. Use when writing or reviewing any content to ensure clear,
  direct, human-sounding communication.
---

# Writing Style Guide

## Goal
Ensure all PM artifacts and communications follow consistent voice, tone, and quality standards.

## When to Use
- Use when a PM or product manager writes or reviews any document (PRDs, 1-pagers, OKRs, updates)
- When providing feedback on written content from team members
- When creating customer-facing or stakeholder communications
- Applied as a quality layer across all document-generating PM skills in this toolkit

## Input
- **Required:** Text content to review or guidelines to apply
- **Optional:** Target audience (internal team, leadership, customers)
- **Context:** Reference `company-level-context/` for company-level brand voice and strategy alignment

## Output
- **Format:** Edited text or review feedback in Markdown (`.md`)
- **Location:** Same as the source document (no separate file created)
- **Template structure:** Feedback organized by section: voice issues, banned words, LLM patterns, formatting

## Process

1. Validate inputs and gather context
2. Execute core analysis
3. Generate output and review results
4. Iterate based on feedback


### Step 1: Scan for issues
Read the content and identify banned words, LLM patterns, passive voice, and tone problems.

### Step 2: Apply voice rules
Check active voice, specificity, and directness against the rules in the voice and tone section below.

### Step 3: Check formatting
Validate punctuation, structure, readability, and consistency with the formatting standards.

### Step 4: Suggest improvements
Provide concrete before/after options for each issue found. Prioritize high-impact changes.

### Step 5: Review and validate
Evaluate whether suggested changes improve clarity without losing meaning. Iterate on edge cases.

## Success Criteria
- Zero banned words remaining in final output (metric: banned word count = 0/total)
- Active voice usage in 90% or more of sentences
- All claims backed by specific data or examples
- Readability score appropriate for target audience

## Decision Support
When tone conflicts arise, recommend options:
- **Option A:** Formal tone (for leadership, board communications)
- **Option B:** Conversational tone (for team updates, internal docs)
- **Recommend:** Match the document type and audience context

## Context Preservation
- Reference `company-level-context/` for brand voice guidelines and strategic messaging
- Maintain consistency with existing document tone when editing (not rewriting from scratch)
- Preserve the author's intent and domain-specific terminology

## Self-Evaluation
- Review whether edits improve clarity without distorting meaning
- Evaluate consistency: Are rules applied uniformly across the document?
- Validate that LLM pattern removal produces natural-sounding text
- Improve by collecting feedback on which edits were accepted vs. rejected

## Skill Integration
- **Before this skill:** Apply after any other skill generates written output (PRDs, 1-pagers, OKRs)
- **After this skill:** Content is ready for review or publication workflow
- **Related:** Works with all document-generating PM skills as a quality layer

## Time Efficiency
- Quick scan for banned words should complete within 2 minutes
- Full voice and tone review should complete within 10 minutes per document
- Focus on highest-impact issues first when time is limited

---

## Voice and Tone Rules

- Write like humans speak. Avoid corporate jargon and marketing fluff.
- Be confident and direct. Avoid softening phrases like "I think," "maybe," or "could."
- Use active voice instead of passive voice.
- Use positive phrasing; say what something *is*, rather than what it *isn't*.
- Say "you" more than "we" when addressing external audiences.
- Use contractions like "I'll," "won't," and "can't" for a warmer tone.

## Specificity and Evidence

- Be specific with facts and data instead of vague superlatives.
- Back up claims with concrete examples or metrics.
- Highlight customers and community members over company achievements.
- Use realistic, product-based examples instead of `foo/bar/baz` in code.
- Make content concrete, visual, and falsifiable.

## Title Creation

- Make a promise in the title so readers know what they get.
- Share something uniquely helpful that makes readers better at their work.
- Avoid vague titles like "My Thoughts On XYZ." Titles should be opinions or shareable facts.
- Write placeholder titles first, finalize after content is complete.

## Banned Words
`a bit/a little/actually/agile/arguably` > remove |
`assistance` > "help" | `attempt` > "try" | `battle tested` > remove |
`best practices` > "proven approaches" | `blazing fast` > "build XX% faster" |
`business logic/cognitive load` > remove | `commence` > "start" | `delve` > "go into" |
`disrupt/disruptive` > remove | `facilitate` > "help" | `game-changing` > specific benefit |
`great` > remove or be specific | `implement` > "do" | `individual` > "person" |
`initial` > "first" | `innovative` > remove | `just` > remove | `leverage` > "use" |
`mission-critical` > "important" | `modern/modernized` > remove | `numerous` > "many" |
`out of the box` > remove | `performant` > "fast and reliable" |
`pretty/quite/rather/really/very` > remove | `referred to as` > "called" |
`remainder` > "rest" | `robust` > "strong" | `seamless` > "automatic" |
`sufficient` > "enough" | `utilize` > "use" | `webinar` > "online event"

## Banned Phrases
`I think/I believe/we believe` > state directly | `it seems/sort of/kind of/pretty much` > remove |
`a lot/a little` > be specific | `By developers, for developers` > remove |
`We can't wait to see what you'll build` > remove | `We obsess over` > remove |
`The future of` > remove | `We're excited` > "We look forward" | `Today, we're excited to` > remove

## LLM Pattern Avoidance
- Replace em dashes with semicolons, commas, or sentence breaks.
- Do not start with "Great question!", "You're right!", or "Let me help you."
- Skip "Let's dive into...", "In today's fast-paced world", "In the ever-evolving landscape."
- Avoid "It's not just [x], it's [y]" and self-referential AI disclaimers.
- Avoid essay closers: "In conclusion," "Overall," "To summarize."
- Avoid overusing "Furthermore," "Additionally," "Moreover."
- Remove hedge stacking: "may potentially," "it's important to note that."
- Avoid perfectly symmetrical lists starting "Firstly... Secondly..."
- Use sentence-case headings, not title-case.
- Remove Unicode artifacts: smart quotes, non-breaking spaces.

## Punctuation and Formatting
- Use Oxford commas consistently.
- Use exclamation points sparingly.
- Sentences can start with "But" and "And" (do not overuse).
- Use periods instead of commas when possible for clarity.
