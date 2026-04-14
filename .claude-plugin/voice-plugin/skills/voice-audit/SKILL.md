---
name: voice-audit
description: Quality check an existing voice profile — find what's strong, what's thin, and what's missing. Use when you want to evaluate whether a voice profile is good enough to produce authentic output.
---

# Voice Profile Audit

You are evaluating the quality of an existing voice profile. Your job is to assess whether this profile gives Claude enough internalized understanding to write authentically as this person — or whether it reads like a generic style guide that will produce mechanical output.

## Step 1: Find the Profile

Look for voice skill files in the workspace. Check common locations:
- `skills/` directory
- Any file with "voice" in the name
- Any SKILL.md with a `voice-profile` name in its frontmatter

If you find multiple voice profiles, list them and ask which one to audit.

If you find none, say: "I can't find a voice profile in your workspace. Run `/voice:create` to build one from scratch."

## Step 2: Evaluate

Read the voice profile and evaluate it against these criteria. For each one, assess whether it's **strong**, **thin**, or **missing**.

### Voice Identity (the character brief)

**Strong:** Specific enough that you could distinguish this person from anyone else. Written as character direction ("You are someone who..."), not a trait list. If Claude only read this section, it would still produce recognizably correct output.

**Thin:** Exists but is generic. Could describe many people. "Writes in a conversational, professional tone" tells Claude almost nothing.

**Missing:** No character brief at all — the profile jumps straight into patterns or rules.

### Signature Moves

**Strong:** 5-8 concrete, observable patterns with real examples from the person's writing. Each one describes a specific structural or stylistic habit, not a vague quality.

**Thin:** Vague descriptions without examples. "Uses humor" instead of "drops dry one-liners mid-paragraph without setup." Or has patterns but no examples to anchor them.

**Missing:** No section covering recurring patterns or structural habits.

### Tone Modes

**Strong:** 2-3 distinct contexts with clear descriptions of how the voice shifts in each. Includes examples.

**Thin:** One flat description that doesn't capture how the voice changes across contexts. Or mentions multiple modes but without enough detail to be useful.

**Missing:** No acknowledgment that the voice has different modes.

### Never List

**Strong:** Specific phrases, patterns, and AI defaults to suppress. Concrete enough that Claude can pattern-match against them. Includes alternatives where relevant.

**Thin:** Too short (1-2 items), too vague ("avoid jargon"), or just a list of generic AI cliches without connecting them to why they conflict with this specific voice.

**Missing:** No anti-patterns documented at all.

### Calibration Examples

**Strong:** 3-5 real excerpts with annotations explaining what makes each one sound like this person. The annotations point to specific moves and choices.

**Thin:** Examples exist but without annotations. Or annotations are vague ("this is a good example of their style").

**Missing:** No real writing samples included in the profile.

### Internalization vs. Rules

**Strong:** The profile reads like character direction an actor would use. Claude can inhabit this voice, not just follow instructions about it.

**Thin:** Mixed — some sections are character direction, others are rule lists. The overall effect is that Claude would partially inhabit and partially checklist.

**Weak:** The profile is fundamentally a style guide — a list of do's and don'ts. Claude will follow it mechanically, producing a caricature rather than an authentic voice.

## Step 3: Report

Present a concise audit. Don't overwhelm — flag what matters.

```
## Voice Profile Audit: [Name]

| Section | Status | Notes |
|---------|--------|-------|
| Voice Identity | [Strong/Thin/Missing] | [Specific note] |
| Signature Moves | [Strong/Thin/Missing] | [Specific note] |
| Tone Modes | [Strong/Thin/Missing] | [Specific note] |
| Never List | [Strong/Thin/Missing] | [Specific note] |
| Calibration Examples | [Strong/Thin/Missing] | [Specific note] |
| Overall Approach | [Internalized/Mixed/Rules-based] | [Specific note] |
```

After the table, give 2-3 sentences on the overall assessment. Be direct: "This profile will produce [good/mediocre/generic] output because [reason]."

Then list the highest-impact fixes — the 1-3 changes that would most improve the profile's effectiveness.

## Step 4: Offer Next Step

```
Want to fix these now? Run `/voice:update` and I'll walk you through targeted improvements.
```

## Rules

- Be specific in every assessment — not "thin" but "thin because [exact reason]"
- Lead with the highest-impact issues, not an exhaustive list
- The "internalization vs. rules" criterion is the most important — a profile with great patterns but written as a checklist will still produce mechanical output
- Don't rewrite the profile during audit — that's the update skill's job
- If the profile is genuinely strong, say so. Don't manufacture issues.
