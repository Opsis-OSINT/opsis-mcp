# Opsis MCP Server

**OSINT search for Claude, ChatGPT and any AI agent.** Give your assistant email, username and domain search across 1,000+ sources. It finds the accounts behind an identifier, reads the profiles, and follows the leads.

- **Hosted:** `https://api.useopsis.com/mcp` (Streamable HTTP). Nothing to install.
- **Sign in with your Opsis account** (OAuth). No keys to copy.
- **3 free searches** on every account, no card.
- **Verified results:** an account only counts when the site returns real profile evidence. Our last run of 1,000+ modules had zero false positives against known fake accounts.

[Product page](https://useopsis.com/products/osint-mcp) · [API docs](https://useopsis.com/docs/api) · [Create a free account](https://useopsis.com/sign-up)

## Connect

### Claude (web, desktop and mobile)
Settings → **Connectors** → **Add custom connector**, paste the URL below, then sign in to Opsis.

```
https://api.useopsis.com/mcp
```

### ChatGPT
In ChatGPT's connector settings, turn on **developer mode**, create a connector with the URL above, choose **OAuth** and sign in to Opsis. Needs a paid ChatGPT plan.

### Claude Code
```sh
claude mcp add --transport http opsis https://api.useopsis.com/mcp
```
Then run `/mcp` in Claude Code and sign in to Opsis.

### Cursor
`~/.cursor/mcp.json`
```json
{
  "mcpServers": {
    "opsis": { "url": "https://api.useopsis.com/mcp" }
  }
}
```

### VS Code (Copilot agent mode)
`.vscode/mcp.json`
```json
{
  "servers": {
    "opsis": { "type": "http", "url": "https://api.useopsis.com/mcp" }
  }
}
```

### Any other MCP client
Point it at `https://api.useopsis.com/mcp`. Clients that can't sign in by OAuth can send an API key instead, with the header `Authorization: Bearer YOUR_OPSIS_KEY`. Create a key at [useopsis.com/account/api-keys](https://useopsis.com/account/api-keys).

## Tools

| Tool | What it does | Cost |
|---|---|---|
| `search_email` | Find the accounts registered to an email address, with names, photos, bios, locations, stats and linked accounts | 1 credit |
| `search_username` | Find accounts that use a username across 1,000+ sites. `premium` adds solver-protected sources | 1 credit (premium 2) |
| `search_domain` | WHOIS, ownership history, other domains by the same owner, and archived snapshots | 1 credit |
| `get_search` | Read a search that was still running | Free |
| `list_searches` | Your recent searches | Free |
| `account` | Plan, free searches left and API credits | Free |

A full search checks 1,000+ sources live and takes 60 to 110 seconds. Search tools return what is ready after about 45 seconds plus a `run_id`, and `get_search` returns the rest, so nothing is lost to client timeouts.

## Example prompts

- "Who is behind jason.draper@example.com? Check which sites the address is registered on."
- "Search the username jdraper01 and summarize the profiles that look like the same person."
- "This phishing email came from billing@paypa1-support.com. Look up the domain and the sender."
- "List the websites and other accounts linked from the profiles you found, and search the strongest ones."

## Pricing

Every account gets 3 free standard searches through the MCP server. After that, searches use API credits on a Pro plan: top-ups start at $20 for 50 credits and reach $0.25 per credit at 1,000. Reading results, listing searches and checking your account are always free. [Plans and credits](https://useopsis.com/products/osint-api#api-access).

## Privacy and acceptable use

- **Public sources only:** public profile pages, public APIs and registration checks. No breach databases.
- **Silent:** Opsis never logs in to anyone's account and never contacts or notifies the person you search.
- **Opt-out respected:** every search goes through the Opsis opt-out list and rate limits.
- **Lawful use:** use Opsis for investigations you are authorized to carry out. It is not for employment, tenant or credit-eligibility screening. See the [terms](https://useopsis.com/terms) and [privacy policy](https://useopsis.com/privacy).

## About this repository

This repository documents the hosted Opsis MCP server and holds its [MCP Registry](https://registry.modelcontextprotocol.io) entry (`server.json`, published as `com.useopsis/opsis`). The server itself runs on Opsis infrastructure. Questions or problems: [open an issue](../../issues) or email support@useopsis.com.
