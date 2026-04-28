---
name: timeline-and-project
description: Produce a milestone-based timeline and project plan for taking an idea from today to first paying customer (or first deployment). Identifies critical path, parallelisable workstreams, and key checkpoints. Use when the user wants to know "what's the realistic path and how long".
---

# Timeline & Project Plan

Translate an idea + dev spec into an executable project plan with honest durations.

## Steps

1. Read the idea, dev spec (or hardware feasibility), assumptions output.
2. Define the **target milestone** — typically "first paying customer" for B2C/B2B SaaS, "first pilot deployment" for hardware/enterprise, "first 1000 active users" for consumer.
3. Lay out the path as a sequence of milestones, e.g.:
   - M1: validate top assumption (week 1–2)
   - M2: MVP feature-complete in dev (week 3–8)
   - M3: closed beta with N users (week 9–12)
   - M4: paid launch (week 13–16)
   For each milestone: deliverables, exit criteria, dependencies.
4. Identify the **critical path** — what blocks each milestone. Call out any single-threaded bottleneck.
5. Identify **parallelisable workstreams** — branding/positioning, customer development, partnership conversations, regulatory prep — that can run alongside engineering.
6. Note **decision gates** — points where the user should re-evaluate continuing (e.g. after M1: did the assumption validate? if not, kill or pivot).

## Output

`<workspace_path>/ideas/<slug>/analysis/timeline-and-project.md` with frontmatter:

```markdown
---
lens: timeline-and-project
generated: YYYY-MM-DD
target_milestone: <text>
target_weeks: <number>
critical_path: <short summary>
---
```

## Notes

- Be honest about durations. Solo founder building part-time goes 3-5x slower than a funded team.
- Always include a kill criterion. Plans without a kill criterion become endless.
