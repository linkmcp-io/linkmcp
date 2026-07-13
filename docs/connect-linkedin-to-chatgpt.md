# Can ChatGPT Access LinkedIn? Yes - Here's How (2026)

**Short answer:** ChatGPT can't browse LinkedIn directly (LinkedIn blocks it), but it can operate your LinkedIn through an MCP connector. LinkMCP gives ChatGPT 31 LinkedIn tools - profile lookups, people search, messaging, post engagement, email/phone enrichment - through your own LinkedIn account.

## Setup

1. Create a LinkMCP account at [app.linkmcp.io](https://app.linkmcp.io) (free 7-day trial). The guided setup detects your client.
2. In ChatGPT: enable **Developer Mode** (Settings → Connectors → Advanced), then **Add custom connector** and paste:
   ```
   https://app.linkmcp.io/api/mcp
   ```
3. Authenticate via OAuth, or use a Personal Access Token from LinkMCP **Settings → API Tokens**.
4. Test: *"Look up the LinkedIn profile of <any profile URL> and summarize it."*

> **Requirements:** Developer Mode is available on ChatGPT Plus, Pro, Team, Enterprise, and Edu (not the free plan). ChatGPT only connects to *remote* MCP servers — LinkMCP is hosted, so it works directly, whereas a local/self-hosted server would need a bridge to expose it remotely.

## Example prompts that work

- *"Research these 5 companies on LinkedIn and list their heads of sales."*
- *"Who commented on this LinkedIn post? Which of them are marketing directors?"*
- *"Draft a personalized connection request for <profile url> based on their recent posts."*
- *"Find the work email for <name> at <company> and validate it."*

## Why not just paste LinkedIn pages into ChatGPT?

You can - but you lose search, messaging, bulk lookups, engagement data, your own analytics, and enrichment. An MCP connection makes LinkedIn a first-class tool ChatGPT can use in any conversation or scheduled task.

## Account safety

LinkMCP uses conservative, configurable rate limits (cautious mode by default), dedicated proxies and managed sessions - no scraping of public pages, no browser extension, nothing running on your machine. Details: [app.linkmcp.io](https://app.linkmcp.io)

**See also:** [Will my LinkedIn get banned? Automation & AI safety](./will-my-linkedin-get-banned.md)
