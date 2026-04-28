---
name: council-review-karpathy
description: Run a multi-persona LLM-council review using Andrej Karpathy's original llm-council Python implementation. Clones the repo into a temp scratch dir, configures it for the user's idea, runs it, and copies outputs back into the idea workspace. Use when the user explicitly wants the canonical implementation rather than the native subagent variant.
---

# Council Review (Karpathy)

Wraps the upstream https://github.com/karpathy/llm-council implementation. We do not vendor the code — we clone it on demand into a scratch directory and run it from there.

## Steps

1. Verify prerequisites: `python3`, `git`, and an LLM API key the upstream tool supports (typically `OPENAI_API_KEY` or `ANTHROPIC_API_KEY` — check upstream README at clone time).
2. Choose a scratch directory:
   ```bash
   SCRATCH="${CLAUDE_USER_DATA:-${XDG_DATA_HOME:-$HOME/.local/share}/claude-plugins}/business-idea-eval/scratch/llm-council"
   mkdir -p "$(dirname "$SCRATCH")"
   ```
3. Clone (or pull) the upstream repo into `$SCRATCH`. Don't commit it anywhere; this is throwaway.
4. Read `$SCRATCH/README.md` (it may have changed since this skill was written) and follow its current setup steps. Do not assume specific commands — read what's there.
5. Prepare the prompt input from the idea workspace:
   - Concatenate `idea.md` + the formatted summary version (if present) + a short user-context paragraph
   - Save as the input file in whatever format the upstream tool expects
6. Configure the council personas to match the six in `reference/council-deliberation.md`. The upstream tool typically accepts custom persona prompts via a config file.
7. Run the council deliberation per upstream instructions.
8. Copy outputs into the idea workspace:
   ```
   <workspace_path>/ideas/<slug>/council-karpathy/
     <whatever-files-the-tool-produces>
   ```
9. Optionally write a small index file listing the outputs and the run metadata (model used, timestamp, persona config).

## Notes

- The upstream tool may require API costs the user should be aware of — show the rough request count before running.
- Do not commit the scratch clone to any repo. It exists only for the run.
- If the upstream tool's interface has drifted, fall back to `council-review-subagents` and report the drift to the user.
- Output schema differs from the subagent variant; downstream skills (synthesize-analysis, internal-pdf) handle both folder layouts.
