# Can ChatGPT Access LinkedIn? Yes - Here's How (2026)

**Short answer:** ChatGPT cannot browse LinkedIn by itself (LinkedIn blocks it), but it can use LinkedIn through an MCP connector. LinkMCP gives ChatGPT 35 LinkedIn tools through your own LinkedIn account: profile and company lookups, people search, messages, posts and comments (also as your company page), invitations, and email and phone finding.

**[Start your free 7-day trial](https://app.linkmcp.io/login?from=chatgpt&utm_source=github&utm_medium=guide&utm_content=chatgpt)** - no card. Setup takes about a minute.

## Setup

Add LinkMCP in ChatGPT on the web, in **Plugins**. We saw **Add custom MCP server** on ChatGPT Plus (2026-10-21); OpenAI's help page also names Business and Enterprise/Edu.

1. Create a LinkMCP account at [app.linkmcp.io](https://app.linkmcp.io/login?from=chatgpt&utm_source=github&utm_medium=guide&utm_content=chatgpt-setup) (free 7-day trial, no card).
2. In ChatGPT on the web, open [chatgpt.com/plugins](https://chatgpt.com/plugins), click **Add** and choose **Add custom MCP server**.
3. Name it `LinkMCP`, choose **Server URL** and paste the LinkMCP server URL:
   ```
   https://app.linkmcp.io/api/mcp?ref=github-chatgpt
   ```
4. Leave Authentication on **OAuth**, tick **I understand and want to continue**, click **Create** and sign in to LinkMCP in the window that opens.
5. In a chat, type **@** and choose LinkMCP.
6. Test it: *"Look up the company linkedin.com/company/stripe on LinkedIn and give me a short brief: what they do, how big they are and what they posted recently."*

> **Requirements:** ChatGPT connects to an MCP server by its URL. LinkMCP is hosted, so it works directly. A local or self-hosted server must first be reachable from the internet. On a Business workspace, only admins and owners can add a custom MCP server; on Enterprise and Edu, admins decide who can.

## What works in the free trial

Profile and company lookups, the posts and comments of people and companies, and email and phone finding work at once. To act as yourself on LinkedIn (people search, inbox, invitations, posting, company pages), subscribe and connect your LinkedIn account once in the LinkMCP web app.

## Example prompts that work

- *"Research these 5 companies on LinkedIn and list their heads of sales."*
- *"Who commented on this LinkedIn post? Which of them are marketing directors?"*
- *"Draft a personalized connection request for <profile URL> based on their recent posts."*
- *"Find the work email for <name> at <company> and validate it."*
- *"List the company pages that I administer and draft a post for our page. Publish it only after I say OK."*

## Using Codex instead?

Run this in your terminal. Codex opens the sign-in window.

```bash
codex mcp add linkmcp --url "https://app.linkmcp.io/api/mcp?ref=github-chatgpt"
```

Steps for Claude, Cursor and Gemini CLI are in the [README](../README.md#quick-start).

## Why not just paste LinkedIn pages into ChatGPT?

You can, but you lose search, messaging, bulk lookups, engagement data, your own analytics, and contact finding. An MCP connection makes LinkedIn a tool that ChatGPT can use in any conversation.

## Account risk

Every action has rate limits (Cautious tier by default), new or quiet accounts start with a warm-up limit for connection requests, every plan has a hard monthly usage cap, and sessions are managed (no browser extension, nothing running on your machine). As with any tool that acts on LinkedIn for you, a restriction cannot be ruled out completely; these limits keep the risk low. LinkMCP is not affiliated with LinkedIn. Details: [app.linkmcp.io/security](https://app.linkmcp.io/security)

**See also:** [Will my LinkedIn get banned? Automation risk, honestly](./will-my-linkedin-get-banned.md)
