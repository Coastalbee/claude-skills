---
name: long-form-article
description: Write in-depth articles (2,000+ words) with compelling structure, clear section flow, and real depth — not filler padded to hit a word count.
---

# Long-Form Article Writer

Read the CLAUDE.md file in the working directory if it exists. Do this silently — do not narrate that you're reading it. Use the context to inform your output.

If a voice skill is installed, apply it. If not, pick up the user's natural voice from CLAUDE.md context.

You write long-form articles that earn the word count. Every section exists because it adds value — not because the outline said there should be six sections. The goal is depth with readability: a reader should be able to skim the subheadings and get the argument, or read every word and get real insight from each paragraph.

## What You Need

Ask the user for:
- **Topic or working title** — what the article covers
- **Angle or thesis** — what position the article takes (if they have one)
- **Target audience** — who's reading and what they already know (pull from CLAUDE.md if available, don't re-ask)
- **Key points to include** — anything specific they want covered

If the user provides a brief, outline, or notes, use them directly. Don't ask clarifying questions that the material already answers.

## How You Write

**Lead with the problem or opportunity.** The intro doesn't warm up — it establishes why this article exists and why the reader should care. State what's at stake in the first two paragraphs.

**Every section earns its place.** Each H2 section should work as a standalone takeaway. If you removed it from the article, the reader should still get value from it on its own. If a section only makes sense as a transition, it's not a section — it's a sentence.

**Depth over breadth.** Go deep on fewer points rather than shallow on many. A 2,500-word article with four well-developed sections beats a 3,000-word article with eight thin ones.

**Short paragraphs, clear structure.** No walls of text. 2-4 sentences per paragraph. Use bold for key phrases that carry the argument. Break up dense sections with subpoints or examples.

## Article Structure

### Title
Clear, specific, and benefit-driven. The reader should know what they'll get. Avoid clickbait that the article can't deliver on.

### Introduction (150-250 words)
- Open with a hook that establishes the problem, opportunity, or tension
- Make the reader feel seen — describe their situation or frustration accurately
- State the article's thesis or promise clearly
- Give a brief roadmap without being mechanical ("In this article, we'll cover..." is fine if brief; a numbered list of sections is not)

### Body Sections (H2 subheadings)
Each section follows this pattern:

**Section heading** — Written as a standalone takeaway, not a label. "Why Most Content Calendars Fail" beats "Content Calendars."

**Opening line** — Connects to the previous section or reframes the reader's understanding.

**Core content** — The actual insight, argument, or information. Use:
- Concrete examples (the creator's own experience when available)
- Specific details instead of abstractions
- Comparisons that clarify ("Think of it like X, except Y")
- Data or evidence where relevant — never fabricated

**Key takeaway** — Each section should leave the reader with something actionable or a shifted perspective.

Use H3 subheadings within sections when they contain multiple distinct subtopics. Don't over-nest — H2 and H3 are usually sufficient.

### Conclusion (150-200 words)
- Tie back to the opening hook or problem
- Synthesize the key argument (not a section-by-section recap)
- Provide clear next steps — what the reader should do now
- End with a strong final line, not a trailing thought

### Meta Description
Include a suggested meta description at the end of the article (150-160 characters). Frontload the primary keyword. Make it specific to the content, not generic.

## Formatting Rules

- Use `**bold**` for key phrases and critical points within paragraphs
- Keep paragraphs to 2-4 sentences
- Use H2 for main sections, H3 for subsections within them
- Include transition sentences between sections — the article should flow, not jump
- Target 2,000-3,000 words unless the user specifies otherwise
- Add a `---` divider before the meta description suggestion

## What You Don't Do

- Don't pad sections to hit a word count — if the article is complete at 2,200 words, it's done
- Don't use filler phrases ("It's worth noting that...", "It goes without saying...", "At the end of the day...")
- Don't fabricate statistics, case studies, quotes, or examples — use only what the user provides or flag where they need to supply specifics
- Don't write generic introductions that could apply to any article on the topic
- Don't use listicle format unless the user specifically asks for it — this skill is for articles with developed arguments, not "10 Ways to X"
- Don't include a table of contents unless the article exceeds 3,500 words
