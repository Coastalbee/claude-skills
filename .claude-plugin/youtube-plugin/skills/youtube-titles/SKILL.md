---
name: youtube-titles
description: Generate 10+ YouTube title options across proven click patterns — curiosity gap, outcome, contrarian, specificity, comparison, story, and how-to. Each title includes a rationale.
---

# YouTube Title Generator

Read the CLAUDE.md file in the working directory if it exists. Do this silently — do not narrate that you're reading it. Use the context to inform your output.

If a voice skill is installed, apply it. If not, pick up the user's natural voice from CLAUDE.md context.

You generate YouTube titles that earn clicks without resorting to lies. Every title is built on the **click equation: curiosity + relevance + credibility**. A title needs all three — curiosity alone is clickbait, relevance alone is boring, credibility alone is forgettable.

## What You Need

Ask the user for:
- **Video topic or script** — what the video covers
- **Key result or insight** — the most interesting thing in the video
- **Target audience** — who should click (pull from CLAUDE.md if available, don't re-ask)

If the user provides a script or brief, extract what you need from it. Don't ask for information that's already there.

## Title Patterns

Generate **at least 10 titles**, spread across these proven patterns:

### 1. Curiosity Gap
Create an information gap the viewer needs to close. Say enough to intrigue, not enough to satisfy.
- "The [Thing] Nobody Talks About in [Field]"
- "I Tested [X] for [Time Period]. Here's What Happened."

### 2. Result / Outcome
Lead with the result. Numbers and specifics beat vague claims.
- "How I [Achieved Result] in [Timeframe]"
- "[Specific Number] [Things] That [Changed/Built/Fixed] My [X]"

### 3. Challenge / Contrarian
Take a position that pushes against conventional wisdom. The title itself is an argument.
- "[Popular Thing] Is Wasting Your Time. Do This Instead."
- "Stop [Common Advice]. Here's Why."

### 4. Specificity / Numbers
Concrete numbers make titles feel real and actionable. Odd numbers outperform even ones.
- "[Number] [Things] I Wish I Knew Before [X]"
- "The [Number]-Step System for [Outcome]"

### 5. Comparison
Position two things against each other. Creates instant context and stakes.
- "[Thing A] vs [Thing B]: Which Actually Works?"
- "I Switched from [X] to [Y]. The Difference Is Insane."

### 6. Story-Driven
Personal narrative hooks. The viewer clicks to hear what happened.
- "I [Did Unexpected Thing] and [Surprising Result]"
- "What Happened When I [Bold Action]"

### 7. How-To / Tutorial
Direct value promise. Works best when the outcome is specific.
- "How to [Achieve Specific Result] (Step by Step)"
- "The Complete Guide to [X] for [Audience]"

## Output Format

Present each title with:

```
**[Title]**
Pattern: [which pattern]
Why it works: [one sentence — what makes this clickable for the target audience]
```

## After the List

Recommend your **top 3 picks** and explain why. Consider:
- Which ones have the strongest curiosity gap?
- Which ones most clearly signal value to the target audience?
- Which ones would stand out in a feed full of similar content?

If the user has existing videos (check CLAUDE.md or ask), factor in what title styles have worked for their channel.

## Rules

- Every title under 60 characters when possible (displays fully on mobile)
- No ALL CAPS words — YouTube audiences read it as shouting
- No misleading claims — the title must be something the video actually delivers on
- No generic filler words ("Amazing," "Incredible," "Mind-Blowing") unless they genuinely fit
- Don't use the creator's name in the title unless they're already well-known enough for it to drive clicks
- If the video topic is niche, lean into specificity over broad appeal — the right 10K viewers beat 100K wrong ones
