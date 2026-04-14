---
name: voice-update
description: Update an existing voice profile — fix weak sections, add new evidence, or refresh a stale profile. Use when your voice profile needs targeted improvements, not a full rebuild.
---

# Voice Profile Update

You are making targeted updates to an existing voice profile. This is a focused session — you're not rebuilding from scratch, you're improving what's already there.

## Step 1: Read the Current Profile

Look for voice skill files in the workspace. Check common locations:
- `skills/` directory
- Any file with "voice" in the name
- Any SKILL.md with a `voice-profile` name in its frontmatter

If you find multiple voice profiles, list them and ask which one to update.

If you find none, say: "I can't find a voice profile in your workspace. Run `/voice:create` to build one from scratch."

Read the full profile and understand its current state before proceeding.

## Step 2: Ask What Changed

One open question:

```
What do you want to update? Common reasons:

- **Voice drift** — your writing has evolved and the profile feels stale
- **Audit fixes** — the audit flagged sections that need work
- **New channel** — you started creating in a new format (podcast, YouTube, etc.) and your voice shows up differently there
- **Tighten it up** — specific sections feel weak or generic and you want to sharpen them

What's the situation?
```

Wait for their response. This tells you what kind of update session this is.

## Step 3: Collect New Evidence (If Needed)

**If updating due to voice drift or new channels**, ask for new samples:

```
Feed me your newer writing — the stuff that represents where your voice is now. Same rules as before: paste it, share URLs, or point me to a folder. Anything works.
```

Process the new evidence the same way voice-create does — scan files, fetch URLs, process pasted text.

**If fixing audit issues or tightening sections**, skip this step. You're working with the existing profile and the user's input, not new samples.

## Step 4: Targeted Edits

Based on what they told you and any new evidence, identify which sections need updating. Do NOT rewrite the entire profile — only touch what needs to change.

**For voice drift (new samples provided):**
- Re-analyze the relevant sections against the new evidence
- Ask 1-3 targeted ghostwriter-style questions about what changed: "Your newer writing is [observation]. Was that a deliberate shift, or did it just evolve?"
- Update the sections that have drifted — voice identity, signature moves, tone modes, examples
- Preserve what's still accurate

**For audit fixes:**
- Reference the specific issues flagged by the audit
- For thin sections: ask targeted questions to fill them out. "Your never list only has 2 items. What kind of writing makes you cringe? What AI output have you seen that made you think 'that sounds nothing like me'?"
- For missing sections: run a mini-interview for just that section, then write it
- For rules-based sections: rewrite them as character direction. Transform "use short sentences" into "you get impatient with fluff — if a sentence doesn't earn its place, it gets cut"

**For new channels:**
- Analyze how the voice shows up in the new context
- Add a new tone mode for the channel
- Ask: "How does your [channel] voice differ from your [existing channel] voice? Is it a deliberate shift or does the format just pull it in a different direction?"
- Update signature moves if the new channel reveals patterns not in the current profile

**For tightening:**
- Ask which sections feel weak
- For each one, ask 1-2 targeted questions to sharpen it
- Replace vague language with concrete specifics

## Step 5: Show Changes and Apply

Before saving, show the user exactly what's changing:

```
Here's what I'm updating:

1. **[Section]** — [What's changing and why]
2. **[Section]** — [What's changing and why]

[Show the actual new content for each section]

Want me to apply these changes, or adjust anything first?
```

Wait for approval. Then update the voice skill file in place.

After applying:

```
Updated. Here's what changed:
[Brief list]

Run `/voice:audit` anytime to check profile quality, or `/voice:update` again when things evolve.
```

## Rules

- Read the full existing profile before doing anything
- Only update sections that need it — don't rewrite the whole profile
- If new samples are provided, analyze them before asking questions — same "informed interview" principle as voice-create
- Ask questions ONE at a time
- Show all changes before applying — no surprises
- Preserve what's working — don't break strong sections while fixing weak ones
- If the user says "skip" or "that's fine" for a section, move on
- Never delete calibration examples unless replacing them with better ones from new samples
