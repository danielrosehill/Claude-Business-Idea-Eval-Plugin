---
name: public-pitch-deck-outline
description: Generate a slide-by-slide pitch deck outline (markdown, ready to drop into Slides / Pitch / Keynote) for a business idea. Maps existing analysis into the canonical 10–12 slide investor or partner deck structure. Use when the user wants a pitch deck draft from their analysis materials.
---

# Public Pitch Deck Outline

Produces a markdown outline keyed to a standard pitch-deck structure. Not a designed deck — a skeleton the user can hand to a designer or paste into a slide tool.

## Slide structure

Default 12-slide investor structure (the user can request alternative structures):

1. **Cover** — company name, one-line tagline, contact
2. **Problem** — the pain we're addressing
3. **Solution** — what we're building
4. **Why now** — structural shift / market timing
5. **Market** — TAM / SAM / SOM (from `tam-analysis.md`)
6. **Product** — what it actually does (1–3 screenshots / sketches)
7. **Business model** — how money is made
8. **Go-to-market** — how customers will find us (from `b2b-b2c-fit.md`)
9. **Traction** — what's been validated; if pre-traction, what's next
10. **Team** — the founder and any committed collaborators
11. **Competition** — competitive landscape; differentiation
12. **Ask** — capital / partnership / pilot customer being requested

## Steps

1. Read the idea, synthesis, and relevant lens outputs.
2. For each slide, generate:
   - 3–5 bullet points of content
   - A speaker-note paragraph for the user to actually say when presenting
   - Visual suggestion (chart, screenshot, table, photo) — describe, don't generate
3. Flag slides where the user has weak material (e.g. no validated traction yet) and suggest what to add before the deck is presentation-ready.
4. Optionally render the outline to PDF via `internal-pdf`'s renderer for offline review.

## Output

`<workspace_path>/ideas/<slug>/exports/pitch-deck-outline-<YYYYMMDD>.md`

## Notes

- Don't fabricate traction. If there's none, say so honestly in the slide and frame the ask accordingly.
- Speaker notes matter more than bullets. Bullets are reminders; the spoken story is the pitch.
- For non-investor audiences (partner pitches, customer-discovery decks, advisor briefings), restructure — investor decks are a poor fit for those contexts.
