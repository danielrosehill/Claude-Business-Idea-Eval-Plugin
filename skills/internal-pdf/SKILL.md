---
name: internal-pdf
description: Render an idea's analysis (single lens, full synthesis, or council deliberation) as a Typst PDF for internal/personal use. Picks a clean working-document format with metadata and timestamp. Use when the user wants a portable, archivable version of an analysis for their own records.
---

# Internal PDF

Render any analysis output as a polished but workmanlike PDF — for the user's own files, not for sharing externally.

## Steps

1. Ask the user what to render. Options:
   - A single lens analysis (e.g. `vc-lens.md`)
   - The latest synthesis (`synthesis/YYYY-MM-DD-HHMM.md`)
   - The chairman synthesis from a council run
   - The full bundle: idea + every lens + synthesis as one document
2. If a Typst rendering plugin is installed (`typst-document-generator:personal-doc` or `repo-to-content:repo-to-internal-doc`), prefer it — pass the markdown source and the desired template.
3. Otherwise fall back to a self-contained Typst template bundled in this plugin's `templates/internal/main.typ` (basic IBM Plex Sans, page header with idea slug, page footer with timestamp).
4. Compile via `typst compile` to `<workspace_path>/ideas/<slug>/exports/<source-filename>-<YYYYMMDD>.pdf`.
5. Print the output path.

## Notes

- Internal PDFs include the timestamp and the full source file list — they're working documents, not deliverables.
- For something to share externally, use `public-onepager` or `public-pitch-deck-outline` — they apply different formatting and strip internal-only sections.
- If `typst` isn't installed, tell the user to install it (`apt install typst` on Ubuntu) — don't fall back to a different toolchain silently.
