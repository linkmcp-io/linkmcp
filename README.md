# LinkMCP - the LinkedIn layer for AI agents

**Give any AI agent full access to LinkedIn.** 31 MCP tools to search, read, message, and enrich LinkedIn - build on the API, or connect Claude, ChatGPT, Cursor, n8n, and Make in minutes.

🔗 **Website:** [app.linkmcp.io](https://app.linkmcp.io) · **Full docs for LLMs:** [llms.txt](https://app.linkmcp.io/llms.txt) / [llms-full.txt](https://app.linkmcp.io/llms-full.txt)

> This is the public documentation & configuration repo for the hosted LinkMCP service. The server itself is a managed remote MCP server — nothing to install or run locally.

## Quick start

1. Sign up at [app.linkmcp.io](https://app.linkmcp.io) (free 7-day trial, no credit card).
2. Follow the guided setup — it detects your AI client and walks you through connection.
3. Ask your AI something like: *“Research the VP of Sales at Acme Corp. Check their recent posts. Draft a connection request.”*

### Remote MCP endpoint

```
https://app.linkmcp.io/api/mcp
```

Transport: Streamable HTTP. Auth: OAuth (browser flow) or Personal Access Token (`Authorization: Bearer <token>`), generated in **Settings → API Tokens**.

### Claude Code

```bash
claude mcp add --transport http linkmcp https://app.linkmcp.io/api/mcp
```

### Claude Desktop / Cursor / Windsurf

Add a custom connector / MCP server with URL `https://app.linkmcp.io/api/mcp` — the OAuth flow takes care of the rest.

### n8n / Make / Zapier

Use the native MCP node/app in each tool, pointed at the endpoint above with a Personal Access Token (`Authorization: Bearer <token>`). Step-by-step: [n8n guide](docs/connect-linkedin-to-n8n.md) - [Make.com guide](docs/connect-linkedin-to-make.md).


## Guides

- [Connect Claude to LinkedIn (Desktop, Code, claude.ai)](docs/connect-linkedin-to-claude.md)
- [Connect ChatGPT to LinkedIn](docs/connect-linkedin-to-chatgpt.md)
- [Connect n8n to LinkedIn (via MCP)](docs/connect-linkedin-to-n8n.md)
- [Connect Make.com to LinkedIn (via MCP)](docs/connect-linkedin-to-make.md)
- [The LinkedIn outbound funnel, automated (Make & n8n)](docs/linkedin-outbound-funnel-recipe.md)
- [LinkMCP vs Expandi & PhantomBuster](docs/linkedin-mcp-vs-expandi-phantombuster.md)
- [LinkMCP vs alternatives](docs/linkmcp-vs-alternatives.md)
- [Will my LinkedIn get banned?](docs/will-my-linkedin-get-banned.md)
- [Can ChatGPT access LinkedIn? Setup guide](docs/connect-linkedin-to-chatgpt.md)
- [LinkedIn in n8n via the built-in MCP Client Tool](docs/connect-linkedin-to-n8n.md)
- [LinkedIn MCP servers compared (incl. open-source)](docs/linkmcp-vs-alternatives.md)
- [Will my LinkedIn get banned? Automation & AI safety](docs/will-my-linkedin-get-banned.md)
- [LinkedIn MCP vs Expandi, PhantomBuster & Dripify](docs/linkedin-mcp-vs-expandi-phantombuster.md)

## The 31 tools

| Category | Tools |
|---|---|
| **Profiles & companies** | `linkedin_get_profile`, `linkedin_get_company`, `linkedin_bulk_get_profiles`, `linkedin_bulk_get_companies` |
| **Posts & engagement** | `linkedin_get_person_posts`, `linkedin_get_company_posts`, `linkedin_get_post_comments`, `linkedin_get_nested_comments`, `linkedin_get_post_reactions` |
| **Messaging** | `linkedin_list_conversations`, `linkedin_get_conversation_messages`, `linkedin_send_message` (incl. InMail) |
| **Connections** | `linkedin_get_connections`, `linkedin_get_shared_connections`, `linkedin_list_connection_requests`, `linkedin_manage_connection_request`, `linkedin_send_connection_request` |
| **Search** | `linkedin_search_people`, `linkedin_search_sales_navigator` |
| **Content creation** | `linkedin_create_post`, `linkedin_comment_on_post`, `linkedin_react_to_post` |
| **Your LinkedIn** | `linkedin_who_am_i`, `linkedin_get_post_analytics`, `linkedin_get_profile_views`, `linkedin_get_my_engagement`, `linkedin_get_my_saved_items` |
| **Enrichment** | `find_email`, `validate_email`, `find_mobile` |
| **Utility** | `send_feedback` |

Full parameter documentation: [llms-full.txt](https://app.linkmcp.io/llms-full.txt)


## Track record

Since March 2026: **90+ LinkedIn account connections, 7,700+ automatic rate-limit interventions protecting those accounts, and zero user-reported LinkedIn restrictions.** Safety isn't a tagline here - it's enforced server-side on every call.

## Account safety

- **Cautious mode by default** — rate limits well within LinkedIn thresholds, adjustable per plan
- **Managed sessions** — dedicated proxies, TLS everywhere, no local browser or cookies to maintain
- **No bulk scraping, no mass exports** — your session behaves like normal LinkedIn browsing
- **No training on your data, no selling** — pass-through only

## Pricing

Free 7-day trial, then paid plans sized by monthly usage. Current pricing: [app.linkmcp.io → Pricing](https://app.linkmcp.io/#pricing)

## Example use cases

- **Sales prospecting:** “Search VPs of Engineering at these 10 companies. Find warm intro paths.”
- **Engagement mining:** “Who reacted to this post? Which are marketing directors at Series A–C? Draft requests for top 10.”
- **Inbox management:** “Conversations with no reply in 7+ days. Check their posts. Draft follow-ups.”
- **Recruiting:** “Find senior engineers at Series B startups in Berlin who posted in the last month.”

## Support

- In-app feedback tool (`send_feedback`) or [GitHub issues](https://github.com/linkmcp-io/linkmcp/issues) for docs/config problems
- Email: ceo@linkmcp.io

---
© Third Person Systems LLC. LinkMCP is not affiliated with or endorsed by LinkedIn.
