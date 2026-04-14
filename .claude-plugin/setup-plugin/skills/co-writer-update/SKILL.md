---
name: co-writer-update
description: Scan your entire workspace, memory, connectors, and usage to find what's missing or outdated in your CLAUDE.md — then update it. Autonomous, evidence-based, minimal questions. Use when your system file needs a refresh.
---

# Co-Writer System Update

You are autonomously updating an existing CLAUDE.md by scanning everything the user already has. Your job is to gather evidence from the workspace, memory, connectors, installed plugins, folder structure, and content files — then use that evidence to fill gaps, fix outdated sections, and strengthen the CLAUDE.md.

**This is not an interview.** You read everything first, draft updates from evidence, then present the proposed changes for approval. Only ask the user a question when you genuinely cannot infer the answer from existing files.

**If no CLAUDE.md exists**, tell the user: "You don't have a CLAUDE.md yet. Run `/setup:co-writer-setup` to build one from scratch." Then stop.

---

## Step 1: Deep Scan

Read ALL of these. Don't skip any. Don't summarize from memory — actually read the files.

### Required reads:
1. **CLAUDE.md** — the current system file (this is what you're updating)
2. **Workspace folder structure** — `ls -R` the workspace directory. What folders exist? What content is in them? What's empty?
3. **Memory files** — check for `.memory/` directory. Read `MEMORY.md` index and any individual memory files. These contain business decisions, product changes, preferences, and context that may not be in the CLAUDE.md yet.
4. **Content files** — scan published content (newsletters, scripts, social posts). Read a sample of recent ones. These reveal topics, audience, positioning, and voice that the CLAUDE.md might be missing.
5. **Installed plugins** — check what plugins are installed. Each plugin's capabilities should be reflected in what the CLAUDE.md says about content production.
6. **Voice profile** — check if a voice profile skill exists and is installed. If so, confirm the CLAUDE.md voice section is just a pointer (not duplicating voice rules).
7. **Context folder** — if a `context/` folder exists, read everything in it. Landing pages, bios, sales pages, client docs — all evidence.

### Optional reads (if they exist):
- **Connectors** — check what MCP connectors are available. Cross-reference against what's documented in CLAUDE.md.
- **Previous conversation history** — if accessible, scan for recurring topics, decisions, or patterns that should be captured in the CLAUDE.md.
- **Product files** — anything in `product/` or similar directories that describes offerings, pricing, methodology.
- **Playbooks** — operational processes that should be referenced in the CLAUDE.md.

---

## Step 2: Build the Evidence Map

After scanning, build an internal map of what you know vs. what the CLAUDE.md says. For each section, note:

- **What the CLAUDE.md currently says** (quote it)
- **What the evidence shows** (what you found in workspace/memory/content)
- **The gap** (what's missing, outdated, or contradictory)

### Sections to evaluate:

**Opening directive** — Does it speak TO Claude? Does it accurately describe what the co-writer handles based on actual usage?

**User Profile** — Is it complete? Does the memory or content reveal expertise, background details, or online presence not captured here?

**Business Profile** — Does it match reality? Check product files, landing pages, memory entries for pricing changes, new products, pivots. Are content channels accurate? In scope / out of scope current?

**Ideal Client Profile** — Is it specific? Check landing pages, sales copy, newsletter content for audience signals. Can you extract real frustrations, aspirations, and language from published content?

**Tools & Infrastructure** — Does it match what's actually connected? Are there connectors available but not mentioned? Tools mentioned but not connected? Config details missing?

**Voice** — Is it just a pointer? If it contains word lists or tone rules, flag for cleanup.

**Workspace Structure** — Does the documented tree match what's actually on disk? Undocumented folders? Ghost entries?

**Anything else** — Did you find sections in the CLAUDE.md that don't match the template in `references/example-claude-md.md`? Sections that should exist but don't? Content strategy, safety rules, operational patterns from memory that should be captured?

---

## Step 3: Present Findings and Proposed Updates

Show a summary table, then for each non-strong section, show the proposed update with evidence.

```
## CLAUDE.md Update — Scan Results

| Section | Status | Evidence Source |
|---------|--------|----------------|
| Opening | Strong ✓ | — |
| User Profile | Outdated | Memory shows new expertise not captured |
| Business Profile | Outdated | Product pricing changed per memory file |
| ICP | Thin | Landing page has detailed ICP not reflected here |
| Tools | Outdated | Discord connector added, not documented |
| Voice | Strong ✓ | — |
| Workspace | Outdated | 3 new folders on disk not documented |

### Proposed changes:
```

Then for each section that needs updating, show:

```
### [Section Name] — [Status]

**Currently says:**
> [quote the current content]

**Evidence found:**
- [source]: [what it reveals]
- [source]: [what it reveals]

**Proposed update:**
> [the new content you'd write]
```

**Be specific about where the evidence came from.** "Your memory file `project_product_pivot.md` shows pricing changed to $1,497" — not "I think the pricing might have changed."

---

## Step 4: Ask About Gaps (Only If Necessary)

After presenting all evidence-based updates, check if there are sections where you genuinely couldn't find enough information. Only then ask — and batch the questions together:

```
I updated everything I could from your existing files. There are [X] things I couldn't find evidence for:

1. [Question — what you need and why]
2. [Question — what you need and why]

Answer what you can, skip what you want. I'll finalize the update either way.
```

If you found enough evidence for everything — **don't ask any questions.** Just present the proposed updates and move to approval.

---

## Step 5: Get Approval and Write

After presenting all proposed changes:

```
Here's everything I'd change. Say "go" to apply all, or tell me what to adjust.
```

Wait for approval. Then:

1. **Write the updated CLAUDE.md** — preserve strong sections exactly as-is, replace updated sections
2. **Create any missing workspace folders** if workspace section was updated
3. **Show a summary** of what changed

```
## Updates Applied

✅ Business Profile — updated pricing from $997 to $1,497 (source: memory)
✅ Tools — added Discord connector (source: connectors page scan)
✅ ICP — expanded with frustrations from landing page copy
✅ Workspace — added 3 undocumented folders
⏭ Opening — no changes needed
⏭ User Profile — no changes needed
⏭ Voice — no changes needed

Your CLAUDE.md is current. Run `/setup:co-writer-audit` anytime for a health check.
```

---

## Rules

- **Evidence first, questions last.** Scan everything before asking anything. Most updates can be inferred from existing files.
- **Actually read the files.** Don't summarize from what you think is there. Open them. Read them. Quote them.
- **Don't touch strong sections.** If it's accurate and complete, leave it alone.
- **Show your sources.** Every proposed change should cite where the evidence came from (memory file, content file, folder scan, connector check).
- **Batch questions.** If you must ask, ask everything at once at the end. Never interrupt the scan with questions.
- **Preserve their style.** If they wrote their CLAUDE.md with personality, keep it. Don't sterilize into generic markdown.
- **Use the setup template as structure reference.** Sections should match `references/example-claude-md.md` — but adapt to what they actually need.
- **No voice content in CLAUDE.md.** Voice section is always and only a pointer to the voice skill.
- **CLAUDE.md opens in directive voice.** "You are [name]'s co-writer..." not "This file tells Claude..."
- **Workspace is factual.** Scan disk, report what exists. Never ask the user to describe their own folder structure.
- **Write once at the end.** Collect all changes, get approval, then write the file once.
- **If everything is strong** — say so and stop. "Your CLAUDE.md matches your current setup. Nothing to update." Don't invent work.
- **Memory is gold.** Memory files often contain the most important context — product pivots, preference changes, architectural decisions. Prioritize these.
