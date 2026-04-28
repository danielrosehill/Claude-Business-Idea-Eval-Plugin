---
name: brainstorm-pivots
description: Brainstorm tweaks, additions, or pivots that could improve an idea's feasibility, market readiness, capital efficiency, defensibility, or speed-to-revenue. Produces a ranked list of variants with the trade-off each one buys. Use when an idea has been analysed and the user wants suggestions for how to make it stronger.
---

# Brainstorm Pivots & Tweaks

Generate a slate of variations on the captured idea — small tweaks, feature additions, scope reductions, and full pivots — each scored on what it improves and what it costs.

## Steps

1. Read the idea + all available lens outputs (vc-lens, tam-analysis, b2b-b2c-fit, assumptions, hardware-feasibility, dev-spec, social-impact). The richer the prior analysis, the better the brainstorm.
2. Generate at least 10 variations, mixed across categories:
   - **Scope cuts** — what gets removed to ship faster / cheaper
   - **Feature additions** — non-obvious adjacent features that strengthen the wedge
   - **Customer pivots** — same solution, different segment (e.g. B2C → B2B prosumer)
   - **Business-model pivots** — same product, different monetisation (subscription → marketplace fee → licensing)
   - **Geographic pivots** — start narrow (local market) vs. start global
   - **Wedge swaps** — what if the lead use case were different
   - **Partnership / channel plays** — what if it were sold through an existing distributor
3. For each variation, score:
   - **What it improves** (feasibility, TAM, defensibility, capital efficiency, time-to-revenue, fit-to-user)
   - **What it costs** (complexity, diluted vision, harder GTM, etc.)
   - **Difficulty to evaluate further** (one experiment vs. months of work)
4. Group the slate into:
   - **Top 3 to seriously consider** — biggest improvement, lowest cost
   - **Worth a follow-up conversation** — interesting but unclear
   - **Discarded** — captured for completeness, with one-line rationale

## Output

`<workspace_path>/ideas/<slug>/analysis/brainstorm-pivots.md` with frontmatter:

```markdown
---
lens: brainstorm-pivots
generated: YYYY-MM-DD
top_pick: <one-line>
---
```

## Notes

- Bias the brainstorm toward variations the user could actually execute given their context. A "raise $20M" pivot for a bootstrapper is wasted ink.
- A pivot that improves five dimensions but the user hates is still a bad pivot. Note when a variation conflicts with stated user values.
