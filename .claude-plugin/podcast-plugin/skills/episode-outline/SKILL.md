---
name: episode-outline
description: Structured podcast episode outlines designed for natural conversation flow. Hook opening, segmented talking points, transition notes, and closing with CTA — detailed enough to record from, loose enough to feel natural.
---

# Episode Outline

Read the CLAUDE.md file in the working directory if it exists. Do this silently — do not narrate that you're reading it. Use the context to inform your output.

If a voice skill is installed, apply it. If not, pick up the user's natural voice from CLAUDE.md context.

You build podcast episode outlines that a host can sit down and record from without a full script. The outline gives enough structure to stay on track and enough breathing room to sound like a real conversation — not a teleprompter read.

## What You Need

Ask the user for:
- **Topic or episode idea** — what the episode covers
- **Format** — solo, interview, co-hosted, or panel. Default to solo if not specified.
- **Target length** — short (15-20 min), standard (30-45 min), or long (60+ min). Default to standard if not specified.
- **Audience context** — who listens and what they already know (pull from CLAUDE.md if available, don't re-ask)

If the user provides a brief, notes, or research doc, use it directly. Don't ask questions the material already answers.

## Outline Structure

Produce the outline in this format:

### EPISODE HOOK (first 30-60 seconds)

The opening that grabs attention before the listener decides to skip. This is not a summary of the episode — it's the reason someone keeps their earbuds in.

Approaches that work:
- A bold claim or contrarian take on the topic
- A story that drops the listener into the middle of something interesting
- A specific result, number, or outcome that raises questions
- A question the listener has been asking themselves

Rules:
- No "welcome to the show" throat-clearing as the very first thing. Hook first, housekeeping after.
- Create an information gap — enough to intrigue, not enough to satisfy
- One strong opening, not three weak options

### EPISODE INTRO (after the hook)

Brief context that sets up the episode:
- What the listener will walk away with
- Why this topic matters right now
- Any setup needed for the main content (a quick "here's the backstory" if relevant)

If it's an interview format, introduce the guest here — one sentence on who they are and why they're worth listening to on this topic. Not a full bio.

### SEGMENTS (3-5 segments)

Each segment includes:

**Segment Title** — A clear label for this section of the episode.

**Key Point** — The core idea of this segment in one sentence. This is the thing the listener should remember.

**Talking Points / Bullets** — 3-6 bullets the host can riff on. These are prompts, not scripts. Each bullet is a sentence or phrase that triggers a 1-3 minute riff.

**Supporting Material** — Specific examples, stories, data, or anecdotes that bring the key point to life. Prioritize the host's own experience when available. Never fabricate stories, metrics, or quotes — flag where the host should supply their own.

**Transition to Next Segment** — A natural bridge sentence or question that moves to the next topic. Not "and now let's talk about..." but an actual connection between the ideas. Examples:
- A question the current segment raises that the next one answers
- A callback that reframes what was just discussed
- A "but here's the thing..." pivot

### INTERVIEW QUESTIONS (if applicable)

If the format is interview or panel, include:
- 5-8 prepared questions ordered for conversational flow (not a rapid-fire list)
- 2-3 follow-up prompts per question for when the guest gives a surface-level answer
- One "unexpected" question that goes somewhere the guest probably hasn't been asked before
- Mark which questions are essential vs. optional (in case the conversation runs long or goes in a better direction)

### CLOSING (final 2-3 minutes)

- **Key Takeaways** — 2-3 sentences that recap the most important things from the episode. Not a segment-by-segment rehash — the big ideas.
- **CTA** — Subscribe, share, leave a review, check out show notes, or whatever the host's standard ask is. Pull from CLAUDE.md if a standard CTA exists.
- **Tease** — If there's a next episode or related content, tease it. One sentence.

## Formatting Rules

- Use bullet points and short phrases over full paragraphs — these are speaking prompts, not reading material
- Bold key phrases the host should hit (`**this is the important bit**`)
- Include approximate time allocations per segment based on target length
- Keep talking point bullets actionable — "explain why X fails" not just "X"
- Add `(personal story opportunity)` markers where the host could insert their own experience
- Add `(audience callout)` where directly addressing the listener would land well

## What You Don't Do

- Don't write a full script — this is an outline the host records from naturally
- Don't fabricate stories, statistics, or quotes — use what the user provides or mark where they need to supply their own
- Don't include generic filler ("and that's really powerful" / "this is a game-changer")
- Don't write interview questions that start with "So tell me about..." — make them specific enough to get interesting answers
- Don't pad segments to hit a length target — if three segments cover the topic, three segments is the right number
