---
name: lazybit-report
description: Write a short report on how LazyBit is used on the user's sites — conversations, topics visitors ask about, knowledge base, translation and credits for a period. Use when the user asks how the agent is doing, for usage, credits or a weekly or monthly summary.
---

# Report on LazyBit usage

1. `get_account` for the plan and sites, `get_usage` for credits used and left.
2. Per site and period: `get_agent_metrics` (conversations, resolved share), `get_insights` (top topics) and
   `get_kb_stats` (what the knowledge base answered and missed).
3. `get_recent_changes` for what was changed in the period, by people or assistants.
4. Write it short: the numbers that moved, the three topics asked most, the gaps (topics left unresolved), what
   to do next — for gaps, offer the `lazybit-knowledge-base` skill. If the plan's credits run low, say when, and
   that the owner changes the plan in the dashboard.
