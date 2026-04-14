# Interview Guide

## Phase 1 — Welcome and Document Collection

Say:

> "Welcome. I'm going to help you build the foundation of your co-writing system — three context files that make everything Claude produces sound like you and speak to your audience.
>
> This is a one-time setup that takes 15–25 minutes. The more specific your answers, the better every piece of content will be from here on out.
>
> **Before we start — do you have any existing documents I should read first?**
>
> If you have any of the following, create a subfolder inside your co-writer folder (name it `source-docs` or anything you like) and drop them in there:
>
> - Your website or about page (save as a text file, or paste the URL)
> - Existing newsletters, blog posts, or articles you've written
> - A sales page or product description
> - Social media bios or LinkedIn profile
> - Customer research, surveys, or testimonials
> - Analytics reports or audience insights
> - Anything that describes you, your work, or your audience
>
> Drop whatever you have and let me know when you're ready. If you don't have anything, no problem — we'll build everything from scratch."

Wait for confirmation before proceeding.

---

## Phase 2 — Read and Analyze Documents

Before asking a single question, silently read every file in the project folder including any subfolders. Note what you know, what's missing, and what you'll need to ask about. Do not summarize what you found. Use it to skip questions you already know and make follow-up questions smarter.

If documents were provided: *"I've read through everything — I already have a solid foundation on [X]. I'll confirm a few things and fill in the gaps."*

---

## Phase 3 — Build USER.md

Introduce: *"Let's start with you as a person. USER.md is not about your writing style — that comes later in a separate voice skill. This file is about who you are, how you think, and how you operate. The more Claude understands you as a human being, the better it works with you."*

Interview topics — ask conversationally, one or two at a time. Push back on short answers.

**Note:** Do NOT ask about writing style, tone, voice, formatting preferences, or how content should sound. That is for the voice skill, not USER.md.

**Identity and Background**
- Name, location
- Their professional background and origin story — how did they get to where they are now?
- How long they've been doing what they do
- What drives them — what's the underlying motivation behind their work?

**How They Think**
- How do they approach problems? (Systematic and structured? Intuitive and fast? Big picture first? Details first?)
- How do they make decisions?
- What does their thinking process look like when they're working through something complex?
- Are they a planner or do they figure it out as they go?

**Working Style and Preferences**
- How do they like to collaborate? (One strong recommendation vs. options? Produce first then refine? Ask clarifying questions or just go?)
- What makes a working session feel productive vs. frustrating?
- How do they handle uncertainty — do they want Claude to flag it, make a judgment call, or ask?
- What pace do they work at?

**Personality and Values**
- What do they care most about in their work?
- What are they uncompromising about?
- What do they absolutely hate — in work, in how people operate, in the way things get done?
- How would people who know them well describe how they operate?

**Current Context**
- What are they focused on right now — what are the most important things they're working toward?
- What are the biggest challenges or constraints they're dealing with?
- What does their work life actually look like day to day?

Signal end: *"I have everything I need for USER.md. Let's move to your business."*

---

## Phase 4 — Build BUSINESS.md

Introduce: *"Now BUSINESS.md — your business, products, and brand voice. Claude uses this to make sure everything it writes represents your brand correctly."*

**Business Overview**
- Business name and what it does (2–3 sentences to someone smart who's never heard of it)
- Core mission or belief driving the business
- What makes them different from everyone else doing something similar

**Products and Services** (for each one)
- Name, description, who it's for, price point
- What outcome does the customer get?
- What makes it different from alternatives?

**Brand Voice**
- Three words describing brand personality
- How they want people to feel reading their content
- One thing the brand should be known for above everything else
- Competitors or adjacent players — how are they different?
- What they want completely separate from — topics, tones, associations to avoid

**Core Beliefs and Messaging**
- What they believe that most people in their space ignore
- What their audience consistently gets wrong
- 3–5 key messages content always comes back to

**Content Strategy**
- All active publishing platforms and content types
- Publishing frequency per channel
- Role of content in the business
- What has historically performed best and why

Signal end: *"Perfect. Last one — your customer profile."*

---

## Phase 5 — Build ICP.md

Introduce: *"Last file — ICP.md, your ideal customer profile. This is what makes Claude write to a specific person instead of everyone. Vague audience = vague content."*

**Who They Are**
- Describe as a real human being — not a demographic, a person
- Professional situation, daily life, life stage

**Their Problem**
- Main problem when they find this person/business
- How long they've had it, what they've tried, why it failed
- How it makes them feel daily

**What They Want**
- Surface outcome (what they say they want)
- Deeper desire (the real life/business change underneath)
- What success looks like 6 months after

**Fears and Objections**
- What holds them back
- Objections they raise, stories they tell themselves
- Why they think it won't work for them

**Their Language**
- Exact phrases they use for their problem — their words, not marketing language
- What they call themselves
- Language that resonates vs. language that turns them off

**What Makes Them Buy**
- What tips them from interested to committed
- Trust signals that matter most
- Where they hang out online
- What they need to see before buying

Signal end: *"I have everything. Let me build your files now."*

---

## Phase 6 — Generate Files and Close

Before outputting say:

> "Here are your three context files. To install them:
> 1. Create a new file called `USER.md` in your co-writer folder
> 2. Copy the contents and paste — save
> 3. Repeat for `BUSINESS.md` and `ICP.md`"

Output all three files using the templates in `output-templates.md`.

Close with:

> "Your co-writing system foundation is built. These are living documents — update them as your business evolves. The more current they are, the better everything Claude produces.
>
> Next step: set up your folder instructions, which tells Claude exactly how to use these files every session."
