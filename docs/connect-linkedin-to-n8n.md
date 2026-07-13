# How to Use LinkedIn in n8n with AI (via MCP) - No Community Node Needed

**Short answer:** n8n ships a built-in **MCP Client Tool** node that connects to any MCP server. Point it at LinkMCP and your n8n AI agents get 31 LinkedIn tools - profiles, people search, messaging, posts, enrichment - with no community package to install.

## Setup (built-in MCP Client Tool node)

1. Create a LinkMCP account at [app.linkmcp.io](https://app.linkmcp.io) and generate a token in **Settings → API Tokens**.
2. In your n8n AI Agent workflow, add the **MCP Client Tool** node:
   - **Connection type:** HTTP/HTTPS
   - **Server URL:** `https://app.linkmcp.io/api/mcp`
   - **Authentication:** Bearer token → paste your LinkMCP Personal Access Token
3. The agent auto-discovers all 31 LinkedIn tools and picks the right ones per task.

## Workflow ideas

- **Daily engagement digest:** every morning, pull who reacted to and commented on your posts, score against your ICP, post the shortlist to Slack.
- **CRM enrichment:** new CRM contact → look up LinkedIn profile → find + validate work email → write back.
- **Follow-up agent:** list conversations with no reply in 7 days → read each prospect's recent posts → draft a personalized follow-up for approval.

## Notes

- Works the same with **Make, Zapier and any REST client** - LinkMCP also exposes a REST API using the same token.
- Rate limits are enforced server-side (cautious mode by default) so an over-eager workflow can't endanger the connected LinkedIn account.
- Full tool reference: [app.linkmcp.io/llms-full.txt](https://app.linkmcp.io/llms-full.txt)

**See also:** [Will my LinkedIn get banned? Automation & AI safety](./will-my-linkedin-get-banned.md)
