# LazyBit plugin

Set up and run [LazyBit](https://lazybit.ai) on your website from your coding agent. The plugin bundles the
LazyBit MCP servers with skills, so your agent adds the site, puts the tags into your code, verifies the
domain, switches the AI agent and Translate on — and later tunes them and reports how visitors use them.

## Install

### Claude Code

```
/plugin install lazybit --marketplace lazybit-ai/lazybit-plugin
```

On older Claude Code versions, add the marketplace first:

```
/plugin marketplace add lazybit-ai/lazybit-plugin
/plugin install lazybit@lazybit
```

### Codex

```bash
codex plugin marketplace add lazybit-ai/lazybit-plugin
codex plugin add lazybit@lazybit
```

### Cursor

Once the plugin is listed in Cursor's plugin directory:

```
/add-plugin lazybit
```

Until then, connect the two servers below in Cursor's MCP settings.

### Gemini CLI

```bash
gemini extensions install https://github.com/lazybit-ai/lazybit-plugin
```

### Any other MCP client

```json
{
  "mcpServers": {
    "lazybit": { "url": "https://dashboard.lazybit.ai/mcp" },
    "lazybit-docs": { "url": "https://lazybit.ai/docs/mcp" }
  }
}
```

Then copy `skills/` to where your client reads skills from.

## Sign in

The first call to the `lazybit` server opens a LazyBit page in your browser: sign in and click **Allow**.
Owners and admins of a LazyBit account can connect. The `lazybit-docs` server needs no sign-in.

## Skills

| Skill | Ask for example |
|---|---|
| `lazybit-setup` | "Set up LazyBit on this site." |
| `lazybit-configure` | "Make the chat answers shorter and call the assistant Mia." |
| `lazybit-knowledge-base` | "What do visitors ask that the agent cannot answer? Fix it." |
| `lazybit-report` | "How did the LazyBit agent do this month?" |
| `lazybit-translate` | "Add German and Polish, and never translate our product names." |

## What it cannot do

Deleting a site or the account, your own AI provider key, billing and plans, and the team stay in
the LazyBit dashboard. Every change your agent makes is listed there under **Activity**.

Docs: [Connect your AI](https://lazybit.ai/connect-ai) · Support: support@lazybit.ai

The plugin (this repository: manifests and skills) is MIT-licensed. The LazyBit service it connects to is not open source.
