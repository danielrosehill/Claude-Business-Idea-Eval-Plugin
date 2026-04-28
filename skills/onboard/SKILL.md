---
name: onboard
description: First-run setup for the business-idea-eval plugin. Asks the user where business-idea workspaces should live on disk, captures user context (background, domains of interest, capital appetite, risk profile) used to personalise lens analyses, and writes config.json. Run once before using other skills.
---

# Onboard business-idea-eval

This plugin keeps the user's actual idea data outside the plugin install directory. On first run, capture two things:

1. **Workspace path** — where `ideas/<idea-slug>/` directories will live. Suggest `~/Documents/business-ideas/` or a dedicated git repo under `~/repos/`. Confirm with the user before writing.
2. **User context** — short prose answering: background and domain expertise; current capital availability (bootstrap / small / VC-track); risk appetite; geography (defaults to user's locale); strong preferences (e.g. "B2B SaaS only", "open to hardware"). This is loaded into every lens analysis so outputs are calibrated to the user, not generic.

## Steps

1. Resolve config root:
   ```bash
   CONFIG_DIR="${CLAUDE_USER_DATA:-${XDG_DATA_HOME:-$HOME/.local/share}/claude-plugins}/business-idea-eval"
   mkdir -p "$CONFIG_DIR"
   ```
2. If `$CONFIG_DIR/config.json` already exists, ask whether to re-run setup or edit a single field.
3. Prompt for workspace path. Default to `~/Documents/business-ideas`. Create the directory if missing.
4. Prompt for user context. Write to `$CONFIG_DIR/user-context.md` (markdown free-form).
5. Write `$CONFIG_DIR/config.json`:
   ```json
   {
     "workspace_path": "/absolute/path",
     "user_context_path": "/absolute/path/to/user-context.md",
     "council_default": "subagents"
   }
   ```
6. Print the path and confirm setup is complete.

## Notes

- `council_default` is `"subagents"` or `"karpathy"` — see council-review-* skills.
- Other skills resolve config the same way; never hardcode the workspace path.
- The `user-context.md` file is read-mostly: encourage the user to edit it directly when their situation changes.
