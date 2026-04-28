# Council Deliberation Method

## Overview

The Council method replaces single-voice evaluation with a 6-personality deliberation. Instead of one evaluator scoring an idea or business, six distinct analytical personas each provide independent assessments, then blindly rank each other's work, and finally a chairman synthesizes the result.

This produces richer, more balanced evaluations by forcing genuinely different perspectives into the process.

---

## The Six Personas

### 1. The Operator
Thinks about execution, operations, and day-to-day reality. Focuses on whether this can actually be built and run. Asks: What does the first week look like? Where are the operational bottlenecks? What breaks at scale?

### 2. The Financier
Thinks in numbers, unit economics, and return on capital. Focuses on whether the math works. Asks: What are the margins? When does cash flow turn positive? What's the downside exposure?

### 3. The Skeptic
Stress-tests everything. Identifies risks, failure modes, and uncomfortable truths. Not negative for its own sake — essential voice of caution. Asks: What are we not seeing? What kills this? What if the key assumption is wrong?

### 4. The Visionary
Sees opportunity and potential. Focuses on the upside scenario and what this could become. Asks: What if this works brilliantly? What adjacent opportunities open up? What's the 10x version?

### 5. The Customer Advocate
Thinks from the buyer's perspective. Focuses on whether anyone actually wants this. Asks: Would I pay for this? What problem does this solve better than alternatives? What's the switching cost from existing solutions?

### 6. The Strategist
Thinks about positioning, timing, and competitive dynamics. Focuses on market fit and defensibility. Asks: Why now? Why this team? What's the moat? How does the competitive landscape evolve?

---

## Three-Stage Deliberation Process

### Stage 1: Independent Assessment

Each persona evaluates the idea/business independently. They each produce:
- Their perspective on each scoring dimension (ICEC for ideas, PRGX for businesses)
- Suggested scores with reasoning
- Key insights unique to their lens
- Recommended action

**Format per persona:**
```
## [Persona Name] Assessment

### Perspective
[2-3 paragraphs of analysis from this persona's viewpoint]

### Suggested Scores
- [Dimension 1]: [score] — [one-line reasoning]
- [Dimension 2]: [score] — [one-line reasoning]
- [Dimension 3]: [score] — [one-line reasoning]
- [Dimension 4]: [score] — [one-line reasoning]

### Key Insight
[The single most important thing this persona wants the group to consider]

### Recommended Action
[What this persona thinks the owner should do]
```

### Stage 2: Blind Ranking

All six assessments are anonymized (labeled Assessment A through F) and each persona ranks them from most to least compelling. This prevents authority bias and forces evaluation on merit.

**Ranking criteria:**
- Quality and depth of reasoning
- Strength of evidence cited
- Practical actionability of insights
- Honesty and realism of assessment

**Output:** Aggregate ranking revealing which perspectives were most valued by peers.

### Stage 3: Chairman Synthesis

A synthesis pass reviews all six assessments plus the peer rankings to produce the final evaluation. The chairman:

1. Identifies points of **consensus** (where 4+ personas agree)
2. Highlights **productive disagreements** (where divergent views reveal important tensions)
3. Weights insights by peer ranking quality
4. Produces final scores with reasoning that references specific persona contributions
5. Generates a unified recommendation

---

## When to Use Council Mode

- **High-stakes decisions**: Ideas or businesses where getting it wrong has significant consequences
- **Close calls**: When a quick single-evaluator pass produces borderline scores
- **Complex situations**: Multi-dimensional problems where one perspective is insufficient
- **Second opinions**: When you want to stress-test a previous evaluation

Council mode takes longer but produces substantially richer analysis. Use single-evaluator mode for quick triage, council mode for decisions that matter.

---

## Output Format

Council deliberations are saved to `output/council-deliberations/` as JSON files containing:
- All six Stage 1 assessments (with persona attribution)
- Stage 2 blind rankings (anonymized inputs, attributed results)
- Aggregate ranking scores
- Stage 3 chairman synthesis
- Final scores and recommendation
