---
name: writing-guide
description: >
  Writing style guide with voice and tone rules, banned words, LLM pattern avoidance,
  and formatting standards. Use when writing or reviewing any content to ensure clear,
  direct, human-sounding communication.
---

# Writing Style Guide

Keep PM artifacts and communications clear, direct, and human-sounding. Apply as a
quality layer over any document-generating skill.

## When to Use
- Writing or reviewing any document (PRDs, 1-pagers, OKRs, updates)
- Giving feedback on written content
- Creating customer-facing or stakeholder communications

## Input
- Text to review, or guidelines to apply
- Optional: target audience (team, leadership, customers)
- **Context:** `company-level-context/` for brand voice

## Output
- Edited text or section-by-section feedback (voice, banned words, LLM patterns, formatting)
- Saved in place with the source document; no separate file

## How to apply
Scan for banned words, LLM patterns, passive voice, and tone problems; apply the rules
below; offer concrete before/after rewrites for the highest-impact issues. Preserve the
author's intent and domain terms — edit, don't rewrite from scratch.

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

## Quality bar
- Zero banned words and LLM patterns remain; voice is active and direct.
- Claims are backed by specific data or examples.
- Edits improve clarity without distorting meaning or the author's intent.
- Tone matches the audience (formal for leadership/board, conversational for internal).

## Skill Integration
- **Before:** apply after any skill generates written output (PRDs, 1-pagers, OKRs).
- **After:** content is ready for review or publication.
- **Related:** works with all document-generating PM skills as a quality layer.
