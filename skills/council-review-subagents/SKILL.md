---
name: council-review-subagents
description: Run a multi-persona LLM-council review of an idea using Claude Code subagents — six personas (Operator, Financier, Skeptic, Visionary, Customer Advocate, Strategist) each review the idea independently, then a chairman synthesizes. Runs entirely inside the Claude harness — no external code or repo clone. Faster path; use unless the user wants the original Karpathy implementation.
---

# Council Review (Subagents)

Inspired by the LLM-council pattern (https://github.com/karpathy/llm-council), implemented natively as parallel Claude Code subagents.

## Personas

The six personas live in `reference/council-deliberation.md`:

1. **The Operator** — execution, operations, day-to-day reality
2. **The Financier** — numbers, unit economics, returns
3. **The Skeptic** — risks, failure modes, uncomfortable truths
4. **The Visionary** — upside, adjacent opportunities
5. **The Customer Advocate** — buyer perspective, real demand
6. **The Strategist** — positioning, timing, competitive dynamics

## Steps

1. Read the idea + user-context + any existing lens analyses (the council should be informed by them, not repeat them).
2. Spawn six subagents **in parallel** (all in a single tool-call message, one Agent call each, `subagent_type: general-purpose`). Each gets:
   - The full idea text
   - User context
   - Available prior lens outputs
   - A persona briefing extracted from `reference/council-deliberation.md`
   - Instruction to produce: a structured assessment + a 1-line verdict + a 0–10 score
3. Collect the six independent assessments. Write each to `<workspace_path>/ideas/<slug>/council/<persona>.md`.
4. **Blind ranking pass** — spawn one more subagent that receives the six assessments anonymized (labelled A–F, persona names stripped) and ranks them by the quality of reasoning. This is the LLM-council twist: peer evaluation.
5. **Chairman synthesis** — produce a final synthesis as a single document. The chairman:
   - Reads all six assessments + the blind ranking
   - Produces a unified verdict that gives more weight to higher-ranked assessments
   - Flags genuine disagreements between personas (don't paper over)
   - Issues one of: Strong Pursue / Pursue with Changes / Hold for More Validation / Pass
6. Write the chairman synthesis to `<workspace_path>/ideas/<slug>/council/chairman-synthesis.md`.

## Output

Council folder structure after a run:

```
council/
  the-operator.md
  the-financier.md
  the-skeptic.md
  the-visionary.md
  the-customer-advocate.md
  the-strategist.md
  blind-ranking.md
  chairman-synthesis.md
```

## Notes

- All six initial subagents must run in parallel. Sequential personas defeats the parallel-perspective pattern.
- Don't let the chairman "average" the personas. The point is principled disagreement, not consensus.
- See `council-review-karpathy` for the variant that runs the original Python implementation.
