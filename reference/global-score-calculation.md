# Global Comprehensive Score Calculation Guide

## Purpose

The **Global Comprehensive Score** is an optional secondary metric that incorporates both quantitative (ICEC) and qualitative analysis dimensions into a single numeric score.

**Key Distinction:**
- **ICEC Score**: Primary ranking metric (quantitative only)
- **Global Score**: Comprehensive metric (quantitative + qualitative)

---

## When to Use Global Score

Use the Global Score when:
- You want a single number reflecting the complete analysis
- You need to compare ideas that have very different profiles (e.g., high impact but difficult vs. easy but low impact)
- You want to identify ideas where qualitative factors significantly change the assessment
- You're creating comprehensive reports or presentations

**Continue to use ICEC as the primary sort key** in rankings, but display Global Score as supplementary information.

---

## Step 1: Convert Qualitative Assessments to Numeric Values

### Commercial Viability Conversion

| Assessment | Numeric Value |
|-----------|---------------|
| High | 10 |
| Medium | 6 |
| Low | 3 |
| Unknown | 5 |

### Competition Level Conversion (higher = better for user)

| Competition Level | Numeric Value | Rationale |
|------------------|---------------|-----------|
| Sparse | 10 | Minimal competition = opportunity |
| Emerging | 9 | Early mover advantage possible |
| Moderate | 6 | Healthy competition, room to compete |
| Crowded | 3 | Highly competitive, hard to differentiate |

### Novelty Level Conversion

| Novelty Level | Numeric Value | Rationale |
|--------------|---------------|-----------|
| Novel | 10 | Truly new approach |
| Incremental Innovation | 7 | Meaningful improvement on existing |
| Existing but Improved | 5 | Refinement of known solution |
| Saturated | 2 | Nothing new being offered |

### Implementation Difficulty Conversion (inverted for score)

| Difficulty Level | Raw Value | Inverted for Score | Rationale |
|-----------------|-----------|-------------------|-----------|
| Very Low | 10 | 1 | 11 - 10 = 1 |
| Low | 8 | 3 | 11 - 8 = 3 |
| Medium | 6 | 5 | 11 - 6 = 5 |
| High | 4 | 7 | 11 - 4 = 7 |
| Very High | 2 | 9 | 11 - 2 = 9 |

**Note**: Difficulty is inverted because *easier* execution should contribute *more* to the global score.

### Funding Feasibility Conversion

Assess alignment between funding requirements and user's situation:

| Alignment | Numeric Value | Description |
|-----------|---------------|-------------|
| Perfect | 10 | User has all resources needed or idea is fully bootstrappable with available funds |
| Good | 7 | Achievable with reasonable effort (e.g., small angel raise, revenue-funded within reach) |
| Challenging | 4 | Requires significant capital raising or resources beyond current access |
| Impractical | 2 | Requires resources completely out of reach (e.g., VC-scale funding for pre-revenue founder) |

---

## Step 2: Calculate Global Score

### Formula

```
Global Score = (
  0.40 × ICEC_Score +
  0.15 × Commercial_Viability_Score +
  0.10 × Competition_Score +
  0.10 × Novelty_Score +
  0.15 × Difficulty_Score_Inverted +
  0.10 × Funding_Feasibility_Score
)
```

### Weight Rationale

| Component | Weight | Justification |
|-----------|--------|---------------|
| ICEC | 40% | Foundation - represents core viability dimensions |
| Commercial Viability | 15% | Critical - can't succeed without viable business model |
| Difficulty (inverted) | 15% | High impact - easier ideas more likely to get done |
| Funding Feasibility | 10% | Important - must be able to fund it |
| Competition | 10% | Moderate - matters but can compete in crowded spaces |
| Novelty | 10% | Moderate - incremental ideas can succeed too |

---

## Step 3: Worked Example

### Example Idea: "AI-Powered Local Restaurant Discovery App"

**ICEC Scores:**
- Impact: 7
- Confidence: 8
- Ease: 6
- Contextual Suitability: 7
- **ICEC Score**: (7 + 8 + 6 + 7) / 4 = **7.0**

**Qualitative Assessments:**
- Commercial Viability: **Medium** → 6
- Competition Level: **Crowded** → 3
- Novelty: **Existing but Improved** → 5
- Difficulty: **Medium** → 6 (inverted to 5)
- Funding Feasibility: **Good** → 7

**Global Score Calculation:**

```
Global Score = (
  0.40 × 7.0 +      [ICEC] = 2.80
  0.15 × 6 +        [Viability] = 0.90
  0.10 × 3 +        [Competition] = 0.30
  0.10 × 5 +        [Novelty] = 0.50
  0.15 × 5 +        [Difficulty inverted] = 0.75
  0.10 × 7          [Funding] = 0.70
)

= 2.80 + 0.90 + 0.30 + 0.50 + 0.75 + 0.70
= 5.95

Global Score = 6.0 (rounded to 1 decimal)
```

### Interpretation

- **ICEC Score**: 7.0 (Worth Exploring)
- **Global Score**: 6.0 (Lower than ICEC)

**Divergence Analysis:**
The Global Score is lower than ICEC due to:
- **Crowded competition** (only scored 3/10)
- **Limited novelty** (only scored 5/10)

This divergence suggests: *While fundamentally viable (good ICEC), market dynamics make success harder than ICEC alone suggests.*

---

## Step 4: Document the Calculation

In the analysis JSON, include:

```json
{
  "global_score": {
    "value": 6.0,
    "calculation_breakdown": {
      "icec_component": 2.80,
      "viability_component": 0.90,
      "competition_component": 0.30,
      "novelty_component": 0.50,
      "difficulty_component": 0.75,
      "funding_component": 0.70
    },
    "divergence_from_icec": "Global Score (6.0) is 1.0 points lower than ICEC (7.0) primarily due to crowded competitive landscape and limited novelty. While the idea has solid fundamentals, execution will face significant market challenges."
  }
}
```

---

## Step 5: Interpreting Divergence

### When Global Score > ICEC Score

**Meaning**: Qualitative factors improve the outlook beyond core ICEC assessment.

**Common Causes:**
- Sparse competition in seemingly average space
- Highly novel approach to known problem
- Exceptionally good funding fit for user
- Much easier execution than initially apparent

**Action**: Highlight as **underrated opportunity** worth prioritizing.

---

### When Global Score < ICEC Score

**Meaning**: Qualitative factors introduce challenges not captured by ICEC.

**Common Causes:**
- Crowded competitive space
- Poor commercial viability despite good metrics
- Difficult execution or high complexity
- Funding challenges for user's situation

**Action**: Flag as **higher risk** - proceed with caution despite good ICEC.

---

### When Global Score ≈ ICEC Score (within ±0.5 points)

**Meaning**: Qualitative factors generally align with quantitative assessment.

**Action**: ICEC alone is sufficient for ranking. No special concerns.

---

## Usage in Rankings and Reports

### In rankings.json

Include both scores:

```json
{
  "id": "idea-20250523-001",
  "name": "AI Restaurant Discovery App",
  "icec_score": 7.0,
  "global_score": 6.0,
  ...
}
```

**Sort by**: `icec_score` (primary)
**Secondary sort**: `global_score` (if ICEC tied)

### In Export Reports

Present as:

```
Idea: AI Restaurant Discovery App
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
ICEC Score: 7.0 (Worth Exploring)
Global Score: 6.0 ⚠️ Lower due to market factors

Divergence Note: Crowded competition and limited novelty
reduce practical viability despite solid fundamentals.
```

### In Comparative Analysis

When comparing ideas with different profiles:

| Idea | ICEC | Global | Divergence | Insight |
|------|------|--------|------------|---------|
| A | 7.0 | 8.0 | +1.0 | Underrated - easier + sparse competition |
| B | 7.0 | 6.0 | -1.0 | Overrated - crowded + funding challenges |
| C | 7.0 | 7.0 | 0.0 | Aligned - ICEC accurately represents viability |

---

## Calibration Notes

### Avoiding Score Inflation

- Be conservative with "High" viability assessments
- "Perfect" funding fit should be rare (truly zero barriers)
- "Novel" should be genuinely unprecedented, not just "new to user"

### Avoiding Score Deflation

- Don't penalize "Moderate" competition excessively (most markets have competition)
- "Medium" difficulty is neutral, not negative
- "Incremental Innovation" can be highly valuable (don't over-index on novelty)

---

## Summary

✅ **Global Score complements ICEC** - doesn't replace it
✅ **Highlights market and execution realities** beyond core framework
✅ **Identifies divergences** where qualitative factors significantly matter
✅ **Use ICEC for primary ranking**, Global Score for deeper insight
✅ **Document calculation breakdown** for transparency
✅ **Explain divergences** when Global and ICEC differ by >0.5 points
