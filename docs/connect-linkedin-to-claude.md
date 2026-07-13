# How to Connect Claude to LinkedIn (Claude Desktop, Claude Code & claude.ai)

**Short answer:** Claude can't access LinkedIn out of the box - but it can through an MCP server. LinkMCP is a hosted MCP server that gives Claude 31 LinkedIn tools (profiles, people search, messaging, posts, enrichment) through your own LinkedIn account, with managed sessions and account-safe rate limits. Setup takes about 60 seconds.

## Claude Desktop / claude.ai (custom connector)

1. Create a LinkMCP account at [app.linkmcp.io](https://app.linkmcp.io) (free 7-day trial, no credit card). The guided setup detects your client and walks you through it.
2. In Claude: **Settings → Connectors → Add custom connector** and paste:
   ```
   https://app.linkmcp.io/api/mcp
   ```
3. Complete the OAuth prompt (or paste a Personal Access Token from **Settings → API Tokens** in LinkMCP).
4. Ask Claude: *"Who am I on LinkedIn?"* - if it answers, you're connected.

## Claude Code (CLI)

```bash
claude mcp add --transport http linkmcp https://app.linkmcp.io/api/mcp
```

Then authenticate via the OAuth flow on first use, or set a PAT.

## What can Claude do on LinkedIn once connected?

- Research: *"Get the profile of <url> and summarize their last 5 posts."*
- Prospecting: *"Search VPs of Engineering at Series B companies in Berlin."*
- Warm intros: *"List the shared connections between me and <profile>."*
- Inbox: *"Show conversations with no reply in 7+ days and draft follow-ups."*
- Content: *"Who reacted to my latest post? Which ones match my ICP?"*
- Enrichment: *"Find the work email for <name> at <company>."*

Full tool catalog: [31 tools](https://app.linkmcp.io/llms.txt)

## Is this safe for my LinkedIn account?

LinkMCP runs **cautious mode by default**: rate limits well inside LinkedIn's thresholds, dedicated proxies, managed TLS sessions, no local browser session to maintain, no bulk scraping. Your account behaves like normal LinkedIn browsing.

## FAQ

**Does it work with Sales Navigator?** Yes - `linkedin_search_sales_navigator` uses your Sales Navigator subscription.

**Do I need my LinkedIn password in Claude?** No. You connect LinkedIn once in the LinkMCP dashboard; Claude only ever sees the MCP tools.

**What does it cost?** 7-day free trial, then paid plans sized by usage - see [pricing](https://app.linkmcp.io/#pricing).

**See also:** [Will my LinkedIn get banned? Automation & AI safety](./will-my-linkedin-get-banned.md)
