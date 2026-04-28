---
name: dev-spec
description: Translate a captured idea into a development specification — system architecture sketch, key components, data model outline, third-party dependencies, build phases to MVP, and identified hard problems. Software-focused; for hardware see hardware-feasibility. Use when the user wants to estimate "what would I actually need to build".
---

# Development Spec

A first-pass spec a developer could review and challenge — not a final design.

## Steps

1. Read the idea + any prior lens outputs.
2. Outline:
   - **System architecture** — high-level boxes-and-arrows description in prose; client / server / data / integrations
   - **Key components** — each with one-paragraph responsibility statement
   - **Data model** — main entities, relationships, key fields (don't go to schema-level)
   - **Third-party dependencies** — APIs, services, models, libraries the build assumes (auth, payments, AI, email, etc.)
   - **Hard problems** — the parts that are not boilerplate; ranked by uncertainty
   - **Out-of-scope for v1** — explicitly listed
3. Define **build phases** to first usable version:
   - Phase 1: thinnest credible MVP (one user, one happy path)
   - Phase 2: enough features to put in front of paying users
   - Phase 3: scale and polish
   For each phase, list deliverables and rough effort (developer-weeks).
4. Note **technology choices** the user should make explicitly (language/framework, hosting, AI model strategy, mobile native vs. web). Don't pick for them — surface the trade-offs.

## Output

`<workspace_path>/ideas/<slug>/analysis/dev-spec.md` with frontmatter:

```markdown
---
lens: dev-spec
generated: YYYY-MM-DD
mvp_effort_dev_weeks: <number>
---
```

## Notes

- This is a sketch, not a contract. The goal is making the build cost visible enough to inform go/no-go.
- If the idea is hardware-primary, defer most of this to `hardware-feasibility` and only spec the companion software layer.
