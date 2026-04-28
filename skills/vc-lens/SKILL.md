---
name: vc-lens
description: Review a captured business idea from a venture-capital lens — market size, defensibility/moat, team-market fit, capital efficiency, exit pathways, traction milestones, and investability. Produces a structured analysis with a clear verdict. Use when the user wants to know how a VC would react to the idea.
---

# VC Lens

Apply a VC-style review to a single idea. Output is a markdown analysis document, not a recommendation.

## Inputs

- Idea slug (must already exist in `<workspace_path>/ideas/<slug>/`)
- The idea's `idea.md` and any `versions/*.md` variants
- User context from `$CLAUDE_USER_DATA/business-idea-eval/user-context.md`

## Analysis dimensions

Address each in 1–3 paragraphs:

1. **Problem & customer** — pain severity, frequency, who actually pays, willingness-to-pay signal
2. **Market** — TAM/SAM/SOM rough sizing (defer detail to `tam-analysis`), category maturity
3. **Wedge & differentiation** — what's the initial wedge, why now, what's the unfair advantage
4. **Moat** — network effects, data, regulatory, switching cost, brand, scale economies — or honest absence
5. **Business model** — unit economics intuition, pricing power, GTM motion (PLG / sales-led / hybrid)
6. **Capital intensity** — bootstrap-viable, seed-friendly, or capital-hungry; rough burn-to-milestone estimate
7. **Team-market fit** — is the founder (the user, per user-context.md) credibly positioned to win this
8. **Exit landscape** — strategic acquirers, public-market path, or lifestyle business — set expectations honestly
9. **Risks** — top three, ranked, with severity
10. **Verdict** — investable as-is / investable with changes / fund-of-friends or bootstrap only / pass

## Output

Write to `<workspace_path>/ideas/<slug>/analysis/vc-lens.md` with frontmatter:

```markdown
---
lens: vc-lens
generated: YYYY-MM-DD
verdict: <one of the four verdicts>
---
```

## Notes

- Calibrate to the user's actual situation per `user-context.md`. Don't tell a bootstrapper "raise a Series A" if they explicitly want to stay self-funded.
- Be direct. Empty validation is worse than honest pushback.
- Cross-reference `reference/scorecard.md` (ICEC) if the user wants quantitative scoring layered on top.
