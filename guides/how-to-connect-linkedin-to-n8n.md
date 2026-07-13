# How to Connect LinkedIn to n8n (with an MCP Server)

**Short answer: use n8n's built-in MCP Client Tool node to connect a LinkedIn MCP server - no custom node or install required.** n8n natively speaks the Model Context Protocol, so you point its MCP Client Tool node at a LinkedIn MCP server like [LinkMCP](https://linkmcp.io), and every LinkedIn tool (read profiles, search, message, enrich) becomes available inside your workflows and AI-agent nodes. This is the simplest, most maintainable way to add LinkedIn to n8n.

## Why the MCP approach (and not a dedicated node)

You don't need a special "LinkedIn" community node. n8n's **MCP Client Tool** node connects to any MCP server and exposes its tools directly - so a single MCP connection gives you the full LinkedIn tool set, and it keeps working as the server adds tools, with nothing to install or maintain on the n8n side.

## Steps

1. **Get a LinkedIn MCP server endpoint.** With a hosted server (LinkMCP), connect your LinkedIn account once in the dashboard and copy the server URL and access token. (No browser extension or local scraper.)
2. **Add the MCP Client Tool node** in your n8n workflow.
3. **Configure the connection** with the server URL and token (as a Bearer credential).
4. **Use the tools** - attach the MCP Client Tool to an AI Agent node so the agent can call LinkedIn tools, or invoke a specific tool directly in a workflow step.

## What you can build in n8n

- **Lead enrichment pipelines** - take a list of LinkedIn URLs or a search, pull profile data, enrich with emails, write to your CRM.
- **AI-agent workflows** - an agent that researches a prospect, drafts a personalized message, and queues it.
- **Inbox automation** - triage LinkedIn messages, draft context-aware replies for approval.
- **Engagement tracking** - pull who engaged with your posts and route follow-ups.

## Account safety in automated workflows

Because n8n can run on a schedule, it's easy to accidentally push high volumes. Keep it human-scale:

- Use a managed, rate-limited MCP server rather than raw scraping.
- Add delays and daily caps in your workflow; don't blast connection requests.
- Treat any published limit as a ceiling, not a target.

See our [LinkedIn automation safety guide](./will-my-linkedin-get-banned.md) for detail.

## FAQ

**Do I need a LinkedIn community node for n8n?**
No - the built-in MCP Client Tool node connects to a LinkedIn MCP server directly, which is simpler and more complete.

**Does this work with n8n's AI Agent nodes?**
Yes - attach the MCP Client Tool to an AI Agent and it can call the LinkedIn tools as part of its reasoning.

**Self-hosted or hosted n8n?**
Either - the MCP Client Tool node works the same. You just need a reachable MCP server URL and token.

**Is it safe to run on a schedule?**
Yes, if you keep volumes reasonable and use a managed, rate-limited server. Scheduled high-volume automation is where account risk comes from.

---

*LinkMCP is a hosted LinkedIn MCP server that plugs into n8n's MCP Client Tool node - 31 LinkedIn tools, managed sessions, no install. [Start a free trial](https://linkmcp.io).*
