---
name: tam-analysis
description: Estimate Total Addressable Market, Serviceable Addressable Market, and Serviceable Obtainable Market for a captured idea. Uses both top-down (industry reports, public stats) and bottom-up (price × users) approaches and reconciles them. Use when the user wants market sizing for an idea.
---

# TAM / SAM / SOM Analysis

Sizing is always wrong but the discipline is useful. Produce two independent estimates and reconcile.

## Steps

1. Read the idea + user context.
2. Identify the buying unit (end consumer, SMB, mid-market, enterprise, developer, etc.) and the geography (global, region, single country).
3. **Top-down**: cite the broadest plausible industry category, look up published market size (use WebSearch / WebFetch for current figures — do not invent), narrow by relevance percentages with explicit reasoning.
4. **Bottom-up**: estimate number of buying units × ARPU/ACV × annual purchase frequency. Show every assumption.
5. Reconcile — if top-down and bottom-up are >5x apart, find the error before reporting.
6. Define SAM (the slice the company can realistically reach in its initial geography/segment) and SOM (a credible 3-year capture).
7. Note category dynamics: growing / flat / declining; consolidating / fragmenting.

## Output

`<workspace_path>/ideas/<slug>/analysis/tam-analysis.md` with frontmatter:

```markdown
---
lens: tam-analysis
generated: YYYY-MM-DD
tam_usd: <number>
sam_usd: <number>
som_3y_usd: <number>
geography: <scope>
---
```

Body must include the assumption table for both top-down and bottom-up, plus a one-paragraph confidence note.

## Notes

- Use WebSearch for current market data; cite sources inline.
- If the idea is hyper-niche and no published category exists, document that — and suggest the analogous category that bounds it from above.
- Round numbers honestly. Five significant figures is false precision.
