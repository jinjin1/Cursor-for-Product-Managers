---
name: build-prototype
description: >
  Builds a working, clickable prototype plus a companion doc (a 10-question FAQ) in place of a
  heavyweight PRD, so engineers ask "how do we make this better?" instead of "what do you want?".
  Use to validate a solution's interaction and flow, de-risk a desirability or usability assumption,
  or hand engineering a near-complete (80%) starting point.
---

# Build a Working Prototype + Companion Doc

Show a working prototype instead of writing a PRD first. A prototype with a companion doc reaches
the same understanding faster and produces a better conversation — engineers start asking "how do
we make this better?" instead of "what do you want?". The non-negotiable bar: **80% of the way there
with zero engineering time**, and it must not crash on the first click.

## When to Use
- Validating a solution's interaction or flow, where a static mock is not enough
- Giving an [identify-test-assumptions](/identify-test-assumptions) desirability/usability LoFA a concrete test *method*
- Turning the engineering conversation from "what do you want?" into "how do we make this better?"
- Branch vs [generate-figma-prompt](/generate-figma-prompt): clickable flow → prototype; static visual exploration → Figma

## Input — specify the outcome before the prompt
A vague prompt yields a vague prototype. Before writing a single character of the build prompt,
write down three things and paste them as the first message:
- **Input** — what data source or user input is needed
- **Output** — concretely, what the finished artifact shows
- **Audience** — who looks at it and what decision they are trying to make

Then gather:
- **Primary source:** the selected solution (`solutions/`), design brief (`design/`), and the assumption under test (`assumptions/`)
- **Design system:** repo `design-system/` tokens — map to the brand aesthetic if present; proceed with neutral defaults if not
- **Minimum:** one solution or flow + the Input/Output/Audience triad

## Output
- **Location:** `prototype/` (the initiative's `prototype/` directory)
- **Files:**
  - the prototype artifact — a runnable HTML app (single page or a few screens), or a `.canvas.tsx` board for data/decision views
  - `companion-doc-[feature-name].md` — the 10-question FAQ that lives next to the prototype
  - `README.md` — how to run the local preview

## Process
1. **Specify the outcome (gate).** Lock the Input/Output/Audience triad first. No build prompt before the triad is written — a vague prompt yields a vague prototype.
2. **Pull context.** Read the selected solution, design brief, and assumption(s); load `design-system/` tokens if they exist.
3. **Scope to a thin slice.** Pick the one core flow that *must* work in V1. Keep screens minimal (ideally one, a few at most). Everything else becomes a non-goal in the companion doc.
4. **Build it.** A self-contained static app with few dependencies (prefer a single HTML file or a light component). Fill with realistic mock data.
5. **Preview — match the surface to the artifact.** A *data/decision board* (metrics, cohorts, charts, tables) renders best as a **Cursor Canvas** (a `.canvas.tsx` beside the chat) — package its layout, data sources, and formatting so it regenerates consistently. A *working UI prototype* (a clickable flow) stays a runnable HTML app; surface the **`localhost` URL to open in a browser**. Don't assume an inline browser pane appears — Cursor's native Browser tool needs a paid plan, a capable model, and approval, so treat inline preview as a bonus, not the path. Adjust to a brand aesthetic if asked.
6. **Test before showing.** Click the core flow end to end. **The biggest failure mode is showing an engineer a prototype that crashes on the first click** — if it does, it is not ready to hand off. Verify by actually loading it: open the `localhost` URL in a browser (or run a headless click-through) and read the console for errors. **Do not report the flow as tested unless a tool actually ran** — narrating "I clicked through" without a real check is the exact failure this guards against.
7. **Write the companion doc** — the 10 questions below.
8. **Save** the code and companion doc to `prototype/`.

## Companion Doc — the 10 questions
A FAQ that lives next to the prototype and answers the obvious questions. Not a PRD — lighter, and anchored to the working artifact.
1. **Why** are we doing this? (the problem + the outcome/opportunity it ties to)
2. **Who** is it for, and what decision does it help them make? (audience)
3. What **must work** in V1?
4. What is explicitly **out of scope**? (non-goals)
5. The **core user flow** — the happy path the prototype demonstrates.
6. **Edge cases / failure states** known but not yet handled.
7. **Data** — input sources; mock vs. real.
8. **Assumptions & open questions** (link the LoFA from `assumptions/`).
9. What does **success** look like? (a measurable signal)
10. **Known gaps** — the final 20% engineering must fill (scale, backend, edge handling).

## Quality bar
- The Input/Output/Audience triad is written down before the build starts.
- The prototype runs the core flow start to finish without crashing — tested *before* it is shown.
- 80% of the way there with zero engineering time (non-negotiable); the last 20% is named in the companion doc.
- If `design-system/` exists, tokens are reused; if not, neutral defaults are used and noted in the companion doc.
- All 10 companion-doc questions are answered; non-goals and known gaps are explicit.
- Scope to fit: single screen (concept) · few-screen flow (assumption test) · full happy path (engineering handoff).

## Skill Integration
- **Before:** [generate-solutions](/generate-solutions) for the selected solution, [create-design-brief](/create-design-brief) for visual direction and tokens, [identify-test-assumptions](/identify-test-assumptions) for the assumption under test.
- **Parallel:** [generate-figma-prompt](/generate-figma-prompt) produces a *static visual* mock — a branch, not a replacement (interaction test → prototype; visual exploration → Figma Make).
- **After:** feed test results back into [identify-test-assumptions](/identify-test-assumptions); at handoff, [create-prd](/create-prd) and [generate-tasks](/generate-tasks) treat the prototype + companion doc as their most precise input (the prototype *is* the spec).
- **Workflow:** Solutions → Design Brief → Build Prototype (+ Companion Doc) → Test → Eng handoff
