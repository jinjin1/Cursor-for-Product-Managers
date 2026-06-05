---
name: product-strategy-review
description: >
  Conducts PRISM-based product strategy self-review with evidence gates and scoring.
  Use when reviewing product strategy documents, validating strategic options, or
  conducting CPO-level strategy assessments with structured frameworks.
---

# CPO Self-Review Partner — PRISM Strategy

CPO-level, evidence-based self-review of a product strategy document.

## When to Use
- Reviewing and validating a product strategy document
- Quarterly strategy reviews or comparing strategic options for an initiative
- Preparing a strategy for leadership or board review

## Input
- `doc_link`: strategy document to review
- `evidence_hub_link`: evidence folder (e.g., `initiatives/<name>/`)
- `product_or_area`, `owner`, `review_window_start/end` (YYYY-MM-DD)
- `riskiest_assumptions`: at least 2 tagged assumptions
- Optional: `baseline_metric`, `north_star`, `capacity_window`, `runway_months`
- **Context:** `company-level-context/` for strategy/OKR/vision alignment; reference prior review versions.

If required inputs are missing, return **HOLD** with a 1-Day Evidence Sprint proposal.

Citation format: `[[ev-id|path#line-range|YYYY-MM-DD]]` (missing citations deduct one step).

## Output
- **Format:** `review.json` (machine-readable) + `review.md` (≤ 900 words)
- **Location:** same directory as the strategy document
- **Required sections:** Executive Summary, Impact × Confidence table, PRISM Scores, Pre-mortem/Kill-Switch, Next Review Date

## Process

### Step 1: Evidence readiness gate
Core items (need 4+ to proceed): (1) last-180-day signals — 3+ founder/customer notes,
tickets, competitor moves; (2) 2+ riskiest assumptions tagged; (3) success criterion (OMTM
or qualitative heuristic); (4) 1-2 week discovery plan or OKR draft; (5) versioned evidence
hub link. **HOLD** if ≤3 core. **PROCEED** if ≥4 (must include #2 and #3). **AUTO-ESCALATE**
if PROCEED + 2+ advanced items.

### Step 2: PRISM scoring (0-5 per dimension)
1. **P — Problem Diagnosis** — causal analysis, recent behavioral data, JTBD, broken assumptions
2. **R — Reframe Opportunity** — opportunity with timing rationale, competitive whitespace, user/business shift
3. **I — Intentional Bets** — bold testable choices with explicit trade-offs, non-goals, success/failure thresholds
4. **S — Systemized Execution** — OKRs reflecting bets, discovery loops, leading indicators, operating rhythm
5. **M — Momentum & Meta-Reflection** — quarterly retros, stopped work, updated assumptions, learning culture

Scale: 0 = no evidence, 1 = memo, 2 = fragmentary, 3 = solid/recent, 4 = strong (metrics-connected), 5 = exemplary (reproducible). Overall = equal-weighted average.

### Step 3: Mode analysis
- **Mode 0 — Principle alignment:** mission/vision coherence, 1-3yr narrative, value thesis
- **Mode 1 — Socratic checklist:** thesis, outcomes, opportunity, causality, alternatives (3+), trade-offs, unit economics, disconfirming evidence
- **Mode 2 — Bias guardrails:** address all 6 — Confirmation, Availability, Sunk Cost, Survivorship, Overconfidence, Anchoring
- **Mode 3 — Options & capital allocation:** assumptions, investment, impact, risks, decision rules per option
- **Mode 4 — Scenarios & runway:** Base/Upside/Downside sensitivity, quarterly sequencing
- **Mode 5 — Pre-mortem & kill-switch:** top-5 failure causes, leading indicators, kill criteria, pivot/market triggers, adaptation plan
- **Mode 6 — Stakeholder lens:** Investor/Board, Engineering, GTM, Customer Support

### Step 4: Outputs and recommendations
Produce `review.json` first, then `review.md`. Include the decision, improvements with
owners and due dates, and the next review date.

## Quality bar
- All 5 PRISM dimensions scored with valid, current evidence citations (not hallucinated); anchors applied consistently.
- Evidence gate produces a clear PROCEED/HOLD; at least 3 strategic options compared (warn if fewer).
- Decision follows the scores: Approve (overall ≥ 3.5), Conditional (dimensions need strengthening), or Revise (critical gaps or < 2.5).
- Improvements are prioritized by impact with owners and dates.
- Watch the anti-patterns: strategy as a feature list, lagging-only metrics, untested assumptions as fact, over-broad scope, no stopped work.

## Skill Integration
- **Before:** gather evidence from initiatives; use [OKR Sparring Partner](/okr-sparring-partner) for OKR validation.
- **After:** feed improvements into strategy revision and the next planning cycle.
- **Related:** [OKR Sparring Partner](/okr-sparring-partner) for OKR-specific review.
