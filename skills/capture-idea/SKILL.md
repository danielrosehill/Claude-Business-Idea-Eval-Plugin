---
name: capture-idea
description: Capture a new business idea from text input into a structured workspace. Always preserves the raw input verbatim and offers optional formatted versions — executive summary, elevator pitch, technical deep-dive, and timeline/project plan. Use when the user wants to start a new idea workspace from a written description, brain-dump, or pasted text.
---

# Capture Idea (text)

Creates a new idea workspace under `<workspace_path>/ideas/<idea-slug>/` and lays down the raw input plus any formatted variants the user requests.

## Steps

1. Read `$CLAUDE_USER_DATA/business-idea-eval/config.json` for `workspace_path`. If absent, run `onboard`.
2. Take the raw idea text from the user (paste, file, or dictation that's already been transcribed).
3. Derive an idea slug — short, kebab-case, descriptive. Confirm with the user before creating the directory.
4. Scaffold:
   ```
   <workspace_path>/ideas/<idea-slug>/
     idea.md              # raw input, verbatim, with frontmatter (created date, source)
     versions/            # formatted variants
     analysis/            # lens outputs
     council/             # council deliberation outputs
     synthesis/           # consolidated assessments
     exports/             # rendered PDFs
   ```
5. Write `idea.md` with frontmatter:
   ```markdown
   ---
   slug: <idea-slug>
   captured: YYYY-MM-DD
   source: text | voice | imported
   ---

   <verbatim raw input>
   ```
6. Offer the user a menu of formatted variants (any combination):
   - **Executive summary** — 150–250 words, one-pager-style, problem/solution/market/why-now
   - **Elevator pitch** — three options: 30-second, 60-second, 2-minute
   - **Technical deep-dive / spec outline** — architecture sketch, key components, build phases, hard problems
   - **Timeline & project plan** — milestone-based, MVP → public launch, with rough effort estimates and dependencies
7. For each variant requested, write to `versions/<variant>.md`. Keep them clearly labelled as derived/edited so the raw stays canonical.
8. Print the new directory path and the list of files written.

## Notes

- Never edit `idea.md` after creation — it's the source of truth. Formatted variants live in `versions/`.
- If the user only wants raw capture, skip the menu.
- Idea slug should be unique within the workspace; if a collision exists, append a short suffix and confirm.
