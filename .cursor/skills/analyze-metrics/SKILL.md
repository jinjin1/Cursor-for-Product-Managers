---
name: analyze-metrics
description: >
  Turns raw product analytics (funnels, cohorts, event data, A/B results) into structured
  quantitative evidence. Use when grounding opportunities, assumptions, or ICE scores in
  numbers, sizing a problem, or reading whether a metric moved and why.
---

# Analyze Product Metrics

Turn raw analytics into structured **quantitative evidence** — the numeric counterpart to
interview research. This is the discovery toolkit's quantitative half: it sizes problems,
moves assumptions off weak evidence, and supplies the data ICE weights most heavily.

## When to Use
- Sizing an opportunity or reading whether a metric moved (and why)
- Producing strong evidence to validate an assumption or feed an ICE score
- Reviewing baseline vs target metrics for an initiative
- Investigating a funnel drop, retention change, or A/B result

## Input
- **Primary:** Raw analytics — funnel/conversion data, retention cohorts, event/usage data, A/B test results, dashboard exports
- **Required:** The question or metric in focus (e.g., "why does checkout drop at step 3?")
- **Context:** `company-level-context/` for the strategic metric tree / OKR targets

## Output
- **Format:** Markdown — **Location:** `product-analytics/` (the initiative's `product-analytics/` directory)
- **Filename:** `metrics-[topic]-v[version].md` (kebab-case, auto-increment; never overwrite)

## Process

### Step 1: Frame the question
State the specific metric or decision in focus and what answer would change a choice.

### Step 2: Gather and organize the data
List each data source with its date range and how the metric is defined. Note known data
quality limits (sampling, instrumentation gaps, attribution).

### Step 3: Find patterns and anomalies
Read trends, segment differences, funnel drop-offs, cohort decay, and outliers. Compare
against the baseline and the OKR target.

### Step 4: Quantify
Put numbers on it: effect size, segment splits, baseline → current → target. Prefer absolute
counts and rates over vague "up/down." Flag where the sample is too small to trust.

### Step 5: Tie to decisions
Connect findings to specific opportunities (sizing), assumptions (does this confirm or refute
one?), or an ICE score (which evidence type, see below).

### Step 6: Classify the evidence (for ICE)
Tag each finding by the strongest evidence type it supports:
**Market Data**, **User-based Evidence**, or **Test Results** (A/B / experiment). This is what
[calculate-ice-score](/calculate-ice-score) weights most heavily.

## Output Template

```markdown
# Metrics Analysis — [Topic]
**Topic / Version / Question in focus / Decision it informs**

## Data Sources
| Source | Metric definition | Date range | Quality caveats |

## Baseline & Target
- **Metric:** [name] — Baseline [X] → Current [Y] → OKR Target [Z]

## Findings
### 1. [Finding]
- **What the data shows:** [absolute numbers, rates, segment splits]
- **Confidence:** Strong / Moderate / Weak (sample size, sources)
- **Evidence type:** Market Data | User-based | Test Results

## Anomalies & Counter-Metrics
- [Outliers, regressions, metrics to watch that could break]

## Implications
- **Opportunities sized:** [...] | **Assumptions confirmed/refuted:** [...] | **ICE inputs:** [...]

## Open Questions
- [What the data can't yet answer]
```

## Quality bar
- Every number is sourced and dated; metric definitions are explicit.
- Findings are segmented, not just aggregate; small-sample findings are flagged, not over-claimed.
- Correlation is not reported as causation — only A/B / experiment results claim causal effect.
- Counter-metrics are named so a "win" that quietly breaks something else gets caught.
- Each finding ties to a decision (opportunity sizing, assumption, or ICE evidence), not data for its own sake.

## Skill Integration
- **Before:** [setup-initiative](/setup-initiative) for the folder; pair with [create-interview-snapshots](/create-interview-snapshots) (qualitative) for triangulation.
- **After:** feeds [calculate-ice-score](/calculate-ice-score) (Market Data / User-based / Test Results evidence), [identify-test-assumptions](/identify-test-assumptions) (moves assumptions off weak evidence), and [create-opportunities](/create-opportunities) (Opportunity Sizing lens).
- **Workflow:** Interviews + **Metrics** → Opportunities → Solutions → Assumptions (tested against metrics) → ICE
