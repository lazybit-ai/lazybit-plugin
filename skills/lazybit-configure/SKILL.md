---
name: lazybit-configure
description: Change how the LazyBit AI agent behaves and looks on a site — its instructions, the chat widget, its limits, the support button. Use when the user asks to change the agent's tone, name, instructions, chat colours or button, limits, or to undo a LazyBit change.
---

# Change the LazyBit agent's settings

1. Read before you write: `get_settings` with `area` `agent`, `widget` or `limits` for the site
   (`site_id` from `get_account` when there are several).
2. Change only what the user asked for: `update_settings` with `area` `agent` (instructions, short answers,
   learning new pages, auto-approving page updates, …) or `widget` (name, placeholder, chat button, support
   email or link, branding), `update_agent_limits`. A setting the plan does not include is refused with what is
   needed — tell the user, do not work around it.
3. Tell the user what changed. `get_recent_changes` lists every change with its old value; to undo one, set the
   old value back with the same tool.

Instructions are the agent's voice on the user's site: keep the user's own wording, and do not add claims
about prices, policies or guarantees the user did not give you.
