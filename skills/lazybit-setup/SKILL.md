---
name: lazybit-setup
description: Set LazyBit up on the website in this project — add the site, put the AI agent and Translate tags into the code, verify the domain, switch the products on and check the install. Use when the user asks to install, add or set up LazyBit, its AI agent or its translation.
---

# Set up LazyBit on this website

You work through the `lazybit` MCP server; the user signs in once in the browser when you first call it.
For questions about how LazyBit works, search the `lazybit-docs` server (`search_lazybit_docs`).

1. Call `get_setup_plan` (with `site_id` when the account has several sites). Do its next step, then call it
   again. Repeat until it says the setup is complete — it always names the next tool.
2. Before you edit the site's code, read `get_sdk_docs` for `setup`, `translate` and `agent`. Mark up the pages
   as they describe: `data-i18n-ignore` for text that must not be translated, `data-agent-ignore` for what the
   agent must not touch, `data-rag-ignore` for what it must not learn, `data-lb-secret` for secrets.
3. `get_install_code` returns the tags with their keys. Put them where the guide says, show the user the change
   and **ask before deploying**.
4. Verify the domain yourself: `get_verification_steps`, put the proof into the code (the attribute on the
   script tag is usually enough), deploy, then `verify_site`. Ask the user for a DNS record only when no other
   method works. Never send them to the dashboard to verify.
5. Choose languages with `set_languages`, switch the products on with `set_translation_enabled` and
   `set_agent_enabled`, and write the agent's first instructions with `generate_agent_prompt`.
6. Finish with `check_installation` (it reads the live homepage, so deploy first) and fix what it reports.

Deleting sites or the account, keys, the own AI provider key, billing, plans and the team are done by the
owner in the dashboard; tools that hit a plan limit say what is needed. If a tool you needed was missing or a
guide was wrong, tell LazyBit with `give_feedback`.
