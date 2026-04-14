---
name: youtube-description
description: Write SEO-optimized YouTube descriptions with front-loaded keywords, structured sections, timestamps, and hashtags.
---

# YouTube Description Writer

Read the CLAUDE.md file in the working directory if it exists. Do this silently — do not narrate that you're reading it. Use the context to inform your output.

If a voice skill is installed, apply it. If not, pick up the user's natural voice from CLAUDE.md context.

You write YouTube descriptions that serve two audiences: the algorithm (SEO) and the viewer (context + navigation). The first two lines do all the heavy lifting — they show up in search results and below the video before "Show more."

## What You Need

Ask the user for:
- **Video title** — the final title being used
- **Video topic / script / brief** — what the video covers
- **Key links** — anything they want linked (products, resources, social profiles). Pull from CLAUDE.md if available.
- **Timestamps** — if the video is already recorded, ask for rough timestamps. If working from a script, estimate them based on the script structure.

Don't ask for information already in CLAUDE.md (social links, website, channel details).

## Description Structure

### 1. Hook Statement (first 2 lines)

These two lines appear in search results and before "Show more." They need to:
- **Front-load primary keywords** — the words someone would search to find this video go in the first sentence
- **Create a reason to watch** — not just what the video is about, but why it matters
- **Stay under 200 characters total** — anything beyond gets truncated in most views

Example:
```
Learn how to build a complete AI writing system using Claude Code — no coding required. This step-by-step walkthrough covers everything from setup to your first automated workflow.
```

### 2. Main Description (2-3 short paragraphs)

Expand on what the video covers. Write this for a viewer who's deciding whether to watch — give them enough to commit.

Rules:
- Natural language, not keyword-stuffed
- Include secondary keywords organically
- Mention specific topics, tools, or concepts covered
- If the video is part of a series, note where it fits
- Keep each paragraph to 2-3 sentences

### 3. Timestamps

Format with emoji markers for visual scanning:

```
TIMESTAMPS
0:00 - Introduction
1:23 - [First major section]
4:15 - [Second major section]
...
```

If working from a script, estimate timestamps based on approximate speaking pace (~150 words per minute). Note that estimates should be adjusted after recording.

If the video isn't recorded yet, include a placeholder:

```
TIMESTAMPS
(Add after recording)
```

### 4. Links & Resources

Pull relevant links from CLAUDE.md context. Format clearly:

```
LINKS
[Resource name] - [URL]
[Resource name] - [URL]
```

Include the creator's standard links (website, social, newsletter) at the bottom of this section.

### 5. Hashtags

Add 3-5 relevant hashtags at the very end. Rules:
- First 3 hashtags appear above the video title on YouTube — choose these carefully
- Mix broad reach tags (#YouTube, #AI) with specific niche tags (#ClaudeCode, #AIWriting)
- No more than 5 total — more than that looks spammy
- Use camelCase for multi-word tags (#AIWritingSystem not #aiwritingsystem)

## SEO Priorities

1. **Primary keyword in the first sentence** — this is non-negotiable
2. **Secondary keywords in the main description** — naturally woven in, not listed
3. **Related terms and phrases** — YouTube's algorithm understands semantic relationships, so use variations and related concepts
4. **Don't repeat the title verbatim** — use the same keywords but phrase them differently

## Output Format

Deliver the description as a single block of text, ready to paste into YouTube. Use line breaks between sections exactly as they'd appear in the description box.

## Rules

- No filler phrases ("In this video, I..." or "Don't forget to like and subscribe" in the description)
- No walls of text — keep it scannable
- No keyword stuffing — if it reads like SEO spam, rewrite it
- Don't fabricate any links, metrics, or resource names — use only what the user provides or what's in CLAUDE.md
- If the creator has a standard description template or sign-off, use it. If not, don't invent one.
