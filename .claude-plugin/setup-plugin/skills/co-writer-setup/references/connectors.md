# Available Connectors

Reference file for the setup skill. Present these to the user during the Tools & Infrastructure interview. Update this file when new connectors are added.

---

## How Platform Connectors Work

All Co-Writer platform connectors follow the same setup flow:

1. **Get the API key** for the service (steps below per connector)
2. **Go to app.alexmcfarland.ai/connectors** — find the connector card
3. **Enter the API key** (or credentials) and save
4. **Copy the connector URL** from the card
5. **In Cowork** → go to Connectors → Add custom connector → paste the URL
6. **Sign in** when prompted — this verifies your platform access via OAuth

That's it. Once connected, Claude can read and write to that service directly.

---

## Co-Writer System Platform Connectors

### YouTube

- **What it does:** Channel stats, video search, comments, playlist items, analytics
- **API key type:** Google Cloud API key with YouTube Data API v3 enabled
- **Setup steps:**
  1. Go to [Google Cloud Console](https://console.cloud.google.com/apis/credentials)
  2. Create a project (or use existing)
  3. Enable "YouTube Data API v3"
  4. Create an API key (Credentials → Create Credentials → API Key)
  5. Copy the key and paste it on the Connectors page
- **What to add to CLAUDE.md:**
  ```
  **YouTube** — Channel analytics and content data
  - **Channel ID:** [their channel ID — find at youtube.com/account_advanced]
  - **Connector:** Co-Writer platform (app.alexmcfarland.ai/connectors)
  ```

### Substack

- **What it does:** Post performance, email stats, subscriber growth, revenue metrics
- **API key type:** Session token (connect.sid cookie) — no official API, uses session auth
- **Setup steps:**
  1. Log into Substack in your browser
  2. Open DevTools (F12 or Cmd+Option+I)
  3. Go to Application → Cookies → substack.com
  4. Find the `connect.sid` cookie and copy its value
  5. Paste the publication URL and session token on the Connectors page
- **Note:** Session tokens expire periodically — the user will need to re-grab it when that happens. Let them know upfront.
- **What to add to CLAUDE.md:**
  ```
  **Substack** — Newsletter analytics
  - **Publication URL:** [their-newsletter].substack.com
  - **Connector:** Co-Writer platform (app.alexmcfarland.ai/connectors)
  ```

### Kit (ConvertKit)

- **What it does:** Manage subscribers, broadcasts, sequences, tags, email analytics
- **API key type:** Kit API key
- **Setup steps:**
  1. Go to [Kit Developer Settings](https://app.kit.com/settings/developer)
  2. Copy the API key (starts with `ck_`)
  3. Paste it on the Connectors page
- **What to add to CLAUDE.md:**
  ```
  **Kit (ConvertKit)** — Email marketing & subscriber management
  - **Role:** [What they use it for — sequences, broadcasts, subscriber management, etc.]
  - **Tags:** [Any key tags they use and what they mean]
  - **Connector:** Co-Writer platform (app.alexmcfarland.ai/connectors)
  ```
- **Optional guided setup:** If the user wants help organizing their Kit account, offer to help them plan:
  - Tag structure (e.g., purchase tags, segment tags, campaign tags)
  - Sequence strategy (welcome, nurture, sales)
  - Subscriber segmentation approach

### Zulip

- **What it does:** Send/read messages, channels, topics, community moderation
- **API key type:** Zulip bot API key (server URL + email + API key)
- **Setup steps:**
  1. Go to your Zulip organization settings
  2. Go to [API Keys page](https://zulip.com/api/api-keys) (or Settings → Your bots → Add a new bot)
  3. Create a bot or use your personal API key
  4. Copy the server URL, email, and API key
  5. Enter all three on the Connectors page
- **What to add to CLAUDE.md:**
  ```
  **Zulip** — Community messaging
  - **Server:** [their-org].zulipchat.com
  - **Connector:** Co-Writer platform (app.alexmcfarland.ai/connectors)
  ```

### Perplexity

- **What it does:** Web search, deep research reports, citation-backed answers
- **API key type:** Perplexity API key
- **Setup steps:**
  1. Go to [Perplexity API Settings](https://perplexity.ai/settings/api)
  2. Generate or copy your API key (starts with `pplx-`)
  3. Paste it on the Connectors page
- **What to add to CLAUDE.md:**
  ```
  **Perplexity** — Web search and deep research
  - **Connector:** Co-Writer platform (app.alexmcfarland.ai/connectors)
  ```

### Firecrawl

- **What it does:** Scrape web pages to clean markdown, crawl entire sites, discover URLs, extract structured data
- **API key type:** Firecrawl API key
- **Setup steps:**
  1. Go to [Firecrawl Dashboard](https://firecrawl.dev/app/api-keys)
  2. Create an account and generate an API key (starts with `fc-`)
  3. Paste it on the Connectors page
- **How the setup skill should use it:** If the user shares their website, blog, portfolio, or any URL during the interview — scrape it immediately. Use the content to auto-fill voice patterns, topics, audience, brand language, and expertise areas instead of asking the user to describe them manually. This dramatically speeds up onboarding.
- **What to add to CLAUDE.md:**
  ```
  **Firecrawl** — Web scraping and site crawling
  - **Connector:** Co-Writer platform (app.alexmcfarland.ai/connectors)
  ```

### Discord

- **What it does:** Manage channels, send/read/delete messages, threads, pins, list members
- **API key type:** Compound credential — Discord bot token + Server (Guild) ID
- **Setup steps:**
  1. Go to [Discord Developer Portal](https://discord.com/developers/applications)
  2. Create a new application → go to Bot → Reset Token → copy the bot token
  3. Enable **Server Members Intent** and **Message Content Intent** under Privileged Gateway Intents
  4. Go to OAuth2 → URL Generator → select `bot` scope → select permissions (Manage Channels, Send Messages, Read Message History, Manage Messages, Manage Threads)
  5. Copy the generated URL → open it → select your server → Authorize
  6. Get your Server ID: in Discord, Settings → Advanced → enable Developer Mode, then right-click your server name → Copy Server ID
  7. Enter bot token and guild ID on the Connectors page
- **What to add to CLAUDE.md:**
  ```
  **Discord** — Community management
  - **Server:** [server name]
  - **Connector:** Co-Writer platform (app.alexmcfarland.ai/connectors)
  ```

---

## Cowork Official Connectors

These are installed directly in Claude Cowork (or Claude Desktop) via the Connectors directory. The user doesn't need the Co-Writer platform for these — they're available to all Claude users.

Tell the user: *"Claude Cowork also has its own official connectors. Go to Cowork → Connectors to browse what's available. Here are some common ones:"*

### Airtable

- **What it does:** Read/write records, tables, manage bases
- **Where to install:** Cowork → Connectors → search "Airtable"
- **Optional guided setup:** If the user wants to use Airtable for editorial pipeline tracking, offer to help them design:
  - Base structure (one base per project or one for everything)
  - Table design (e.g., Content Pipeline with fields: Title, Status, Publish Date, URL, Type)
  - Status workflow (Idea → Brief → Draft → Review → Published)
  - Then add to CLAUDE.md:
    ```
    **Airtable** — Editorial pipeline tracking
    - **Base:** [Base name] (`appXXXXXXXXXXXXX`)
    - **Tables:**
      - [Table name] (`tblXXXXXXXXXXXXX`) — [purpose]. Fields: [key fields].
    - **Rule:** If it's something you *write*, it stays in the workspace. If it's something you *track*, it goes in Airtable.
    - **Connector:** Cowork official
    ```

### Notion

- **What it does:** Read/write pages, databases, comments, search
- **Where to install:** Cowork → Connectors → search "Notion"
- **What to add to CLAUDE.md:**
  ```
  **Notion** — [What they use it for — notes, docs, project management, etc.]
  - **Connector:** Cowork official
  ```

### Google Drive

- **What it does:** Read/search docs, sheets, files
- **Where to install:** Cowork → Connectors → search "Google Drive"
- **What to add to CLAUDE.md:**
  ```
  **Google Drive** — [What they use it for]
  - **Connector:** Cowork official
  ```

### Slack

- **What it does:** Send/read messages, channels, threads
- **Where to install:** Cowork → Connectors → search "Slack"
- **What to add to CLAUDE.md:**
  ```
  **Slack** — [What they use it for — team comms, client channels, etc.]
  - **Connector:** Cowork official
  ```

---

## When the User Wants to Set One Up

If the user says they want to set up a specific connector during the interview, walk them through it right there:

1. Show them the setup steps from above
2. Help them get the API key / credentials
3. For tools that benefit from structure (Airtable, Kit), offer to help design their setup
4. Add the properly configured entry to their CLAUDE.md
5. Then continue with the rest of the interview

Don't force it — if they'd rather do it later, just note it in the CLAUDE.md with placeholder values and move on.
