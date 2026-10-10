# How to Connect Claude to LinkedIn (Claude Desktop, Claude Code & claude.ai)

**Short answer:** Claude can't access LinkedIn out of the box - but it can through an MCP server. LinkMCP is a hosted MCP server that gives Claude 34 LinkedIn tools (profiles, people search, messaging, posts, enrichment) through your own LinkedIn account, with managed sessions and rate limits on every action. Setup takes about 60 seconds.

**[Start your free 7-day trial](https://app.linkmcp.io/login?from=claude&utm_source=github&utm_medium=guide&utm_content=claude)** - no card. Setup takes about a minute.

## Claude Desktop / claude.ai (custom connector)

1. Create a LinkMCP account at [app.linkmcp.io](https://app.linkmcp.io) (free 7-day trial, no credit card). The guided setup detects your client and walks you through it. Connecting your own LinkedIn account needs a paid plan.
2. In Claude: **Settings → Connectors → Add custom connector** and paste:
   ```
   https://app.linkmcp.io/api/mcp?ref=github-claude
   ```
3. Complete the OAuth prompt (or paste an access key from **API Keys** in LinkMCP).
4. Ask Claude: *"Who am I on LinkedIn?"* - if it answers, you're connected.

## Claude Code (CLI)

```bash
claude mcp add --transport http linkmcp "https://app.linkmcp.io/api/mcp?ref=github-claude"
```

Then authenticate via the OAuth flow on first use, or set a PAT.

## What can Claude do on LinkedIn once connected?

- Research: *"Get the profile of <url> and summarize their last 5 posts."*
- Prospecting: *"Search VPs of Engineering at Series B companies in Berlin."*
- Warm intros: *"List the shared connections between me and <profile>."*
- Inbox: *"Show conversations with no reply in 7+ days and draft follow-ups."*
- Content: *"Who reacted to my latest post? Which ones match my ICP?"*
- Enrichment: *"Find the work email for <name> at <company>."*

Full tool catalog: [34 tools](https://app.linkmcp.io/llms.txt)

## Can this put my LinkedIn account at risk?

The **Cautious tier is the default** (daily limits and pacing on every action), new or quiet accounts start with a warm-up limit for connection requests, every plan has a hard monthly usage cap, and sessions are managed server-side over TLS, with no local browser session to maintain. As with any tool that acts on LinkedIn for you, a restriction cannot be ruled out completely; these limits keep the risk low. LinkMCP is not affiliated with LinkedIn.

## FAQ

**Does it work with Sales Navigator?** Yes - `linkedin_search_sales_navigator` uses your Sales Navigator subscription.

**Do I need my LinkedIn password in Claude?** No. You connect LinkedIn once in the LinkMCP dashboard; Claude only ever sees the MCP tools.

**What does it cost?** 7-day free trial, then paid plans sized by usage - see [pricing](https://app.linkmcp.io/#pricing).

**See also:** [Will my LinkedIn get banned? Automation risk, honestly](./will-my-linkedin-get-banned.md)
