# Can ChatGPT Access LinkedIn? Yes - Here's How (2026)

**Short answer:** ChatGPT cannot browse LinkedIn by itself (LinkedIn blocks it), but it can use LinkedIn through an MCP connector. LinkMCP gives ChatGPT 34 LinkedIn tools through your own LinkedIn account: profile and company lookups, people search, messages, posts and comments (also as your company page), invitations, and email and phone finding.

**[Start your free 7-day trial](https://app.linkmcp.io/login?from=chatgpt&utm_source=github&utm_medium=guide&utm_content=chatgpt)** - no card. Setup takes about a minute.

## Setup

Developer mode needs ChatGPT Plus, Pro, Business, Enterprise or Edu (not Free), on the web.

1. Create a LinkMCP account at [app.linkmcp.io](https://app.linkmcp.io/login?from=chatgpt&utm_source=github&utm_medium=guide&utm_content=chatgpt-setup) (free 7-day trial, no card).
2. In ChatGPT, open **Settings > Security and login** and turn on **Developer mode**.
3. Go to [chatgpt.com/plugins](https://chatgpt.com/plugins), click **+**, name it `LinkMCP` and paste this address:
   ```
   https://app.linkmcp.io/api/mcp
   ```
4. Create the connection and approve the sign-in window.
5. In a new chat, click **+ > Developer mode** and turn on LinkMCP.
6. Test it: *"Look up the company linkedin.com/company/stripe on LinkedIn and give me a short brief: what they do, how big they are and what they posted recently."*

> **Requirements:** ChatGPT connects only to *remote* MCP servers. LinkMCP is hosted, so it works directly. A local or self-hosted server needs a bridge to expose it remotely. A workspace admin can turn Developer mode off for a Business or Enterprise workspace.

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
codex mcp add linkmcp --url https://app.linkmcp.io/api/mcp
```

Steps for Claude, Cursor and Gemini CLI are in the [README](../README.md#quick-start).

## Why not just paste LinkedIn pages into ChatGPT?

You can, but you lose search, messaging, bulk lookups, engagement data, your own analytics, and contact finding. An MCP connection makes LinkedIn a tool that ChatGPT can use in any conversation.

## Account risk

Any automated use of LinkedIn can put an account at risk, and no tool can promise that LinkedIn will not restrict an account. LinkMCP limits the risk: rate limits on every action (Cautious tier by default), a warm-up limit for connection requests on new or quiet accounts, a hard monthly usage cap on every plan, and managed sessions (no browser extension, nothing running on your machine). LinkMCP is not affiliated with LinkedIn. Details: [app.linkmcp.io/security](https://app.linkmcp.io/security)

**See also:** [Will my LinkedIn get banned? Automation risk, honestly](./will-my-linkedin-get-banned.md)
