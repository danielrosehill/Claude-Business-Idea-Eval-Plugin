---
name: hardware-feasibility
description: For ideas that involve a physical product, sketch a bill of materials, identify the hardest engineering risks, propose feasibility tests, and estimate prototyping cost. Only use when the idea has a hardware component — skip for pure-software ideas.
---

# Hardware Feasibility

Hardware ideas die on three rocks: BOM cost at volume, regulatory / certification, and manufacturing tolerance. Surface them early.

## Steps

1. Read the idea. Confirm with the user that there's a meaningful hardware component (not just "an app that connects to existing hardware").
2. Sketch a **bill of materials** (BOM) at small volume (1, 100, 1000 units). For each line:
   - Component category
   - Likely supplier or off-the-shelf module reference
   - Approximate unit cost at each volume
   - Lead time / supply-chain risk note
3. Identify **hardest engineering problems** — the components or integrations that aren't off-the-shelf and require real R&D. For each, note:
   - What's hard about it
   - Whether a prior art / open-source design exists
   - Estimated engineering effort (weeks of one engineer)
4. **Feasibility tests** — propose a phased prototyping plan:
   - **Phase 0**: bench breadboard / dev kit proving the riskiest function works at all
   - **Phase 1**: integrated prototype, ugly, single unit
   - **Phase 2**: form-factor prototype, externally presentable
   - **Phase 3**: pilot run / DFM iteration
   For each phase, estimate cost and duration.
5. **Regulatory & certification** — note any required certifications (FCC, CE, FDA, UL, etc.) given target geography and category. Flag long-lead items.
6. **Path to manufacturing** — contract manufacturer landscape (US, EU, China, Israel/local), ODM vs. CM vs. self-manufacture trade-off.

## Output

`<workspace_path>/ideas/<slug>/analysis/hardware-feasibility.md` with frontmatter:

```markdown
---
lens: hardware-feasibility
generated: YYYY-MM-DD
bom_estimate_v1_usd: <number>
hardest_risk: <one-line>
---
```

## Notes

- Use WebSearch to verify component price ranges; don't invent.
- A hardware idea where the hardest problem hasn't been built before by anyone is much riskier than one composed of solved sub-problems integrated cleverly.
