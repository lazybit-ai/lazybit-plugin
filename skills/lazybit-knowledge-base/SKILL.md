---
name: lazybit-knowledge-base
description: Improve what the LazyBit AI agent knows — find what visitors ask that it cannot answer, add or fix knowledge base documents, approve or reject learned pages, keep pages out. Use when the user asks why the agent did not know something, wants to add information to it, or wants to review what it learned.
---

# Improve the LazyBit agent's knowledge

1. See what visitors ask: `get_stats` with `kind` `insights` (topics, with a `period`) and `knowledge_base`. Topics where answers
   went unresolved are the gaps. Conversations themselves stay in the dashboard — you see topics and counts.
2. See what the agent knows: `list_kb` with `kind` `pages` (pages it learned from the site) or `documents`
   (documents added by hand); `read_kb` for one.
3. Close a gap the best way:
   - the answer belongs on the website → propose the page change in this project; after the deploy,
     `learn_pages` (the changed `paths`, or `all: true`) makes the agent read the site again;
   - it is internal or not on the site → `kb_document` (`action` `add`) with a clear title and the facts, written as plain
     statements the agent can quote;
   - a document is wrong or outdated → `kb_document` (`action` `update`) with the corrected text.
4. Review learning: `list_kb` with `kind` `pending`, then `review_new_page` for new pages and
   `review_page_update` for changed pages (`decision` `approve` or `reject`). `excluded_pages` (`action` `add`)
   keeps a URL pattern out for good (`list_kb` `excluded`; `action` `remove` lets it back in).
5. A learned page shows the site's header, footer or a live counter instead of its content, or keeps coming back
   as changed? Fix the markup in this project (`get_sdk_docs` `agent`, "Prepare the pages"): menus in `<nav>`,
   content in `<main>`, `data-kb-ignore` on the rest of the shell; after the deploy, `learn_pages` with those pages.

Show the user every document before you add it, and never put personal data, keys or passwords into one.
