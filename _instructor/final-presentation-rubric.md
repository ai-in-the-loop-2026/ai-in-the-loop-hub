# Final Presentation Grading Sheet
Creating with AI in the Loop — `_instructor/final-presentation-rubric.md`

Internal grading sheet for the Week 15 final presentations (Thu, April 30). Student-facing version (without the level descriptors) lives in [`resources/final_project.md`](../resources/final_project.md#presentation).

**Total: 25 points.** Each category scored on the 5-point ladder: **5 Exemplary · 4 Proficient · 3 Developing · 2 Beginning · 0–1 Missing**.

The presentation slot is 5% of the final-project grade, so each rubric point ≈ 0.2% of project total.

---

## Problem framing & motivation (5 pts)

- **5 —** Specific user and use case clearly articulated. Audience understands the problem and why it matters *before* the demo. Grounded — not generic ("students," "anyone").
- **4 —** Problem and audience are clear; framing could be sharper but the "why" lands.
- **3 —** Problem identified but audience or value is fuzzy. Use case must be inferred.
- **2 —** Vague problem statement; jumps to features without grounding the user.
- **0–1 —** No clear problem framing.

## Live demo (5 pts)

- **5 —** App runs end-to-end smoothly. Well-paced, focused on the core value; the polished interface shines. The "this is cool" moment lands.
- **4 —** Demo works and communicates the value. Slight pacing/focus issues, or a minor hiccup handled gracefully.
- **3 —** Demo runs but is unfocused, rushed, or buries the value. *Or* a meaningful failure with awkward recovery.
- **2 —** Demo partially works or repeatedly stumbles; core value hard to see.
- **0–1 —** Demo fails to run, or no live demo attempted.

## Technical approach (5 pts)

- **5 —** Architecture explained at the right altitude — names the moving parts (tools, conditional routing, custom state) and how they fit, without reading code. Design choices are justified.
- **4 —** Architecture is clear; key components named. May skim one element or briefly drift into the weeds.
- **3 —** Audience gets the gist, but the explanation is either too vague or too deep (code on slides). Required features mentioned but not contextualized.
- **2 —** Confusing, missing key components, or pitched at the wrong altitude.
- **0–1 —** No meaningful technical explanation.

## Challenges & learning (5 pts)

- **5 —** Honest, specific reflection. Names concrete challenges, what was tried, what worked, what they'd do differently. Shows what they understand now that they didn't before.
- **4 —** Real challenges with thoughtful reflection. Leans on outcomes more than learnings.
- **3 —** Challenges acknowledged but reflection is generic ("it was hard," "we learned a lot").
- **2 —** Reflection is superficial or skipped. Reads as a feature list rather than learning.
- **0–1 —** No reflection on challenges or learning.

## Delivery & teamwork (5 pts)

- **5 —** Slides clean and readable. All team members speak; handoffs are smooth. Within the 10–15 min window. Q&A handled confidently.
- **4 —** Solid with minor issues — uneven speaking time, slightly over/under time, or one cluttered slide.
- **3 —** Noticeable issues: meaningfully off time, hard-to-read slides, one member dominates or disengages, Q&A struggles.
- **2 —** Multiple compounding delivery problems.
- **0–1 —** Disorganized or absent delivery.

---

## Per-team scoring template

| Category | Score (/5) | Notes |
|---|---|---|
| Problem framing & motivation |   |   |
| Live demo |   |   |
| Technical approach |   |   |
| Challenges & learning |   |   |
| Delivery & teamwork |   |   |
| **Total** | **/25** |   |

## Calibration reminders

- **Demo > slides.** The live demo is the highest-signal moment. Don't let polished slides paper over a weak demo, and don't penalize rough slides for a strong demo.
- **"Technical approach" ≠ code review.** Full credit if they can say "this tool searches the docs, this conditional edge routes back to the LLM if confidence is low, this state field tracks the user's plan." Code on slides is a *negative* signal at this altitude — that's what Monday's code review is for.
- **Reflection is where growth shows.** "We learned a lot" is a 3. "We thought RAG would solve X but it kept hallucinating citations, so we added a verification node" is a 5.
