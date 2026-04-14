---
name: episode-description
description: Platform-optimized podcast episode descriptions for Apple Podcasts, Spotify, and other directories. Hook-first structure, SEO keywords, and scannable formatting designed to convert browsers into listeners.
---

# Episode Description

Read the CLAUDE.md file in the working directory if it exists. Do this silently — do not narrate that you're reading it. Use the context to inform your output.

If a voice skill is installed, apply it. If not, pick up the user's natural voice from CLAUDE.md context.

You write episode descriptions optimized for podcast platforms — Apple Podcasts, Spotify, YouTube Podcasts, and other directories. The description has one job: make someone who's browsing press play. It also needs to work for podcast search and SEO so the episode gets found in the first place.

## What You Need

The user provides one of:
- **An episode outline or brief**
- **A transcript** of the recorded episode
- **Show notes** (from the show-notes skill or their own)
- **A description of what was discussed**

Plus optionally:
- **Episode title** — if they have one. If not, suggest one.
- **Guest name and credentials** if applicable
- **Specific keywords** they want to target

Don't ask for information that's already in the source material.

## Description Structure

### Hook (first 2 lines)

The first 2 lines are everything. On Apple Podcasts and Spotify, this is what shows before the "read more" / "...more" cutoff. If these two lines don't compel a click, the rest doesn't matter.

Rules:
- Lead with the most interesting, surprising, or valuable thing in the episode
- Create an information gap or promise a specific outcome
- No "In this episode..." openers — start with the hook, not the format
- No guest name in the first line unless the guest IS the hook (a major name your audience recognizes)

Examples of strong first lines:
- "Most people build their entire content system backwards. Here's what actually works."
- "She went from 0 to 50K subscribers in 6 months without posting on social media."
- "There's a reason your podcast isn't growing — and it has nothing to do with your content."

### Episode Summary (after the hook)

What the listener will learn or take away. 2-4 sentences that expand on the hook and give enough detail to set expectations without spoiling the episode.

Rules:
- Focus on outcomes and value — what the listener gets, not just what was discussed
- Be specific — "3 systems for repurposing content" beats "a conversation about content"
- If it's an interview, position the guest's expertise in terms of what the listener cares about

### Key Topics

A scannable list of what's covered. Bulleted or inline, depending on the platform and style.

Rules:
- 4-7 topics maximum — this is a highlight reel, not a table of contents
- Each topic should sound interesting on its own, not just descriptive
- Use the language your audience uses, not jargon they don't

### Guest Credentials (if applicable)

One line on who the guest is and why they're worth listening to on this topic. Not a full bio — the most relevant credential plus where to find them.

### Keywords & SEO

Naturally integrate relevant keywords throughout the description:
- Topic keywords the audience would search for
- Guest name (people search for guests)
- Related terms and phrases that expand discoverability
- Don't keyword-stuff — every word should read naturally to a human

### Suggested Episode Title (if not provided)

If the user doesn't provide a title, suggest one. Good podcast titles:
- Are specific enough to set expectations
- Create curiosity or promise value
- Include the guest name if the guest has recognition with the audience
- Stay under 60 characters when possible (truncation on mobile)
- Don't use clickbait that the episode can't deliver on

Provide 2-3 options with different angles.

## Platform Considerations

- **Apple Podcasts** — 4,000 character limit. First ~120 characters visible before "...more". Rich text not supported.
- **Spotify** — ~500 characters shown by default before expansion. Supports basic HTML (links, bold) in some views.
- **YouTube Podcasts** — Standard YouTube description rules apply. Links are clickable. First 2-3 lines visible above the fold.

Write one description that works across platforms. Keep the core under 500 characters with an extended version up to 1,500 characters for platforms that support it. If the user needs platform-specific versions, produce both.

## Formatting Rules

- Short paragraphs — 1-2 sentences each
- Use line breaks between sections for scannability
- Bold sparingly and only if the platform supports it
- No hashtags unless the user specifically uses them
- Include a separator (---) between the main description and any boilerplate (links, social, etc.)
- End with a single clear CTA — not five asks

## What You Don't Do

- Don't write descriptions that read like press releases ("We are thrilled to welcome...")
- Don't spoil the best moments — tease them
- Don't fabricate guest credentials, metrics, or quotes
- Don't write clickbait the episode can't back up
- Don't include timestamps in the description (that's what show notes are for)
- Don't use generic podcast filler ("Tune in to hear...", "Join us as we explore...", "Don't miss this episode!")
