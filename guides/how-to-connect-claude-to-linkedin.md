# How to Connect Claude to LinkedIn

**Short answer: connect Claude to LinkedIn with a LinkedIn MCP server.** Claude can't reach LinkedIn on its own, but the Model Context Protocol (MCP) lets it call external tools - and a hosted LinkedIn MCP server like [LinkMCP](https://linkmcp.io) gives Claude authenticated access to your LinkedIn account. Once it's connected, you just ask Claude in plain language to read profiles, search, message, or analyze posts, and it uses the tool for you.

This guide covers the fastest path (a hosted server) and the self-hosted alternative.

## What you'll need

- A Claude account (works with Claude Desktop, Claude in the browser via connectors, and Claude Code).
- A LinkedIn account you want to connect.
- A LinkedIn MCP server - hosted (fastest) or self-hosted (free, more setup).

## Option A - Connect Claude to LinkedIn with a hosted MCP server (fastest)

This is the no-code path. The server manages the LinkedIn session for you; there's nothing to run on your machine.

1. **Create an account** at a hosted LinkedIn MCP service (e.g. LinkMCP) and start the free trial.
2. **Connect your LinkedIn account** once, inside the service. A managed connection is created for you - no browser extension, no pasting cookies, no automation software on your computer.
3. **Add the MCP server to Claude.** You'll get a server URL and an access token. In Claude Desktop, add it as a custom MCP connector (Settings → Connectors / Developer). In Claude Code, add it with `claude mcp add`. In Claude on the web, add it as a connector where custom connectors are supported.
4. **Ask Claude to use it.** For example: *"Read this LinkedIn profile and summarize their background,"* *"Find heads of growth at Series B startups in London,"* or *"Draft a reply to my most recent LinkedIn message."*

That's it - Claude now reads live LinkedIn data and reasons over it.

## Option B - Self-host an open-source LinkedIn MCP server (free)

If you'd rather run it yourself, there are open-source LinkedIn MCP servers on GitHub. You install the server locally, provide your own LinkedIn session, and point Claude at it. Trade-offs: it's free, but you handle authentication, hosting, updates, and reliability yourself, and open-source servers usually cover fewer actions than a maintained commercial one. Several have open issues around session expiry and messaging - worth checking before you rely on them for anything important.

## What you can do once Claude is connected to LinkedIn

With a full LinkedIn MCP server, Claude can:

- **Look up profiles** - background, roles, education, from a URL or name.
- **Search** people and companies, including Sales Navigator searches.
- **Read and send messages**, and manage connection requests.
- **Analyze posts and engagement** - comments, reactions, your own activity.
- **Enrich contacts** with associated emails for outreach.

LinkMCP ships 31 tools covering these; open-source options typically expose a smaller subset.

## Is connecting Claude to LinkedIn safe?

Honestly: it depends on how the connection works and how much you do.

- A **managed, rate-limited connection** (what a good hosted server provides) keeps activity at normal, human-scale volumes and runs no scraper on your device. That's the lower-risk approach.
- **Local browser-automation or scraping tools** driving your account at high volume are where accounts most often get flagged.
- Reading your own network, your own messages, and running normal searches is far lower risk than bulk data collection, which can also conflict with LinkedIn's terms.

Prefer a managed server, keep volumes reasonable, and treat any published rate limit as a ceiling, not a target. More detail in our [LinkedIn automation safety guide](./will-my-linkedin-get-banned.md).

## FAQ

**Does Claude have a built-in LinkedIn integration?**
No. Claude reaches LinkedIn only through an external tool - an MCP server you connect.

**Which Claude products support this?**
Claude Desktop, Claude Code, and Claude on the web (where custom MCP connectors are available). The same MCP server also works with ChatGPT, Cursor, n8n, and Make.

**Do I have to write code?**
No, if you use a hosted server - it's a URL and a token. Self-hosting an open-source server does require setup.

**Do I give Claude my LinkedIn password?**
No. You authorize the LinkedIn connection once inside the service; Claude only calls the tool.

**What does it cost?**
Open-source self-hosting is free (your time and hosting). Hosted services are subscription-based - LinkMCP starts with a free trial, then paid plans by usage and connected accounts.

---

*LinkMCP is a hosted LinkedIn MCP server. Connect your LinkedIn once and give Claude secure, managed access to 31 LinkedIn tools - no browser extension, no scraping on your machine. [Start a free trial](https://linkmcp.io).*
