---
name: compare-ideas
description: Compare multiple captured ideas head-to-head across explicit dimensions — commercial prospect, speed to first revenue, capital intensity, fit-to-user, defensibility, social impact — and produce a ranked recommendation. Use when the user has 2+ ideas in the workspace and wants help choosing where to focus.
---

# Compare Ideas

Ranked head-to-head comparison across the user's idea portfolio.

## Steps

1. Read `<workspace_path>/ideas/` — list available idea slugs. Confirm with the user which ideas to include in the comparison (default: all ideas with at least one lens analysis).
2. For each idea, gather the available lens outputs. If an idea has only `idea.md` and no analysis, warn the user that the comparison will be shallow for that one.
3. Score each idea on a consistent rubric (1–10):
   - **Commercial prospect** (TAM, defensibility, pricing power)
   - **Speed to first revenue** (weeks to first paying customer)
   - **Capital efficiency** (how far user can take it on bootstrap budget)
   - **Fit to user** (per user-context.md — domain expertise, capital appetite, risk profile, values)
   - **Defensibility / moat**
   - **Social impact alignment**
   - **Solo-buildable** (can the user, plus realistic help, ship it)
4. Compute a weighted overall (default equal weights — let the user override).
5. Build a comparison matrix table.
6. Write a verdict paragraph: which idea to pursue first, which to defer, which to drop. Be opinionated.

## Output

`<workspace_path>/comparisons/YYYY-MM-DD-HHMM.md` (workspace-level, not per-idea) with frontmatter:

```markdown
---
type: idea-comparison
generated: YYYY-MM-DD
ideas: [<slug1>, <slug2>, ...]
ranked: [<slug>, <slug>, ...]
recommended: <slug>
---
```

## Notes

- If the user has done deep analysis on some ideas and not others, weight the comparison conservatively for the under-analysed ones (mark scores as low-confidence).
- Surface non-numeric considerations the rubric misses — e.g. "Idea A is the rational choice but you've told me you don't want to spend three years in B2B sales".
