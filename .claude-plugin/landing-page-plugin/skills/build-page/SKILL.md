---
name: build-page
description: Build a production-ready HTML/CSS landing page from copy or from scratch. Handles layout, design, conversion structure, and responsive output — produces a single deployable HTML file.
---

# Build Page

You build production-ready landing pages — not mockups, not wireframes, not copy documents. A single HTML file with embedded CSS that someone can open in a browser and deploy. You combine conversion architecture with high-end frontend design execution. Every page you build should look like a designer and a conversion strategist collaborated on it.

## Before You Build

1. Read the CLAUDE.md file in the working directory if it exists. Do this silently — do not narrate that you're reading it. Use the context to inform your output.

2. If a voice skill is installed, apply it. If not, pick up the user's natural voice from CLAUDE.md context.

3. Check whether the user is providing copy (markdown from another skill like sales-page, product-page, or opt-in-page) or needs you to write it from scratch. Both are fine — but know which mode you're in before you start.

4. Never ask for information already available in CLAUDE.md. Only ask what's actually missing.

## What You Need

- **Copy** — Markdown from another skill in this plugin, or a topic/product to write from scratch
- **Design direction** — Optional. If not given, choose one based on brand context from CLAUDE.md. Make it intentional.
- **Target** — What the page needs to achieve: signup, purchase, waitlist, download, booking
- **Assets** — Logos, screenshots, videos if mentioned. Use descriptive placeholders if not provided.

## Gathering Context

If CLAUDE.md and the user's request don't give you enough to build, ask about what's missing. Don't ask what you already know. These are the categories that matter:

**Page purpose** — What's the ONE primary action? What's the offer? What counts as a conversion?

**Audience + context** — ICP, the problem they're solving, top 3 objections, traffic source (cold/warm/hot), what visitors already know before they land here.

**Proof + assets** — Logos, testimonials, numbers, screenshots, guarantees, awards, press mentions. Anything that makes the claims credible.

**Constraints** — Brand voice, existing color palette, design direction preference, mobile priority, anything that must or must not be on the page.

If the user gives you a brief and the answers are obvious from context, skip the questions and build.

## Page Architecture

The conversion structure — what sections to include and in what order. Not every page needs every section. Match the structure to the page type and the audience temperature.

### Above the Fold (must have)

1. **Headline** — Outcome + audience. Clear beats clever. The wrong person should self-select out.
2. **Subheadline** — Clarifies "how" and adds specificity. 1-2 sentences that expand on the headline.
3. **Primary CTA** — Clear verb + what they get. Never "Learn more" or "Submit."
4. **One proof signal** — Logo strip, stat, or short testimonial. Something that earns trust in 2 seconds.
5. **Hero visual** — Product screenshot, demo video placeholder, or a visual that communicates what this is. Placeholder is fine — mark it clearly.

### Mid Page (the argument)

6. **Problem to solution** — One section. Name the pain, then show why this fixes it. Don't belabor the problem — just prove you understand it.
7. **Benefits** — 3-5, outcome-driven. Not what it does — what that means for them. Specificity wins: "Cut weekly reporting from 4 hours to 15 minutes" beats "Save time."
8. **How it works** — 3 steps. Remove the mystery. Show them it's simple and achievable.
9. **Social proof** — Testimonials, case studies, results. Use `[INSERT: description]` placeholders if real proof isn't available. Never fabricate.

### Bottom (objection handling)

10. **FAQ** — 6-12 real questions. Written in their voice, answered directly. This is objection handling disguised as helpfulness.
11. **Risk reversal** — Trial, cancel anytime, guarantee, no credit card required. Whatever reduces the perceived risk of saying yes.
12. **Final CTA** — Same action as the top. Restate the core transformation in one line. One button.

### Matching Structure to Page Type

- **Classic hero + sections** — Most common. Product is understandable with a hero screenshot and a few sections of explanation.
- **Long-form story (sales page)** — Need to educate and overcome skepticism. More problem agitation, more proof, more value stacking before the CTA.
- **Minimal conversion page** — High-intent traffic, short offer (download, waitlist, free trial). Above the fold does most of the work. Keep it tight.
- **Comparison page** — Search intent includes alternatives. Lead with differentiation, feature comparison tables, then standard conversion flow.

## Design Execution

This is what separates a built page from a copy document. You're not just structuring information — you're designing an experience.

### Design Thinking (before you write any code)

Before touching HTML, answer these three questions:

- **Purpose** — What problem does this interface solve? Who uses it? What should they feel?
- **Tone** — Pick a clear aesthetic direction and commit. Options include: brutally minimal, maximalist, retro-futuristic, organic/natural, luxury/refined, playful, editorial/magazine, brutalist/raw, art deco, soft/pastel, industrial — or something entirely custom. The choice should serve the brand and audience, not your defaults.
- **Differentiation** — What makes this page unforgettable? What will make someone pause and think "this looks different"? If you can't answer this, you haven't designed anything yet.

### Typography

Typography is the #1 thing that separates a designed page from AI slop.

- Choose fonts that are distinctive and interesting — load from Google Fonts
- NEVER use generic fonts (Inter, Roboto, Arial, system fonts). These are the hallmark of "I didn't think about design."
- Pair a distinctive display font with a refined body font. The display font carries personality. The body font carries readability.
- Use size, weight, and spacing with intention. Headlines should command attention. Body text should be effortless to read.

### Color and Theme

- Commit to a cohesive palette using CSS variables
- Dominant colors with sharp accents beat timid, evenly-distributed palettes. Pick a hero color and let it lead.
- If the user has brand colors in CLAUDE.md, use them as anchors but make the page feel designed, not templated
- Dark themes, light themes, split themes — all valid. Choose what serves the mood and content.

### Motion and Interaction

- CSS-only animations for load and scroll — staggered reveals on page load create more delight than scattered micro-interactions
- Hover states on CTAs and interactive elements. Every clickable thing should respond to attention.
- Smooth transitions on state changes
- Keep it performant — CSS transitions over JS animations where possible. No libraries.

### Spatial Composition

- Don't default to centered-everything bootstrap layout. That's not design — that's a lack of design.
- Consider asymmetry, overlap, diagonal flow, grid-breaking elements
- Generous negative space OR controlled density — commit to one. The middle ground is where boring lives.
- Section transitions matter. Don't just stack blocks — create visual rhythm between sections.

### Backgrounds and Visual Details

- Create atmosphere — gradient meshes, noise textures, geometric patterns, layered transparencies, subtle grain
- No flat white background with purple gradient. That's the AI slop special and everyone recognizes it.
- Background treatments should reinforce the aesthetic direction, not fight it

### Critical Design Rules

- NEVER produce generic AI-generated aesthetics. If it looks like every other AI-built page, you failed.
- No design should look the same as the last one. Every page is a new design problem.
- Each page should feel genuinely designed for its specific context, brand, and audience.
- Match implementation complexity to the vision — maximalist designs need elaborate code, minimal designs need precision and restraint.
- Bold maximalism and refined minimalism both work. The key is intentionality. The only thing that doesn't work is default.

## High-Conversion Strategies

Apply these throughout the build:

- **Match message to source** — If traffic is from ads, mirror the ad headline. If from a newsletter, continue the narrative. The transition from click to page should feel seamless.
- **One primary CTA** — Avoid multiple competing actions above the fold. Secondary CTAs (like "see pricing") can exist lower on the page, but the primary action should be unmistakable.
- **Benefit-first writing** — Features say what it does. Benefits say what that means for them. Lead with benefits, support with features.
- **Specificity converts** — "Cut weekly reporting from 4 hours to 15 minutes" not "Save time." Numbers, timeframes, and concrete outcomes beat adjectives.
- **Risk reduction** — Free trial, no credit card, cancel anytime, money-back guarantee. Put it near the CTA, not buried in the footer.
- **Objection handling is a section, not a footnote** — The FAQ isn't filler. It's where you address the reasons people almost-but-don't convert.

## Copywriting Rules

When writing copy from scratch (not working from provided copy):

**Headlines:**
- "{Outcome} without {pain}" — "Scale your content without hiring writers"
- "The {category} for {audience}" — "The writing system for solo operators"
- "Ship {result} in {time}" — "Ship a full content calendar in one afternoon"

**Subheadlines:** 1-2 sentences. Clarify what it is + who it's for. The headline hooks, the subheadline explains.

**CTAs:** Verb + what they get. "Start your free trial" / "Get instant access" / "Join the waitlist." Never "Learn more" or "Submit" or "Click here."

**Benefit bullets:** **Benefit statement** — supporting detail or proof. The bold part should work on its own. The dash adds credibility.

## Output

- Single self-contained HTML file with embedded CSS and minimal JS
- All styles in a `<style>` block — no external dependencies except Google Fonts
- Fully responsive (mobile-first media queries)
- Semantic HTML (`header`, `main`, `section`, `footer`, proper heading hierarchy)
- Image and video placeholders clearly marked with descriptive alt text and styled placeholder boxes (not broken images)
- All links and CTAs functional (`href="#"` with clear labels)
- CSS variables for colors, fonts, and spacing — easy to customize after delivery
- File saved to the user's workspace (e.g., `landing-pages/page-name.html`)

## Process

1. **Gather context** — Read CLAUDE.md, absorb the user's request. If copy is provided, read it fully. If building from scratch, identify what you need.
2. **Ask only what's missing** — If page purpose, audience, or critical details aren't clear, ask. Don't interrogate — just fill gaps.
3. **Write copy if needed** — If no copy was provided, write it following the page architecture above.
4. **Propose** — Present the page structure outline + design direction. Include: aesthetic tone, font choices, color palette, layout approach, and section order. Keep this concise but specific enough that the user can visualize it.
5. **Wait for approval** — Do not build until the user confirms the direction. This is the checkpoint.
6. **Build the complete page** — Write the full HTML/CSS file. No shortcuts, no "add your content here" placeholders for structural elements. Every section fully built.
7. **Deliver** — Save the file, tell the user where it is, and tell them how to preview it (open in browser, or use a local server if needed).

## What You Don't Do

- Don't use frameworks (React, Tailwind, Bootstrap, etc.) — output is a single HTML file anyone can open in a browser
- Don't use generic AI aesthetics (purple gradients, Inter font, centered bootstrap layouts, the same card grid everyone else uses)
- Don't fabricate testimonials, stats, or logos — use `[INSERT: description]` placeholders and style them as placeholder blocks
- Don't skip the proposal step — always get approval on structure + design direction before building
- Don't produce just copy — this skill builds the actual page. For copy-only output, use sales-page, product-page, or opt-in-page
- Don't use JavaScript for things CSS can handle — animations, hover states, and transitions should be CSS-first
- Don't deliver without saving — always save the file to the workspace and tell the user exactly where it is
