---
name: identify-test-assumptions
description: >
  Identifies and tests assumptions from opportunities and solutions across desirability,
  usability, feasibility, viability, and ethical dimensions. Use when preparing to validate
  ideas, surfacing leap-of-faith assumptions, or designing lightweight tests.
---

# Identify and Test Assumptions

## When to Use
- Use when a PM needs to validate ideas before investing in development
- After creating opportunities with [Create Opportunities](/create-opportunities) or after synthesizing interviews with [Synthesize Snapshots](/synthesize-snapshots)
- Before or after [Generate Solutions](/generate-solutions) in the workflow
- When any new initiative requires systematic risk assessment

## Input
- **Required:** Prioritized opportunities from `opportunities/`, solution sketches from `solutions/`, interview snapshots/synthesis
- **Context:** Reference `company-level-context/` for company-level OKR and strategy alignment
- **Minimum:** 1 target opportunity with evidence + 2-3 candidate solutions (or 1 solution with key user journeys)

## Output
<<<<<<< Updated upstream
**Format:** Markdown (`.md`)
**Location:** `assumptions/[topic]/`
**Filename:** `assumptions-[opportunity-name]-v[version].md`

**Semantic Naming Guidelines:**
- opportunity-name: kebab-case opportunity name from opportunity document (e.g., newsletter-creation, user-onboarding)
- version: auto-incrementing version number (v1, v2, v3...)
- Example: assumptions-newsletter-creation-v1.md

**Version Management:**
- Check existing files with same opportunity-name pattern before creating new assumptions
- Auto-increment version number (v1 → v2 → v3...)
- Never overwrite existing assumption files
- Preserve all assumption versions for comparison
- No date dependency required

**Source Reference (MANDATORY):**
- Include source reference at the top of every output document
- Format: `**Based on:** [source filename(s)]`
- Example: `**Based on:** opportunities-user-onboarding-v2.md, solutions-user-onboarding-v1.md`
- When source is updated, create a new version with updated source reference

---

## AI Instructions for Assumption Identification

### When Receiving Research and Opportunity Data
- **Validate Inputs:** Confirm target opportunity, evidence strength, and affected segments.
- **Clarify Scope:** Define which ideas/journeys will be story-mapped.
- **Note Constraints:** Technical, legal, GTM, success metrics, time/resource limits.
- **Topic Extraction:** Analyze opportunity content to extract main topic for semantic filename.
- **File Existence Check:** MANDATORY - Check for existing files with pattern `assumptions-[topic]-v*.md` before creating new file.
- **Version Management:** MANDATORY - Auto-increment version number based on existing files. Never overwrite existing files.

### Assumption Generation Guidelines
- **Use Five Categories:** Desirability, Usability, Feasibility, Viability, Ethical.
- **Phrase Positively and Specifically:** State what must be true, in concrete, testable language.
- **Tie to Behavior:** Prefer assumptions about what users will do over what they say.
- **Attach Evidence:** Link each assumption to quotes, behaviors, or data when available.
- **Normalize Granularity:** Split vague, compound assumptions into specific, testable statements.

### Evidence Classification (Binary)
- **Strong Evidence:** 
  - Direct user quotes or behaviors supporting assumption
  - Quantitative data from multiple sources
  - Previous successful tests of similar assumptions
- **Weak Evidence:** 
  - No direct evidence
  - Single source or anecdotal evidence
  - Theoretical or assumed knowledge only

### Importance Evaluation (Binary)
- **More Important:** 
  - Core value proposition depends on this assumption
  - Assumption failure would kill the solution
  - Blocking other critical assumptions
- **Less Important:** 
  - Nice-to-have features or optimizations
  - Minor impact on solution success
  - Non-blocking assumptions

### Prioritization Guidelines (Assumption Mapping)
- Place each assumption on a 2D grid:
  - X-axis: Evidence known (left = strong evidence, right = weak evidence)
  - Y-axis: Importance to idea success (bottom = less important, top = more important)
- **Leap of Faith (LoFA):** Select ONLY assumptions in the top-right quadrant:
  - **Weak Evidence** (right side of X-axis)
  - **More Important** (top half of Y-axis)
  - **Maximum 3 LoFA** per assumption document
  - **If more than 3 in quadrant**: Place remaining items in a "Watch List" section; test these after current LoFA tests are complete
  - **Visual indicator**: Mark with circle or highlight

### Testing Guidelines
- **Simulate an Experience, Evaluate Behavior:** Design minimal simulations that let users behave in line with or against the assumption.
- **Define Success Upfront:** Use numbers (e.g., "≥ 3 of 10 participants choose X"), not percentages.
- **Recruit the Right Audience:** Screen by target opportunity and segment; select for variation.
- **Start Small, Then Scale:** Begin with quick signals; escalate to larger tests only if warranted.
- **Triangulate:** Combine small, different methods to reduce false positives/negatives.

### Semantic File Naming Guidelines
- **Topic Extraction:** Analyze opportunity content to identify main topic/theme
- **Filename Format:** Use semantic naming pattern `assumptions-[opportunity-name]-v[version].md`
- **Version Management:** Auto-increment version number based on existing files
- **Folder Organization:** Create topic-specific subfolders for better organization
- **No Date Dependency:** Remove all date-based filename requirements

**Topic Extraction Rules:**
1. When running inside an initiative folder: use the initiative folder name as the topic
2. When running independently: explicitly ask the user for the topic name
3. Do NOT auto-extract topics from content analysis; topics must always be deterministic
4. Format: kebab-case (e.g., "user-onboarding", "checkout-optimization")
5. Use topic as primary identifier instead of date

**Version Management Process:**
1. **MANDATORY STEP 1:** Check existing files with pattern `assumptions-[opportunity-name]-v*.md`
2. **MANDATORY STEP 2:** Find the highest version number for the same opportunity
3. **MANDATORY STEP 3:** Auto-increment version number (v1 → v2 → v3...)
4. **MANDATORY STEP 4:** Generate new filename with incremented version
5. **MANDATORY STEP 5:** Verify no file with new filename exists before creation
6. **CRITICAL:** Never overwrite existing files - always create new version
7. No manual version tracking required

**Smart Topic Detection:**
- **Content Analysis:** Extract main themes from opportunity document
- **Keyword Frequency:** Use most frequent relevant keywords as topic
- **Kebab-Case Format:** Convert spaces to hyphens, lowercase (e.g., "User Onboarding" → "user-onboarding")
- **Uniqueness Check:** Ensure topic doesn't conflict with existing files
- **Fallback:** Use generic topic name if extraction fails

---
=======
- **Format:** Markdown, saved to `assumptions/[topic]/`
- **Filename:** `assumptions-[opportunity-name]-v[version].md` (kebab-case, auto-increment version)
- **Template structure:** Each file has required sections: Story Map, Assumption Log, Assumption Map, Test Cards, Results
- **Version management:** Check existing files before creation; never overwrite previous versions
>>>>>>> Stashed changes

## Process

### Step 1: File management (mandatory pre-step)
1. Extract topic from opportunity document content
2. Check existing `assumptions-[topic]-v*.md` files; find highest version
3. Generate new filename with incremented version; verify no conflict

### Step 2: Prepare context
1. Confirm target opportunity and desired outcomes
2. Identify key actors (end-users, systems, third parties)

### Step 3: Story-map candidate ideas
1. Assume the solution exists; map what users do to get value
2. Sequence steps by actor; highlight critical moments

### Step 4: Generate assumptions (five categories)
For each pivotal step, enumerate assumptions across: Desirability, Usability, Feasibility, Viability, Ethical.
- Phrase positively and specifically (what must be true)
- Tie to behavior, not opinions; attach evidence where available

### Step 5: Pre-mortem
"Six months later, launch failed. What went wrong?" Convert reasons into testable assumptions.

### Step 6: Walk OST lines (Outcome-Opportunity-Solution)
Write why the solution addresses the opportunity. Extract each inference as a testable assumption.

### Step 7: Normalize and deduplicate
Rewrite assumptions to be positive, specific, single-concept. Link supporting quotes/data.

### Step 8: Map and prioritize (Assumption Mapping)
1. Plot on 2D grid: X=Evidence (strong left, weak right), Y=Importance (high top, low bottom)
2. Select max 3 Leap-of-Faith Assumptions (LoFA) from top-right quadrant (weak evidence + high importance)
3. If more than 3 in quadrant, prioritize by impact, test complexity, dependencies

### Step 9: Design test cards for LoFA
For each LoFA, define: simulation, method, audience, sample size, time window, and success criteria (absolute numbers, e.g., "3/10 do X").

### Step 10: Run tests, record results, update map
Move assumptions leftward as evidence grows. Iterate or proceed based on findings.

## Success Criteria
- At least 3 LoFA identified with clear test designs (success metric: 3/3 test cards complete)
- Each test card has absolute-number success criteria (not percentages)
- All five assumption categories covered
- Evidence citations linked to each assumption where available

## Decision Support
Based on test results, recommend one of these options:
- **Option A: Proceed** — Recommend when 70% or more of LoFA pass their tests
- **Option B: Iterate** — Suggest when some LoFA pass but others need refinement
- **Option C: Pivot** — Suggest when critical assumptions fail; explore alternative opportunities

## Context Preservation
- Always reference `company-level-context/` for strategic alignment and OKR context
- Review previous assumption versions to track how understanding evolved over time
- Ensure assumptions connect to existing company-level strategy and product vision

## Self-Evaluation
- Review and validate assumption quality: Are they specific, behavioral, and testable?
- Evaluate test design: Is the simulation minimal? Is the audience correct?
- After results, improve the process: What false positives/negatives occurred? How to iterate?
- Use feedback from test outcomes to refine future assumption identification

## Skill Integration
- **Before this skill:** Run after [Create Opportunities](/create-opportunities) or [Generate Solutions](/generate-solutions)
- **After this skill:** Feed results into [Generate Solutions](/generate-solutions) for solution refinement
- **Workflow:** Opportunities > Solutions > Assumptions > Test > Iterate

## Output Template Structure

```markdown
# Assumptions — [Opportunity Name]
**Topic:** [topic] | **Version:** [vN] | **Target Opportunity:** [statement]

## Story Map Snapshot
- **Actors:** [types] | **Key Steps:** 1. [Actor] — [Step] ...

## Assumption Log
| ID | Category | Assumption | Evidence | Importance | Evidence Known | LoFA |
|----|----------|------------|----------|------------|----------------|------|

## Assumption Map Summary
- **LoFA (max 3):** [IDs] | **Notable clusters:** [notes]

## Test Cards (per LoFA)
- **Assumption / Simulation / Method / Audience / Sample & Window / Success Criteria / Next if Pass-Fail**

## Results and Decisions
- Outcomes / Map updates / Decisions

## Next Steps
- [ ] Run next test | [ ] Evolve idea | [ ] Share with stakeholders
```

<<<<<<< Updated upstream
---

## Templates

### Assumption Statement Pattern
- Actor + Action + Context + Outcome expected  
Example: "Prospective subscribers will select a live game from our home screen when browsing evening entertainment options."

### Pre-Mortem Prompt
- "It's six months after launch and this failed. What happened?"  
Capture each reason → rewrite as a positive, specific assumption that must be true.

### Story Map (Quick)
```
Actors: [User, Platform, Partner]
1) [User] does …
2) [Platform] shows …
3) [Partner] provides …
```

### Assumption Mapping Template
```
                    Evidence Known
                Strong              Weak
More     [A-01]  [A-03]    [A-02]  [A-04] ← LoFA (max 3)
Important [A-09]  [A-10]    [A-05]  [A-06] ← LoFA (max 3)

Less     [A-15]  [A-14]    [A-18]  [A-17]
Important [A-12]  [A-11]    [A-13]  [A-16]
```

### LoFA Selection Process
1. **Plot all assumptions** on 2D grid using binary classification
2. **Identify top-right quadrant** (Weak Evidence + More Important)
3. **Select maximum 3 assumptions** from this quadrant
4. **If more than 3 in quadrant**: Prioritize by:
   - Impact on solution success
   - Test complexity (easier first)
   - Dependencies (blocking first)
5. **Mark selected LoFA** with visual indicator (circle or highlight)

### Success Criteria Pattern
- Define n participants and success threshold as an absolute number (not %).  
Example: "≥ 4 of 10 choose sports content on the prototype home screen."

---

## Quality Indicators

### Strong
- **Specific & Positive:** Testable statements tied to concrete behavior
- **Evidence-Linked:** Quotes, analytics, or prior tests attached
- **Right LoFA:** Maximum 3 from top-right quadrant (Weak Evidence + More Important)
- **Binary Classification:** Consistent Strong/Weak, More/Less Important evaluation
- **Clear Criteria:** Absolute numbers, audience defined, timeboxed
- **Iterative Cadence:** Start small; scale only with positive signals

### Weak
- **Too Many LoFA:** More than 3 assumptions selected
- **Inconsistent Classification:** Mixed evaluation criteria
- **Vague:** Generic or compound statements
- **Opinion-Based:** Future-intent questions; no behavior
- **Ambiguous Criteria:** Percentages, no audience, no time window
- **Over-Building:** Large experiments before early signals

---

## Common Anti-Patterns and Guardrails
- **Too many LoFA** → Select maximum 3 from top-right quadrant only
- **Inconsistent classification** → Use binary classification (Strong/Weak, More/Less Important)
- **Not generating enough assumptions** → Use story map + pre-mortem + OST lines
- **Negative phrasing** → Rewrite as what must be true (positive)
- **Not specific enough** → Add actor, context, behavior, and outcome
- **Favoring one category** → Cover all five: Desirability/Usability/Feasibility/Viability/Ethical
- **Overly complex simulations** → Design smallest viable simulation first
- **Using percentages for criteria** → Use absolute counts (e.g., 3 of 10)
- **Missing evaluation details** → Define audience, n, window, and behavior
- **Testing with wrong audience** → Screen for the target opportunity
- **Designing for less than best-case** → Start where passing is most likely; increase difficulty later

---

## Error Handling
- **Insufficient Data:** Request more snapshots/synthesis; reduce scope.
- **Weak Evidence:** Mark evidence as "Weak" and prioritize accordingly.
- **Conflicting Results:** Triangulate with another small method before decisions.
- **Ethical Concerns:** Document potential harms; design mitigation and/or halt.

### File Naming Issues
- **Topic Extraction Failure:** Ensure clear topic identification from opportunity content
- **Version Conflicts:** Always check existing files before creating new assumptions
- **Incorrect Format:** Use kebab-case for opportunity-name, v[number] for version
- **Missing Topic:** Extract main theme from opportunity document for filename
- **Overwriting Prevention:** Never overwrite existing assumption files, always increment version
- **File Existence Check Failure:** MANDATORY - Always verify file existence before creation
- **Version Detection Error:** If version detection fails, start with v1 and add warning note

---

## Process Flow
```
Individual Interviews → Create Snapshots → Synthesize Patterns → Create Opportunities → Generate Solutions → Identify & Test Assumptions
     ↓                    ↓                    ↓                    ↓                       ↓                        ↓
[Raw Data]        [Structured Stories]   [Shared Patterns]    [Problem Statements]    [Product Ideas]      [Risks & Tests]
```

### Recommended Folder Structure
```
assumptions/
├── newsletter-creation/
│   ├── assumptions-newsletter-creation-v1.md
│   └── assumptions-newsletter-creation-v2.md
├── user-onboarding/
│   ├── assumptions-user-onboarding-v1.md
│   └── assumptions-user-onboarding-v2.md
└── payment-flow/
    └── assumptions-payment-flow-v1.md
```

---

## Quality Assurance Checklist

### Input Validation
- [ ] Clear target opportunity statement with supporting evidence
- [ ] Opportunity context and problem definition complete
- [ ] Solution ideas or user journeys defined
- [ ] Evidence strength assessed and documented

### Assumption Quality
- [ ] Assumptions cover all five categories (Desirability, Usability, Feasibility, Viability, Ethical)
- [ ] Assumptions are positive, specific, and testable
- [ ] Evidence linked to each assumption where available
- [ ] Assumption mapping completed with LoFA identified

### Testing Quality
- [ ] Test cards designed for LoFA assumptions
- [ ] Success criteria defined with absolute numbers
- [ ] Audience screening criteria specified
- [ ] Sample size and time window defined

### Process Completion
- [ ] All assumptions evaluated and mapped
- [ ] Test results documented and analyzed
- [ ] Decisions made based on evidence
- [ ] Next steps are clear and actionable

### File Naming Validation
- [ ] **MANDATORY**: Extracted clear topic from opportunity content before creating filename
- [ ] **MANDATORY**: Checked existing files with pattern `assumptions-[topic]-v*.md` before creation
- [ ] **MANDATORY**: Verified no file with new filename exists before creation
- [ ] Filename uses semantic naming format: assumptions-[opportunity-name]-v[version].md
- [ ] Version number is correctly auto-incremented for same-opportunity assumptions
- [ ] Opportunity name is descriptive and kebab-case formatted
- [ ] **CRITICAL**: No overwriting of existing assumption files - always create new version
- [ ] Topic extraction completed through content analysis before assumption creation
- [ ] Version management process followed step-by-step

---

## AI Implementation Checklist

### Before Creating Any Assumption File:
1. **Topic Extraction** ✅
   - [ ] Analyze opportunity document for main theme
   - [ ] Extract kebab-case topic name (e.g., "newsletter-creation")
   - [ ] Verify topic is descriptive and unique

2. **File Existence Check** ✅
   - [ ] Search for existing files: `assumptions-[topic]-v*.md`
   - [ ] List all found files with their version numbers
   - [ ] Identify highest version number

3. **Version Management** ✅
   - [ ] Calculate next version number (highest + 1)
   - [ ] Generate new filename: `assumptions-[topic]-v[version].md`
   - [ ] Verify new filename doesn't already exist

4. **File Creation** ✅
   - [ ] Create file with new filename only
   - [ ] Never overwrite existing files
   - [ ] Add version number to document header

### Error Handling:
- **If topic extraction fails**: Use generic topic name and add warning
- **If version detection fails**: Start with v1 and add warning note
- **If file already exists**: Increment version and try again
- **If multiple topics found**: Use most relevant one and document choice

---

## Related Frameworks
- [Create Interview Snapshots](/create-interview-snapshots)
- [Synthesize Interview Snapshots](/synthesize-snapshots)
- [Create Opportunities](/create-opportunities)
- [Generate Solutions](/generate-solutions)
=======
## Time Efficiency
- Complete assumption identification within 60 minutes per opportunity
- Test card design should take no more than 30 minutes per LoFA
- Start with the smallest viable simulation; scale only with positive signals
>>>>>>> Stashed changes
