# The LinkedIn Outbound Funnel, Fully Automated (Make & n8n)

Run a Sales Navigator search, connect, and follow up with a personalized message the moment each prospect accepts - the whole outbound motion as one automation, driven by AI. No dedicated node to install: LinkMCP's 31 LinkedIn tools plug straight into the **native MCP node** in both [n8n](./connect-linkedin-to-n8n.md) and [Make.com](./connect-linkedin-to-make.md).

This is the funnel most teams stitch together from three or four separate tools. With LinkMCP it's one credential and one workflow.

## The funnel

| # | Step | LinkMCP tool |
|---|------|--------------|
| 1 | Run a Sales Navigator search for your target profile | `linkedin_search_sales_navigator` (or `linkedin_search_people`) |
| 2 | Enrich each prospect (role, headline, company, recent activity) | `linkedin_get_profile` / `linkedin_bulk_get_profiles` |
| 3 | Draft a personalized connection note (AI) | your LLM step |
| 4 | Send the connection request | `linkedin_send_connection_request` |
| 5 | Detect who accepted | `linkedin_list_connection_requests` (poll on a schedule) + `linkedin_get_connections` to confirm |
| 6 | Draft + send a personalized first message (AI) | your LLM step -> `linkedin_send_message` |
| 7 | Log the touch to your CRM | your CRM/Sheets node |

Steps 1-4 run as one pass. Steps 5-7 run on a schedule (hourly is the sweet spot - see *Detecting accepts* below).

## Build it

**n8n:** one AI Agent with the **MCP Client Tool** sub-node pointed at `https://app.linkmcp.io/api/mcp` (Bearer = your LinkMCP token). Give the agent the list source (a Google Sheet / Airtable read) and let it call the tools; or wire the tools deterministically with the standalone **MCP Client** node if you don't want an LLM deciding steps. Split the "send requests" and "check accepts + follow up" halves into two workflows (the second on a Schedule Trigger).

**Make.com:** an MCP Client connection to the same endpoint. Use **Execute an action with AI** for the personalization steps and **Call a tool** for the deterministic LinkedIn actions. Two scenarios: one over your list, one on a schedule for accepts.

Full connection setup: [n8n guide](./connect-linkedin-to-n8n.md) · [Make.com guide](./connect-linkedin-to-make.md).

## The prompts (the part that makes it work)

**Connection note (step 3).** Keep it short and human. The profile data should shape *what you say*, never announce that you researched them - context-bragging ("I saw your post about X") reads as automated in 2026. Prompt the model:

> You write one-line LinkedIn connection notes. Given this profile, write a note under 200 characters that references one concrete, relevant reason to connect - phrased as a peer, not a fan. No "I noticed", no flattery, no pitch. Output only the note.

**First message after accept (step 6).**

> Write the first LinkedIn message to a new connection. One specific, useful opener tied to their role or company, then one low-friction question. Under 400 characters, no pitch, no "thanks for connecting". Output only the message.

Add a manual-review gate before step 6 while you calibrate tone (Make: a router + approval; n8n: a Wait/Approval node).

## Detecting accepts (step 5)

LinkMCP doesn't yet push a real-time "connection accepted" webhook (it's on the roadmap). Until then, poll: on a schedule, call `linkedin_list_connection_requests` for your sent invites and diff against the previous run - anything that dropped off the pending list was accepted, declined, or withdrawn. Confirm the accepts with `linkedin_get_connections`. **Poll hourly, not faster:** the two list calls are metered per LinkedIn account (100/day, shared with your other tool usage), and true "the-instant-they-accept" timing isn't something LinkedIn exposes to anyone - hourly is fresh enough for a personalized follow-up and keeps you well inside the budget.

## Safety

Every call runs through LinkMCP's server-side rate limiting (cautious mode by default), so an over-eager schedule can't push the connected account past LinkedIn's thresholds. More: [Will my LinkedIn get banned?](./will-my-linkedin-get-banned.md)

## Get started

1. [app.linkmcp.io](https://app.linkmcp.io) - 7-day free trial, generate a token in **Settings -> API Tokens**.
2. Connect it in [n8n](./connect-linkedin-to-n8n.md) or [Make.com](./connect-linkedin-to-make.md).
3. Build the two workflows above. Full tool reference: [llms-full.txt](https://app.linkmcp.io/llms-full.txt).
