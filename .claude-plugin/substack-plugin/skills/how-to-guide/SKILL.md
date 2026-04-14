---
name: how-to-guide
description: Write step-by-step tutorial newsletters where every step includes context, instruction, and expected result. Clear, specific, no vague advice.
---

# How-To Guide Newsletter

You write step-by-step tutorial newsletters that teach the reader how to do something specific. Every step is concrete enough that someone could follow along with your piece open on one screen and their work on the other.

## Before You Write

1. Read the CLAUDE.md file in the working directory if it exists. Do this silently — do not narrate that you're reading it. Use the context to inform your output.

2. If a voice skill is installed, apply it. If not, pick up the user's natural voice from CLAUDE.md context.

3. Never ask for information already available in CLAUDE.md. If you need the specific process, tool, or outcome that isn't clear from context, ask — but only what's actually missing.

## What You Produce

A complete tutorial newsletter with:
- Subject line
- Preview text (40-90 characters)
- Hook section
- Numbered steps with context/instruction/result blocks
- Wrap-up with next steps

## The Hook Section

Before the steps, earn the reader's attention. The hook section (100-200 words) should:

1. **Name the outcome** — what they'll be able to do after reading this ("By the end of this email, you'll have a working [X] that [does Y]")
2. **Acknowledge the pain** — why this is hard or why existing approaches fall short
3. **Set expectations** — how many steps, how long it takes, what they need before starting

If there are prerequisites (tools, accounts, prior knowledge), list them clearly before Step 1. Don't let the reader get to Step 4 before discovering they needed something from the start.

## Why The Current Approach Fails (Optional)

If the reader has likely tried and failed at this before, add a brief section (3-6 sentences) between the hook and Step 1 that explains:

- What the common approach is and why it seems logical
- Where it breaks down — the specific flaw
- What a better approach looks like (preview of your method)

This earns trust by showing you understand why they're stuck — not just what to do next. Skip this section if the topic is truly novel and the reader hasn't attempted it before.

## The Step Framework

Each step follows a strict three-part structure:

### Context (Why This Step Matters)
1-3 sentences explaining why this step exists. What problem does it solve? What goes wrong if you skip it? This prevents the reader from blindly following instructions without understanding the logic.

### Instruction (Exactly What To Do)
The actual action. Be specific enough that the reader doesn't have to interpret anything. Bad: "Set up your project." Good: "Create a new folder called `newsletter-drafts` in your working directory."

Rules for instructions:
- Use imperative voice ("Click," "Open," "Create," "Write")
- Include exact names, paths, labels, or values when applicable
- If there's a decision point, explain both options and when to choose each
- If something is clickable, name it exactly as it appears in the UI
- Code, file names, and technical terms go in `backticks`

### Expected Result (What They Should See)
What does success look like after completing this step? This is the reader's checkpoint. "You should now see [X]" or "Your [thing] should look like [this]."

If something commonly goes wrong at this step, add a brief troubleshooting note: "If you see [error], it usually means [cause]. Fix it by [solution]."

## Step Format

```markdown
## Step 1: [Action-oriented title]

[Context — why this step matters. 1-3 sentences.]

[Instruction — exactly what to do. As specific as needed.]

**What you should see:** [Expected result after completing this step.]
```

## How Many Steps

- **Sweet spot:** 5-8 steps for a newsletter format
- **If it's more than 10 steps:** Consider splitting into a series or simplifying the scope
- **If it's fewer than 4 steps:** It might be too thin for a standalone tutorial — consider combining with context or expanding scope

## Writing Rules

- **No vague instructions.** "Configure your settings appropriately" is not a step. What settings? What values? Why?
- **No assumed knowledge without stating it.** If Step 3 requires something from a previous guide, link to it or explain it.
- **One action per step.** If a step has "and" in it, it's probably two steps. Split it.
- **Show, don't just tell.** Include examples of what the output looks like — sample text, screenshots descriptions, code blocks, whatever makes the result tangible.
- **No fabrication.** Don't invent tool features, UI elements, or workflows that don't exist. If you're unsure about a specific detail, flag it with [VERIFY: description of what to check].

## When Things Go Wrong (Optional)

If the process has a common failure point, add a brief section before the wrap-up:

- Name the most common roadblock people hit
- Explain why it happens (usually a missed step or a misunderstanding)
- Give clear recovery steps that tie back to the core method
- Reframe the challenge as a signal of progress, not failure

Keep this to 3-5 sentences. Not every how-to needs this — only include it when there's a genuinely common failure mode worth addressing.

## The Wrap-Up

After the final step:

1. **Recap the outcome** — one sentence confirming what they just built or accomplished
2. **What to do next** — one specific next action (not three options — one clear path)
3. **CTA** — reply with questions, share their result, link to the next guide in the series

## Output Format

```
Subject: [headline]
Preview: [40-90 character preview text]

---

[Hook section]

[Prerequisites if any]

[Numbered steps with context/instruction/result]

[Wrap-up]
```

Always include the subject line and preview text. Body uses markdown formatting suitable for email platforms.
