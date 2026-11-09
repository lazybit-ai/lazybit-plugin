---
name: lazybit-setup
description: Set LazyBit up on the website in this project — add the site, put the AI agent and Translate tags into the code, verify the domain, switch the products on, check the install and offer the user the main choices (chat look, languages, limits). Use when the user asks to install, add or set up LazyBit, its AI agent or its translation.
---

# Set up LazyBit on this website

You work through the `lazybit` MCP server; the user signs in once in the browser when you first call it.
For questions about how LazyBit works, search the `lazybit-docs` server (`search_lazybit_docs`).

0. If the user has no LazyBit account yet, call `get_started` on the `lazybit-docs` server (pass `client` = which
   assistant you are) and give the user its sign-up link. Only the user creates the account, in their browser — never
   fill in the form. Once they have signed up, continue with step 1; the sign-in to the `lazybit` server follows.

1. Call `get_setup_plan` (with `site_id` when the account has several sites). Do its next step, then call it
   again. Repeat until it says the setup is complete — it always names the next tool.
2. Before you edit the site's code, read `get_sdk_docs` for `setup`, `translate` and `agent`. Mark up the pages
   as they describe: `data-i18n-ignore` for text that must not be translated, `data-agent-ignore` for what the
   agent must not touch, `data-kb-ignore` for what it must not learn, `data-lb-secret` for secrets. Standard ARIA
   tabs need nothing; if the site's tabs are not standard ARIA tabs, mark each panel `data-lb-section="Name"` so
   each one is learned on its own.
3. `get_install_code` returns the tags for the site. Put them where the guide says, show the user the change
   and **ask before deploying**.
4. Verify the domain yourself: `get_verification_steps`, put the proof into the code (the attribute on the
   script tag is usually enough), deploy, then `verify_site`. Ask the user for a DNS record only when no other
   method works. Never send them to the dashboard to verify.
5. Choose languages with `set_languages`, switch the products on with `set_translation_enabled` and
   `set_agent_enabled`, and write the agent's first instructions with `generate_agent_prompt`.
6. Finish with `check_installation` (it reads the live homepage, so deploy first) and fix what it reports.
7. When `get_setup_plan` says the setup is complete, ask the user **once**, in one message, about the optional
   choices in its `personalise` section — the chat's look, languages, the agent's name, instructions and
   suggested prompts, and the limits — with their current values. Offer only the choices it marks `available`
   (the plan and this connection decide); apply what the user picks with the tool each choice names, and nothing
   else. The limits are starting values: say what they are and that the user may change or switch them off, but
   change them only when asked. If the user keeps the defaults, the setup is finished; do not ask again.

Deleting sites or the account, the own AI provider key, billing, plans and the team are done by the
owner in the dashboard; tools that hit a plan limit say what is needed. If a tool you needed was missing or a
guide was wrong, tell LazyBit with `give_feedback`.
