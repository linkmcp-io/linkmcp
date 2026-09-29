# LinkMCP - hosted LinkedIn MCP server

**Connect your own LinkedIn account to Claude, ChatGPT, Cursor, Gemini CLI, n8n, Make or any MCP client.** 33 tools to research people and companies, search (including Sales Navigator with your own seat), work your LinkedIn inbox, read and write posts and comments, manage connection requests, and find work emails and mobile numbers.

**Website:** [app.linkmcp.io](https://app.linkmcp.io/?utm_source=github&utm_medium=readme) · **Docs for LLMs:** [llms.txt](https://app.linkmcp.io/llms.txt) / [llms-full.txt](https://app.linkmcp.io/llms-full.txt) · **Guides:** [app.linkmcp.io/guides](https://app.linkmcp.io/guides)

> This is the public documentation and configuration repo for the hosted LinkMCP service. The server is a managed remote MCP server and its code is not open source. There is nothing to install or run locally.

## Quick start

1. Sign up at [app.linkmcp.io](https://app.linkmcp.io/?utm_source=github&utm_medium=readme). The 7-day trial is free and needs no card.
2. Connect your LinkedIn account once in the web app (this needs a paid plan).
3. Add the server to your AI client (see below) and ask, for example: *"Research the VP of Sales at Acme Corp. Check their recent posts. Draft a connection request."*

### Remote MCP endpoint

```
https://app.linkmcp.io/api/mcp
```

Transport: Streamable HTTP. Auth: OAuth (browser sign-in, dynamic client registration) or an access key as `Authorization: Bearer <key>` (create it in the web app under **API Keys**).

### Claude (web, desktop)

In Claude, open Customize > Connectors and click "Add custom connector". Paste `https://app.linkmcp.io/api/mcp` and click "Add". On Team and Enterprise plans, an Owner adds it for the organization in Organization settings > Connectors; then each member clicks "Connect" under Customize > Connectors. Guide: [How to connect Claude to LinkedIn](https://app.linkmcp.io/guides/how-to-connect-claude-to-linkedin).

### Claude Code

```bash
claude mcp add --transport http linkmcp https://app.linkmcp.io/api/mcp
```

### ChatGPT

Turn on Developer mode in ChatGPT (Settings > Security and login). Then open the Plugins page, click the plus button and create a connection with the URL above. Guide: [Can ChatGPT read LinkedIn profiles?](https://app.linkmcp.io/guides/can-chatgpt-read-linkedin-profiles)

### Cursor, Gemini CLI and other MCP clients

Add a remote MCP server with URL `https://app.linkmcp.io/api/mcp`. The OAuth sign-in does the rest. If your client does not support OAuth, use an access key as a Bearer token.

### n8n, Make, Zapier

Use the MCP client node or module of the platform, with the endpoint above and an access key. Step by step: [n8n guide](https://app.linkmcp.io/guides/how-to-connect-linkedin-to-n8n), [Make guide](docs/connect-linkedin-to-make.md).

## The 33 tools

| Category | Tools |
|---|---|
| **Profiles and companies** | `linkedin_get_profile`, `linkedin_get_company`, `linkedin_bulk_get_profiles`, `linkedin_bulk_get_companies` |
| **Search** | `linkedin_search_people`, `linkedin_search_sales_navigator`, `linkedin_search_jobs` |
| **Posts and engagement** | `linkedin_get_person_posts`, `linkedin_get_company_posts`, `linkedin_get_post_comments`, `linkedin_get_nested_comments`, `linkedin_get_post_reactions` |
| **Messaging** | `linkedin_list_conversations`, `linkedin_get_conversation_messages`, `linkedin_send_message` (incl. InMail), `linkedin_mark_conversation_read` |
| **Connections** | `linkedin_get_connections`, `linkedin_get_shared_connections`, `linkedin_list_connection_requests`, `linkedin_manage_connection_request`, `linkedin_send_connection_request` |
| **Content** | `linkedin_create_post`, `linkedin_comment_on_post`, `linkedin_react_to_post` |
| **Your LinkedIn** | `linkedin_who_am_i`, `linkedin_get_post_analytics`, `linkedin_get_profile_views`, `linkedin_get_my_engagement`, `linkedin_get_my_saved_items` |
| **Contact enrichment** | `find_email`, `validate_email`, `find_mobile` |
| **Utility** | `send_feedback` |

25 tools only read. 8 tools write (send a message, send or manage a connection request, create a post, comment, react, mark a conversation as read, send feedback). Every tool has a title and read-only or write annotations. Full parameter documentation: [llms-full.txt](https://app.linkmcp.io/llms-full.txt).

## Pricing

- **Free trial:** 7 days, no card. Profile and company lookups, post data and email or phone finding work in the trial. Connecting your own LinkedIn account (inbox, search as you, invites, posting) needs a paid plan.
- **Starter:** $19 per month. **Pro:** $49 per month (5x the Starter usage). **Max:** $199 per month (50x the Starter usage).
- Every paid plan includes every tool. Each plan has a monthly usage allowance and a hard cap, so a looping agent cannot run up a bill. Top-up packs cost $10.

Current prices: [app.linkmcp.io/#pricing](https://app.linkmcp.io/#pricing)

## Account risk and limits

Any automated use of LinkedIn can put an account at risk, and no tool can promise that LinkedIn will not restrict an account. LinkMCP limits the risk:

- Server-side rate limits on every call, and a warm-up ramp for connection requests on new or quiet accounts.
- Your LinkedIn password is not stored. The LinkedIn session runs on dedicated session infrastructure, not in your browser.
- No bulk scraping and no mass exports. No training on your data.
- Read [Will my LinkedIn get banned?](https://app.linkmcp.io/guides/will-my-linkedin-get-banned) before you automate at volume.

## Example prompts

- **Research before outreach:** "Search VPs of Engineering at these 10 companies. Find shared connections for a warm intro."
- **Inbox:** "List conversations with no reply in 7+ days. Check what each person posted recently. Draft follow-ups."
- **Engagement:** "Who reacted to my last post? Which of them are marketing directors? Draft connection notes for the top 10."
- **Recruiting:** "Find senior engineers at Series B startups in Berlin who posted in the last month."

## Support

- In-app `send_feedback` tool, or [GitHub issues](https://github.com/linkmcp-io/linkmcp/issues) for docs and config problems.
- Email: info@linkmcp.io

---
© Third Person Systems LLC. LinkMCP is independent. It is not affiliated with, endorsed by, or built on an official API of LinkedIn.
