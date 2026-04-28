---
name: synthesize-analysis
description: Consolidate all available analysis for a single idea (lens outputs, council deliberation, comparisons) into one timestamped unified assessment with a clear verdict and recommended next step. Use after the user has run multiple lenses and wants a single document that pulls it all together.
---

# Synthesize Analysis

Produces a unified, timestamped assessment that brings together every per-lens output for one idea.

## Steps

1. Read the idea workspace `<workspace_path>/ideas/<slug>/`:
   - `idea.md` and any `versions/*.md`
   - All `analysis/*.md`
   - All `council/*.md` or `council-karpathy/*.md` if present
2. Build the synthesis as a single markdown document with these sections:
   - **Idea summary** — 2–3 sentence reduction of the captured idea
   - **What we know** — 1-paragraph distillation of each lens, naming each
   - **Where the lenses agree** — points of convergence across analyses
   - **Where the lenses disagree** — genuine tensions; do not resolve them artificially
   - **The council's verdict** — if council outputs exist, summarise the chairman synthesis and call out dissent
   - **Top assumptions to validate next** — pull from `assumptions-and-objections.md` if present
   - **Recommended next step** — one concrete action: a validation experiment, a build phase to start, or a kill decision
   - **Verdict** — one of: Strong Pursue / Pursue with Changes / Hold for Validation / Pass / Pivot Required
3. Tag the synthesis with timestamp so multiple runs accumulate (don't overwrite earlier syntheses).

## Output

`<workspace_path>/ideas/<slug>/synthesis/YYYY-MM-DD-HHMM.md` with frontmatter:

```markdown
---
type: idea-synthesis
generated: YYYY-MM-DD HH:MM
verdict: <one of the five>
inputs: [<list of source files folded in>]
---
```

## Notes

- Always write to a new timestamped file. The history of syntheses is itself useful — it shows how thinking evolved.
- If only one or two lenses have been run, synthesise honestly with that limited base — don't pad.
- The recommended next step must be concrete enough to act on this week, not a vague "do more research".
