# Business Idea Eval

Claude Code plugin for evaluating, refining, and developing business ideas. Capture an idea (text or voice), apply structured analytical lenses, run an LLM-council deliberation, synthesise the findings, and export polished documents — internal or public-facing — plus a placeholder logo and name suggestions.

Successor to the `Claude-Business-Evaluator` template repo. The methodology assets (ICEC scorecard, PRGX scorecard, six-persona council) are ported into this plugin's `reference/` directory.

## Skills

### Setup
- `onboard` — first-run setup; pick workspace path and capture user context

### Capture
- `capture-idea` — text input → structured workspace, with optional executive summary, elevator pitch, technical deep-dive, and timeline variants
- `capture-voice-idea` — audio file → transcript → structured workspace (uses `claude-transcription` plugin if installed)

### Analytical lenses
- `vc-lens` — VC-style review (market, moat, capital efficiency, exit, verdict)
- `tam-analysis` — top-down + bottom-up TAM / SAM / SOM with reconciliation
- `b2b-b2c-fit` — explore B2B / B2C / B2B2C / prosumer / marketplace / dev-tool routings
- `assumptions-and-objections` — surface load-bearing assumptions and likely objections
- `hardware-feasibility` — BOM, hardest engineering risks, prototyping plan, cert path
- `dev-spec` — system architecture sketch, components, build phases, MVP effort
- `timeline-and-project` — milestone-based plan to first revenue / first deployment
- `social-impact-lens` — non-financial review: beneficiaries, harms, externalities, mission-coherence

### Council
- `council-review-subagents` — six-persona LLM council via parallel Claude subagents (Operator, Financier, Skeptic, Visionary, Customer Advocate, Strategist) with blind ranking and chairman synthesis
- `council-review-karpathy` — wrapper that clones [karpathy/llm-council](https://github.com/karpathy/llm-council) on demand and runs the canonical implementation

### Comparison & synthesis
- `compare-ideas` — head-to-head ranked comparison across multiple ideas in the workspace
- `brainstorm-pivots` — generate scope cuts, feature additions, customer pivots, model pivots
- `synthesize-analysis` — consolidate every lens + council output for one idea into a timestamped unified assessment

### Output generation

**Internal:**
- `internal-pdf` — render any analysis as a Typst PDF for personal records

**Public-facing:**
- `public-onepager` — single-page shareable PDF (Typst)
- `public-pitch-deck-outline` — 12-slide markdown pitch-deck outline

**Branding:**
- `name-suggestions` — domain and product name candidates with availability checks
- `placeholder-logo` — AI-generated placeholder logo via fal / nano-banana / FLUX

## Workspace layout

The plugin keeps idea data under a user-chosen path (configured during `onboard`):

```
<workspace_path>/
  ideas/
    <idea-slug>/
      idea.md                # raw capture, never edited
      versions/              # formatted variants (exec summary, elevator pitch, ...)
      analysis/              # one file per lens
      council/               # per-persona + chairman synthesis
      synthesis/             # timestamped unified assessments
      exports/               # PDFs, decks, logos
  comparisons/               # workspace-level cross-idea comparisons
```

Plugin config (workspace pointer, user context path, council default) lives at:

```
${CLAUDE_USER_DATA:-${XDG_DATA_HOME:-$HOME/.local/share}/claude-plugins}/business-idea-eval/
```

## Reference content (ported from Claude-Business-Evaluator)

- `reference/scorecard.md` — ICEC methodology (Impact, Confidence, Ease, Contextual Suitability)
- `reference/business-performance-scorecard.md` — PRGX methodology (Performance, Resilience, Growth, Contextual Fit)
- `reference/council-deliberation.md` — six-persona council pattern, blind-ranking protocol
- `reference/comprehensive-analysis-dimensions.md` — extended dimension list
- `reference/global-score-calculation.md` — scoring math
- `schemas/*.json` — JSON schemas for analysis, batch ranking, business analysis, rankings

## Installation

```bash
claude plugins marketplace add danielrosehill/Claude-Code-Plugins
claude plugins install business-idea-eval@danielrosehill
```

Restart Claude Code after install. Run `onboard` first.

## License

MIT
