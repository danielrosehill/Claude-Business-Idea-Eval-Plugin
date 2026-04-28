---
name: assumptions-and-objections
description: Surface the load-bearing assumptions in a captured idea and the most likely objections an investor, customer, or skeptical advisor would raise. Produces an assumption-validation plan and an objection-handling brief. Use when the user wants to pressure-test an idea before committing time or capital.
---

# Assumptions & Objections

Every idea sits on a stack of unproven assumptions. List them, rank them, and plan how to validate the load-bearing ones cheaply.

## Steps

1. Read the idea + user context + any prior lens outputs (vc-lens, tam-analysis, b2b-b2c-fit) for additional grounding.
2. Extract **assumptions** in three categories:
   - **Customer** — who they are, what pain they have, what they'll pay
   - **Solution** — that the proposed solution actually solves it; that it can be built
   - **Market / business** — that distribution works, that unit economics are sustainable, that competition won't crush it
3. For each assumption, score (low/medium/high) on:
   - **Confidence** — how sure are we today
   - **Load-bearing** — how much of the business case collapses if it's wrong
   - **Cost to validate** — what cheap experiment would test it (interviews, fake-door landing page, smoke test, hand-built MVP)
4. Sort by `load-bearing × (1 - confidence)` — the riskiest, highest-impact assumptions go to the top.
5. For the top 5, write a one-line validation experiment (the cheapest credible test).
6. Then build an **objections** section — the top ten objections a hostile reviewer would raise, with a one-paragraph rebuttal each (or "no answer yet" honestly noted).

## Output

`<workspace_path>/ideas/<slug>/analysis/assumptions-and-objections.md` with frontmatter:

```markdown
---
lens: assumptions-and-objections
generated: YYYY-MM-DD
top_risk: <one-line>
---
```

## Notes

- Don't pre-rebut objections you can't actually rebut. "We don't have an answer for this yet" is a stronger position than weak hand-waving.
- The validation plan is the most important output — the user should leave with a concrete next experiment to run.
