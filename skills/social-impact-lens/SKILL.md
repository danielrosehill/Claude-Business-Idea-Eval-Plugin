---
name: social-impact-lens
description: Review a captured idea from a social-impact and ethics lens — who benefits, who is harmed, second-order societal effects, environmental footprint, accessibility, and alignment with the user's personal values. Use when the user wants to weigh non-financial considerations.
---

# Social Impact Lens

Not every idea worth building optimises for return. Apply a non-financial review.

## Steps

1. Read the idea + user context (especially any stated values).
2. Address each dimension:
   - **Direct beneficiaries** — who is materially better off if this succeeds; how much
   - **Direct harmed** — who loses (incumbents disrupted, jobs displaced, attention extracted)
   - **Second-order effects** — what happens at scale; who pays externalities
   - **Environmental footprint** — energy, materials, e-waste, carbon — qualitatively
   - **Accessibility & inclusion** — who can / can't use this; pricing access; cognitive/physical accessibility
   - **Mission-coherence** — does pursuing this align with the user's stated values, per `user-context.md`
   - **Reputation risk** — what story would a hostile journalist write about this in three years
3. Score each on a simple scale (Net positive / Mixed / Net negative) with one sentence of reasoning.
4. Flag any dimension where the idea is structurally problematic. Don't soft-pedal.

## Output

`<workspace_path>/ideas/<slug>/analysis/social-impact-lens.md` with frontmatter:

```markdown
---
lens: social-impact-lens
generated: YYYY-MM-DD
overall: <Net positive | Mixed | Net negative>
---
```

## Notes

- Don't moralise. Surface trade-offs honestly and let the user decide.
- If user-context.md has explicit values (e.g. "I won't build anything that exploits attention"), use them as the spine of the analysis.
