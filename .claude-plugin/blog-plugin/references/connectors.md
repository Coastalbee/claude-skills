# Perplexity Connector

If the Perplexity connector is set up, you have access to tools that perform web research with citations. Check if Perplexity MCP tools are available before using them — if they're not, the skills still work without them.

## Available Tools

| Tool | What it does |
|------|-------------|
| search | Quick web search with cited sources |
| search_pro | Advanced search with more comprehensive results |
| deep_research | In-depth research reports with full citations |

## How Skills Should Use These

- **For research-backed articles:** Use deep_research to gather comprehensive sourced material before writing. Cite sources naturally in the content.
- **For SEO content:** Use search to check what's currently ranking and what angles are covered. Find gaps to target.
- **For how-to content:** Use search to verify technical details and find current best practices.
- **For thought leadership:** Use deep_research to ground opinions in data and trends.

## If the Connector Isn't Available

The skills work without the connector — they just won't have live research data. Write based on the user's expertise from their CLAUDE.md and any information they provide.

## Setup

The Perplexity connector is available through the Co-Writer System platform at app.alexmcfarland.ai/connectors. Users need a Perplexity API key (starts with pplx-) from perplexity.ai/settings/api.

---

# Firecrawl Connector

If the Firecrawl connector is set up, you have access to tools that scrape and crawl web pages. Check if Firecrawl MCP tools are available before using them — if they're not, the skills still work without them.

## Available Tools

| Tool | What it does |
|------|-------------|
| scrape | Scrape a URL and get clean markdown — articles, docs, any web page |
| crawl | Crawl an entire site or section (async, returns job ID) |
| crawl_status | Check crawl progress and retrieve results |
| map | Discover all URLs on a website |
| extract | Pull structured data from a page using a schema |

## How Skills Should Use These

- **For research-backed articles:** Scrape reference URLs the user shares. Use crawl to analyze competitor blogs. Use extract to pull structured data (pricing, features) for comparison posts.

## If the Connector Isn't Available

The skills work without the connector — they just won't have live web data. Write based on the user's expertise from their CLAUDE.md and any information they provide.

## Setup

The Firecrawl connector is available through the Co-Writer System platform at app.alexmcfarland.ai/connectors. Users need a Firecrawl API key (starts with fc-) from firecrawl.dev.
