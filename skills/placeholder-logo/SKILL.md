---
name: placeholder-logo
description: Generate a placeholder logo for an idea via an AI image model (fal / nano-banana). Produces a simple wordmark or icon for use in early decks and one-pagers — explicitly placeholder-grade, not a final brand identity. Use when the user wants a visual stand-in for an idea before committing to design.
---

# Placeholder Logo

Generate a quick visual identity stand-in. Frame it as placeholder — not a substitute for a designer.

## Steps

1. Take the chosen working name (from `name-suggestions` or user-supplied) and a one-sentence description of the idea.
2. Pick a generation backend in this order of preference:
   - `fal-ai` on the MCP gateway (`mcp__gateway__fal-ai__generate_image`; `mcp__gateway__fal-ai__recommend_model` / `list_models` to pick a model) — has multiple model options
   - `nano-tech-diagrams` MCP server (`mcp__gateway__nano-tech-diagrams__text_to_image`) — for diagram-style logos
   - HuggingFace FLUX-1-schnell via `mcp__gateway__huggingface__FLUX_1-schnell-infer` — fallback
   Confirm with the user which backend / model they prefer.
3. Generate **three style variants** in one pass, each as a separate prompt:
   - **Wordmark** — clean typography of the name, minimal ornamentation
   - **Icon + wordmark** — small abstract mark plus the name
   - **Standalone icon** — just the mark, no text
4. Suggest a colour palette in the prompt (default: muted single-colour on white; let user override).
5. Save outputs to `<workspace_path>/ideas/<slug>/exports/logo/`:
   - `wordmark-<YYYYMMDD>.png`
   - `icon-wordmark-<YYYYMMDD>.png`
   - `icon-<YYYYMMDD>.png`
6. Show the user the three options and ask which to keep / regenerate.

## Notes

- Always frame outputs as placeholder. Do not represent these as production brand assets.
- AI-generated logos may inadvertently resemble existing trademarks. Flag this risk before the user uses the logo publicly.
- For a final brand identity, point the user at hiring a designer — this skill exists to unblock the next step (deck, one-pager), not to replace design work.
