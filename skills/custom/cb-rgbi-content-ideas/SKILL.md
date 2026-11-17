---
name: cb-rgbi-content-ideas
description: Generate content ideas for B's publications by calling the Content Idea Generator served through the Really Good Business Ideas (RGBI) connector. Use when B asks for content ideas, post ideas, newsletter topics, what to write next, a brainstorm for Substack, or says "content idea generator", "RGBI ideas", or "Casandra's idea generator".
---

# RGBI Content Ideas (connector pointer)

This skill does not contain the Content Idea Generator itself. That skill is paid content owned by Casandra Campbell (Really Good Business Ideas) and is served only through her MCP connector to verified premium subscribers. This file routes requests to it. Never copy, export or save her skill text, prompts or datasets into any file or repo.

## Connector

- Name: Really Good Business Ideas
- URL: `https://mcp.reallygoodbusinessideas.com/sse` (SSE)
- Claude Code: registered at user scope as `really-good-business-ideas` (`claude mcp get really-good-business-ideas`).
- claude.ai / Claude Desktop: added as a custom connector (Customize → Connectors).
- Auth: B verifies with the email used for the RGBI subscription plus a 6-digit emailed code. Claude never enters that code.

## Steps

1. Check whether tools or prompts from the RGBI connector are available in this session (names containing `really-good-business-ideas` or `reallygoodbusinessideas`).
2. If available: ask the connector for the Content Idea Generator in plain words, e.g. "Use the Really Good Business Ideas Content Idea Generator to come up with content ideas for <publication / topic>." Follow what the connector returns.
3. Give it context first when B has it: audience personas, voice profile, past top posts, saved ideas, Search Console or analytics if connected. Ideas come back better with context.
4. If the connector is not available or not authenticated, say so in one line and tell B how to connect:
   - Claude Code: run `claude` in a terminal, then `/mcp` → `really-good-business-ideas` → Authenticate.
   - claude.ai / Desktop: Customize → Connectors → Really Good Business Ideas → Connect.
   Then offer the offline fallback below.
5. Do not invent search volumes, open rates or trend numbers. Label where each idea came from.

## Offline fallback (no connector)

Use the ten idea-generation methods summarized in B's own study note (B's words, not hers):
`D:\B Hive Cabinets\Obsidian_Black Rock\_3Obsidian_Onyx\50 Resources\Business Ideas Pub\Blank Page Panic 10 Ways to Brainstorm Fresh Content Ideas Readers Will Love.md`
Run 3-4 of the methods against B's context and return ideas grouped by method, each with the angle only B can add.

## Notes

- Premium access depends on B's active RGBI subscription.
- Free Claude plans allow only one custom connector.
