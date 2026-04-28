---
name: public-onepager
description: Generate a public-facing one-pager PDF for a business idea — designed for sharing with potential cofounders, advisors, or early customers. Strips internal-only analysis (council dissent, raw assumptions, kill criteria) and presents a clean, persuasive summary. Use when the user wants a shareable artifact for an idea.
---

# Public One-Pager

External-facing single-page summary. Different audience, different rules: this is marketing, not analysis.

## Steps

1. Read the idea, the latest synthesis, and any explicit "elevator pitch" / "executive summary" variants from `versions/`.
2. Compose the one-pager content:
   - **Headline** — one sentence that an outsider can repeat after reading once
   - **Problem** — three sentences max, framed in customer language not industry jargon
   - **Solution** — what we're building and the wedge
   - **Why now** — the structural shift that makes this the right time
   - **Market** — pulled from `tam-analysis.md` if present (round numbers, no false precision)
   - **Team** — one paragraph drawn from `user-context.md`, calibrated for outside reader
   - **Traction or next milestone** — what's been validated, what's next
   - **Ask** — what is the user asking the reader for (advice / introductions / capital / pilot customer)
3. **Strip aggressively** — no lens labels, no internal council debate, no "we don't know yet" hedging in copy (those go into `internal-pdf` not here).
4. Render via Typst. Prefer `typst-document-generator:public-doc` if installed; otherwise use this plugin's `templates/public/onepager.typ`.
5. Output to `<workspace_path>/ideas/<slug>/exports/onepager-<YYYYMMDD>.pdf`.

## Notes

- The user's "ask" is critical and often missing. Push for it explicitly before generating.
- Show the user the markdown copy before compiling — the words matter more than the layout.
- Public outputs deserve a different visual identity than internal ones. Don't reuse the internal template.
- Surface social-impact-lens findings only if they support the pitch. If they're problematic, that's a real consideration but not for the one-pager.
