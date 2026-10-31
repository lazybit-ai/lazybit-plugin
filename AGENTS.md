# LazyBit

LazyBit adds two products to a website, one script tag each: the **AI agent** (a chat assistant that answers
visitors from the site's own pages and documents and, with the visitor's permission, acts on the page) and
**Translate** (the whole site in its visitors' languages).

This plugin connects your agent to two MCP servers:

- `lazybit` — the user's LazyBit account. Tools act as the user, on their own sites only. The user signs in
  once in the browser (`/mcp` in Claude Code, or your client's equivalent). Start with `get_setup_plan`.
- `lazybit-docs` — LazyBit's public guides and plans, no sign-in: `search_lazybit_docs`, `get_lazybit_guide`,
  `list_lazybit_plans`.

Rules that matter:

- Ask the user before deploying, and show them every change to their code.
- Verifying the domain is your job (`get_verification_steps` → code → deploy → `verify_site`).
- Read a setting before changing it, change only what was asked, and say what changed; `get_recent_changes`
  has the old values for an undo.
- Never: deleting sites or the account, keys, the own AI provider key, billing, plans, the team — the owner
  does those in the dashboard.
- Something missing or unclear? `give_feedback`.

Load the skill that matches the task: `lazybit-setup`, `lazybit-configure`, `lazybit-knowledge-base`,
`lazybit-report`, `lazybit-translate`.
