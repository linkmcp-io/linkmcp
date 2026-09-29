# Can ChatGPT Access LinkedIn? Yes - Here's How (2026)

**Short answer:** ChatGPT can't browse LinkedIn directly (LinkedIn blocks it), but it can operate your LinkedIn through an MCP connector. LinkMCP gives ChatGPT 33 LinkedIn tools - profile lookups, people search, messaging, post engagement, email/phone enrichment - through your own LinkedIn account.

## Setup

1. Create a LinkMCP account at [app.linkmcp.io](https://app.linkmcp.io) (free 7-day trial, no card). The guided setup detects your client. Connecting your own LinkedIn account needs a paid plan.
2. In ChatGPT, turn on **Developer mode** (Settings > Security and login). Then open the **Plugins** page, click the plus button and create a connection with this URL:
   ```
   https://app.linkmcp.io/api/mcp
   ```
3. Authenticate via OAuth, or use an access key from **API Keys** in LinkMCP.
4. Test: *"Look up the LinkedIn profile of <any profile URL> and summarize it."*

> **Requirements:** Developer mode is available on ChatGPT Plus, Pro, Business, Enterprise and Edu (not the free plan). ChatGPT only connects to *remote* MCP servers. LinkMCP is hosted, so it works directly; a local or self-hosted server would need a bridge to expose it remotely.

## Example prompts that work

- *"Research these 5 companies on LinkedIn and list their heads of sales."*
- *"Who commented on this LinkedIn post? Which of them are marketing directors?"*
- *"Draft a personalized connection request for <profile url> based on their recent posts."*
- *"Find the work email for <name> at <company> and validate it."*

## Why not just paste LinkedIn pages into ChatGPT?

You can - but you lose search, messaging, bulk lookups, engagement data, your own analytics, and enrichment. An MCP connection makes LinkedIn a first-class tool ChatGPT can use in any conversation or scheduled task.

## Account risk

Any automated use of LinkedIn can put an account at risk, and no tool can promise that LinkedIn will not restrict an account. LinkMCP limits the risk: rate limits on every action (Cautious tier by default), a warm-up limit for connection requests on new or quiet accounts, a hard monthly usage cap on every plan, and managed sessions - no browser extension, nothing running on your machine. LinkMCP is not affiliated with LinkedIn. Details: [app.linkmcp.io/security](https://app.linkmcp.io/security)

**See also:** [Will my LinkedIn get banned? Automation risk, honestly](./will-my-linkedin-get-banned.md)
