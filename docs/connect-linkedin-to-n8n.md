# How to Use LinkedIn in n8n with AI (via MCP) - No Community Node Needed

**Short answer:** n8n ships built-in MCP nodes that connect to any MCP server. Point them at LinkMCP and your n8n workflows get 34 LinkedIn tools - profiles, people search, connections, messaging, posts, enrichment - with no community package to install and nothing to self-host.

**[Start your free 7-day trial](https://app.linkmcp.io/login?from=n8n&utm_source=github&utm_medium=guide&utm_content=n8n)** - no card. Setup takes about a minute.

## Two ways to use it

n8n has two native nodes, and LinkMCP works with both:

- **MCP Client Tool** (attach to an AI Agent): the agent auto-discovers all 34 tools and picks the right one per task. Best for "research this lead and draft a message" style automations.
- **MCP Client** (standalone step, no LLM required): call one specific LinkMCP tool as a deterministic workflow step. Best for classic operator flows - "enrich this profile", "send this connection request" - where you don't want an agent deciding anything.

## Setup

1. Create a LinkMCP account at [app.linkmcp.io](https://app.linkmcp.io) and create an access key under **API Keys**.
2. Add the **MCP Client Tool** (under an AI Agent) or the standalone **MCP Client** node:
   - **Endpoint / Server URL:** `https://app.linkmcp.io/api/mcp`
   - **Authentication:** Bearer token -> paste your LinkMCP Personal Access Token
   - **Transport:** Streamable HTTP
3. On the Tool node you can include all 34 tools or curate a subset (e.g. only search + connect + message for an outreach agent).

> **If the connection fails:** make sure n8n is using **Streamable HTTP** transport, not the legacy SSE transport - LinkMCP is Streamable-HTTP only. In some n8n versions the transport can fall back to SSE silently; set it explicitly to HTTP Streamable.

## Workflow ideas

- **Full-funnel outbound (search to sent, one workflow):** pull a Sales Navigator list -> enrich each profile -> draft a personalized connection note -> send the request -> when it is accepted, draft and send a personalized first message -> log to your CRM. No manual steps in between.
- **Daily engagement digest:** every morning, pull who reacted to and commented on your posts, score against your ICP, post the shortlist to Slack.
- **CRM enrichment:** new CRM contact -> look up LinkedIn profile -> find + validate work email -> write back.
- **Follow-up agent:** list conversations with no reply in 7 days -> read each prospect's recent posts -> draft a personalized follow-up for approval.

## Notes

- **Make, Zapier, or any tool with an MCP client** connect the same way - point their MCP node at `https://app.linkmcp.io/api/mcp` with your token. LinkMCP is an MCP server; the LinkedIn tools are exposed over MCP, not as a per-endpoint REST API.
- Rate limits are enforced server-side (Cautious tier by default), so an over-eager workflow is slowed down or stopped. Any automated use of LinkedIn can still put the connected account at risk.
- Full tool reference: [app.linkmcp.io/llms-full.txt](https://app.linkmcp.io/llms-full.txt)

**See also:** [The LinkedIn outbound funnel, automated](./linkedin-outbound-funnel-recipe.md) - [Connect LinkedIn to Make.com](./connect-linkedin-to-make.md) - [Will my LinkedIn get banned?](./will-my-linkedin-get-banned.md)
