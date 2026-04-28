---
name: b2b-b2c-fit
description: Explore B2B vs B2C (and B2B2C, prosumer, marketplace, dev-tool) routings for a captured idea. Lays out pros and cons of each viable model and recommends the best fit given the idea, user context, and capital appetite. Use when the user is unsure which customer segment to target.
---

# B2B / B2C Fit

Many ideas are viable through more than one customer model — but rarely all at once well. Force the choice.

## Steps

1. Read the idea + user context.
2. Enumerate the plausible customer-model routings for this idea. Common candidates:
   - Pure B2C (consumer)
   - Prosumer (power-user consumer / individual professional)
   - SMB B2B
   - Mid-market / enterprise B2B
   - B2B2C (sell to a business that distributes to consumers)
   - Marketplace (two-sided, platform fee)
   - Dev tool / API
   - Open-core / OSS-with-paid-tier
3. For each plausible routing, write a short pros / cons / GTM-shape table:
   - Sales motion (self-serve, inside sales, field, community-led)
   - Sales cycle and ACV/ARPU range
   - Distribution channels
   - What "1000 paying customers" looks like in this model
   - Capital intensity to reach product-market fit
4. **Eliminate** routings that don't fit the user's capital appetite or the idea's structural characteristics. Be explicit about why.
5. **Recommend** one primary routing and one fallback. Note which routings could be added later as the company matures.

## Output

`<workspace_path>/ideas/<slug>/analysis/b2b-b2c-fit.md` with frontmatter:

```markdown
---
lens: b2b-b2c-fit
generated: YYYY-MM-DD
primary: <routing>
fallback: <routing>
---
```

## Notes

- "Both" is rarely the right answer at MVP stage. If the user says "we'll do both", challenge that — sequencing matters.
- Cross-reference TAM analysis if available; some routings will dramatically shrink the addressable market.
