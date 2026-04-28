---
name: name-suggestions
description: Generate domain and product name suggestions for a captured idea — themed across categories (descriptive, evocative, abstract, founder-named, compound) — and check basic domain/social-handle availability. Use when the user is ready to give an idea a working name.
---

# Name & Domain Suggestions

Generate candidate names with light availability checks.

## Steps

1. Read the idea and the latest formatted summary so the suggestions are grounded.
2. Generate name candidates across categories. Aim for ~20 total spread across:
   - **Descriptive** — what it does (Stripe → it routes payments; "RouteAPI")
   - **Evocative** — metaphor / vibe (Slack, Notion)
   - **Abstract / coined** — invented words (Twilio, Yelp)
   - **Compound** — two real words (Dropbox, GitHub)
   - **Founder / proper noun** — name-after style (Hewlett-Packard)
3. For each candidate, note:
   - Pronounceability and spelling-from-hearing test
   - Any obvious negative connotations or existing-brand collisions
   - Suggested TLD options (.com first preference, then .io / .ai / .so / niche TLDs)
4. **Availability check** — for the top 5–8 candidates:
   - Run `whois <name>.com` (and `.io`, `.ai`) to check basic registration status. Don't pretend this is definitive — ICANN data has lag and resellers obscure it.
   - Optionally use WebSearch to check if a current product / company already uses the name prominently.
   - For social handles, point the user at the relevant platforms (don't try to scrape availability — too brittle).
5. Present a ranked shortlist with the user's likely top 3.

## Output

`<workspace_path>/ideas/<slug>/exports/name-suggestions-<YYYYMMDD>.md` containing the full slate, the shortlist, and availability notes.

## Notes

- Domain availability is necessary but not sufficient. Cheap aftermarket domains are often worth the cost for a strong name.
- Trademark search is **out of scope** here — the user should consult a trademark attorney before committing. Note this in the output.
- Avoid names that are racist, sexist, or align poorly with the user's stated values from `user-context.md`.
