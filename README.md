# Punchlist for Claude Code

A Claude Code plugin marketplace with one plugin, `punchlist`. It adds the Punchlist MCP server
(OAuth, no token to paste) and a short skill that tells Claude how to work a board.

```
integrations/claude-code/
  .claude-plugin/marketplace.json        the marketplace: one plugin, ./plugins/punchlist
  plugins/punchlist/
    .claude-plugin/plugin.json           the plugin manifest
    .mcp.json                            the server: https://pkytkidrvgydqsdnoabw.supabase.co/functions/v1/punchlist-mcp
    skills/punchlist/SKILL.md            the slim skill
```

## Publishing (the owner's step)

This folder lives in the private app repo so it is reviewed and tested with the app
(`src/lib/claudePlugin.test.ts` checks the manifests and that the server URL is the app's own).
A marketplace has to be readable by the people who install it, so to publish:

1. Create a public GitHub repository, for example `punchlist-claude`.
2. Copy this folder's contents to its root (so `.claude-plugin/marketplace.json` is at the top).
3. People then run, in Claude Code:

```
/plugin marketplace add <owner>/punchlist-claude
/plugin install punchlist@punchlist
```

then `/mcp`, pick `punchlist`, Authenticate, and allow it on punchlistio.com.

Check it before publishing with `claude plugin validate --strict integrations/claude-code`.
