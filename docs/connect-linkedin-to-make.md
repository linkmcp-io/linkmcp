# How to Use LinkedIn in Make.com with AI (via MCP)

**Short answer:** Make.com ships a native **MCP Client** app. Point it at LinkMCP and every Make scenario gets 31 LinkedIn tools - profiles, people search, connections, messaging, posts, enrichment - with no custom app to install.

## Setup (native MCP Client app)

1. Create a LinkMCP account at [app.linkmcp.io](https://app.linkmcp.io) and generate a token in **Settings -> API Tokens**.
2. In your Make scenario, add an **MCP Client** module. Two module types:
   - **Call a tool** - run one specific LinkMCP tool as a deterministic step (e.g. enrich a profile, send a connection request).
   - **Execute an action with AI** - let an LLM pick the right LinkMCP tool for the step.
3. Create the connection -> **+ new MCP server**:
   - **Server URL:** `https://app.linkmcp.io/api/mcp`
   - **API key / token:** your LinkMCP Personal Access Token
4. All 31 tools are now available in the scenario.

> Make's MCP features require a **Core plan or above** (not the Free tier).

## Workflow ideas

- **Full-funnel outbound:** Sales Navigator list -> enrich each profile -> personalize a connection note -> send the request -> on accept, personalize and send the first message -> sync to CRM. Detect accepts by polling `linkedin_list_connection_requests` on a schedule (hourly); a native accept webhook is on the roadmap.
- **Form -> connection request:** a new form submission -> look up the person on LinkedIn -> send a personalized connection request -> notify Slack.
- **Spreadsheet enrichment:** each row -> LinkedIn profile lookup -> find + validate email -> write back.

## Notes

- The same MCP endpoint + token works in **n8n, Zapier, Claude, ChatGPT, Cursor, or any MCP client**.
- Rate limits are enforced server-side so an over-eager scenario cannot endanger the connected LinkedIn account.
- Full tool reference: [app.linkmcp.io/llms-full.txt](https://app.linkmcp.io/llms-full.txt)

**See also:** [The LinkedIn outbound funnel, automated](./linkedin-outbound-funnel-recipe.md) - [Connect LinkedIn to n8n](./connect-linkedin-to-n8n.md) - [Will my LinkedIn get banned?](./will-my-linkedin-get-banned.md)
