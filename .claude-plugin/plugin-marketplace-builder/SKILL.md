---
name: plugin-marketplace-builder
description: "Build and maintain Claude plugin marketplaces. Use when: creating new plugins, adding plugins to a marketplace GitHub repo, updating existing plugin commands or skills, adding new plugins to a marketplace, or setting up a private skill library. Covers correct plugin structure, command format, marketplace.json spec, and GitHub deployment. Works with both Claude Code and Claude Cowork."
---

# Plugin Marketplace Builder

Operational guide for building Claude plugins and maintaining plugin marketplace repos.

## ⚠️ Important: Run This in Claude Code, Not Cowork

**If you're currently in Cowork, stop here.**

Cowork runs in a sandboxed environment — it can't access your local file system or run terminal commands. Building a marketplace requires both: creating files on your machine and running `git` and `gh` commands to push them to GitHub.

**You need to run this in Claude Code.** Here's how to get there:

1. Open the **Claude desktop app**
2. Switch to the **Code** tab (it's in the top navigation)
3. Start a new session and re-run your request from there

Once you're in Claude Code, come back to this. Everything below will work.

---

## Step 0: GitHub Setup Check — Do This First, Wait for Response

**Before anything else, ask the user this exact question and stop:**

> "Before we build anything — do you have GitHub set up? Specifically:
> - A GitHub account (free at github.com)
> - The `gh` CLI installed (the command-line tool for GitHub)
> - Already logged in via `gh auth login`
>
> If yes, just say yes and we'll move straight to building. If no — or if you're not sure — just say no and I'll walk you through the setup right now. It takes about 5 minutes."

**Wait for their answer before proceeding.**

---

### If they say YES → skip to Guided Setup Workflow below.

### If they say NO (or unsure) → walk through this setup sequence, one step at a time:

**Step 0a — GitHub account**

Ask: "Do you have a GitHub account already, or do we need to create one?"

- If no account: Tell them to go to **github.com**, click Sign Up, and create a free account. Tell them to come back when it's done.
- If yes: Move to Step 0b.

**Step 0b — Install the gh CLI**

Tell them:

> "Now we need to install the `gh` CLI — that's GitHub's command-line tool. Open your terminal and run this:"

```bash
brew install gh
```

> "If you're on Windows or don't have Homebrew, go to **cli.github.com** — there's an installer for every platform. Come back when it's installed."

Wait for them to confirm it's installed.

**Step 0c — Authenticate**

Tell them:

> "Now log in. Run this in your terminal:"

```bash
gh auth login
```

> "It'll ask a few questions — choose **GitHub.com**, then **HTTPS**, then **Login with a web browser**. Your browser will open, you click Authorize, and you're done."

Wait for them to confirm it worked.

**Step 0d — Verify**

Tell them to run:

```bash
gh auth status
```

> "It should show your GitHub username with a ✓. If you see that, you're all set — tell me and we'll move on to building."

**Once they confirm GitHub is set up → proceed to Guided Setup Workflow.**

---

## Guided Setup Workflow

Once GitHub is confirmed, follow this sequence for a new marketplace. Don't skip steps — and don't move to the next step until the user confirms the current one is done.

1. **Name the repo and clarify private vs. public** — Ask the user what to call it, then ask this before creating anything:

   > "Do you want this to be a private repo (only you and people you invite can access it) or public (anyone can see it)?"

   Then help them choose based on their setup:

   | Their situation | Recommendation |
   |-----------------|---------------|
   | Using Claude Code only (personal) | Private is fine — Claude Code connects to GitHub directly and handles auth |
   | Using Cowork on a personal plan | Must be **public** — personal Cowork plans can only connect to public repos |
   | Using Cowork on a Claude Team plan | Private works — Team plan supports org plugins with authentication |

   If they're unsure which plan they're on, default to public. They can always make it private later if they upgrade or move to Claude Code.

2. **Group the skills into plugins** — Ask what skills they have. Group related skills together: 3-5 skills per plugin is a good range. If all skills are unrelated, one plugin with multiple skills is fine. Agree on plugin names before building.
3. **Build the folder structure** — Create all plugin folders, `plugin.json`, `skills/`, `commands/`, and root `marketplace.json` per the structure below. Do this fully before moving on.
4. **Move skills in** — Place each SKILL.md into the correct `skills/<skill-name>/SKILL.md` path.
5. **Write command files** — One per skill. Optional but strongly recommended (gives slash command interface).
6. **Create the repo and push** — Once the folder structure is complete, give the user these exact commands to run in their terminal (substituting their actual username and repo name):

   ```bash
   # Use --private or --public based on what they chose in step 1
   gh repo create your-username/your-marketplace --private --description "Our shared Claude skill library"
   cd ~/repos
   gh repo clone your-username/your-marketplace
   # Move the files you just built into the cloned folder, then:
   cd your-marketplace
   git add -A
   git commit -m "Initial marketplace"
   git push
   ```

   Tell them to come back when it's pushed.

7. **Connect to Cowork or Claude Code** — Once pushed, give them this command to add the marketplace:
   ```
   /plugin marketplace add your-username/your-marketplace
   ```
8. **Install and test a plugin** — Install one plugin, run a command, confirm it works.

---

## Core Architecture

Plugins extend Claude Code and Cowork with slash commands and background skills. They live in a GitHub repo and are distributed via marketplace.

**Distribution chain:**
1. Plugin files live in a GitHub repo (public or private)
2. Claude Code or Cowork connects via: `/plugin marketplace add your-username/your-repo`
3. Users install individual plugins via `/plugin install <name>@<marketplace-name>`

## Marketplace Repo Structure

```
your-marketplace/                     ← GitHub repo root
├── .claude-plugin/
│   └── marketplace.json              ← Marketplace catalog (required)
├── plugins/
│   └── youtube-plugin/               ← One folder per plugin
│       ├── .claude-plugin/
│       │   └── plugin.json           ← Plugin manifest (required)
│       ├── commands/                 ← Slash commands (.md files)
│       ├── skills/                   ← Background skills (subdirs with SKILL.md)
│       └── README.md
└── README.md
```

## marketplace.json Format

Located at `.claude-plugin/marketplace.json` in the repo root:

```json
{
  "name": "your-marketplace-name",
  "owner": {
    "name": "Your Name",
    "url": "https://yoursite.com"
  },
  "plugins": [
    {
      "name": "youtube",
      "source": "./plugins/youtube-plugin",
      "description": "Complete YouTube content creation suite"
    }
  ]
}
```

To add a new plugin: add an entry to the `plugins` array with `name` and `source`.

## plugin.json Manifest

Located at `<plugin-dir>/.claude-plugin/plugin.json`:

```json
{
  "name": "plugin-name",
  "version": "0.1.0",
  "description": "What this plugin does",
  "author": {
    "name": "Your Name",
    "url": "https://yoursite.com"
  }
}
```

- `name`: kebab-case (lowercase, hyphens only) — becomes the command namespace (e.g. `youtube` → `/youtube:script`)
- `version`: start at `0.1.0`, increment on updates

## Command Format

Commands live in `commands/*.md`. Each file = one slash command.

```markdown
---
description: Brief description of what this command does
argument-hint: [what to pass]
allowed-tools: Read
---

First, read the following context files from the project folder if they exist:
- USER.md
- BUSINESS.md
- ICP.md

Then read and follow the instructions in @${CLAUDE_PLUGIN_ROOT}/skills/<skill-name>/SKILL.md.

Do the task for: $ARGUMENTS

If no input is provided, ask the user before starting.
```

**Critical rules:**
- Commands are instructions FOR Claude — not documentation for the user
- `$ARGUMENTS` captures everything the user types after the command
- `@${CLAUDE_PLUGIN_ROOT}/skills/name/SKILL.md` = correct way to reference skill files
- `allowed-tools: Read` is needed to read project files and skill files
- Commands CANNOT "invoke" skills — skills auto-trigger from their description; commands contain the actual logic

## Skill Format (inside plugins)

Skills live in `skills/<skill-name>/SKILL.md`. They auto-trigger when Claude detects a matching request.

```markdown
---
name: skill-name
description: Trigger phrases that activate this skill. Be specific.
---

## Load Context First

Before executing this skill, read the following files from the project folder if they exist:

1. **USER.md** — who the user is, how they think, how they work
2. **BUSINESS.md** — their business, products, brand voice, content strategy, social links
3. **ICP.md** — their ideal customer, their language, their fears
4. **Voice or brand voice skill** — look for any installed skill related to voice, tone, or brand voice and apply it automatically
5. Any additional context provided by the user in this session

---

# Skill Name

[Full instructions for the skill]
```

**Critical rules:**
- NEVER hardcode specific skill names for voice (e.g. `voice-profile-alex`) — say "look for any voice or brand voice skill"
- NEVER reference voice.md as a file path — it's a globally installed skill, not a project file
- NEVER put creator-specific content (names, social links, file paths) in plugin skills intended for multiple users
- Skills shared publicly should pull all specifics from context files (USER.md, BUSINESS.md, ICP.md)

## Context File Rules

| File | Location | How to reference |
|------|----------|-----------------|
| USER.md | User's project folder | `Read USER.md` (relative, no path) |
| BUSINESS.md | User's project folder | `Read BUSINESS.md` (relative) |
| ICP.md | User's project folder | `Read ICP.md` (relative) |
| Voice skill | Globally installed | Auto-loaded — do NOT path-reference |
| Plugin skills | Inside plugin | `@${CLAUDE_PLUGIN_ROOT}/skills/name/SKILL.md` |

## Adding a New Plugin

1. Create the plugin directory in `~/repos/your-marketplace/plugins/`
2. Add `.claude-plugin/plugin.json`, `commands/`, `skills/`
3. Validate: `claude plugin validate plugins/<name>/.claude-plugin/plugin.json`
4. Add entry to `.claude-plugin/marketplace.json`
5. Commit and push — Claude Code/Cowork syncs on next marketplace update

## Deploying Updates

**Always bump the plugin version before committing any change to a plugin.** If you skip this, users running the plugin won't get the update — Claude Code and Cowork use the version number to decide whether to download a new copy.

Use semantic versioning — patch for small changes (0.1.0 → 0.1.1), minor for new skills or commands (0.1.0 → 0.2.0):

```bash
# Edit plugins/<name>/.claude-plugin/plugin.json — increment "version"
# Then commit everything together:
cd ~/repos/your-marketplace
git add -A
git commit -m "Description of change"
git push
```

Users update by syncing the marketplace in Claude Code or Cowork.

## Validation

Run before every push — required, not optional:

```bash
claude plugin validate plugins/<name>/.claude-plugin/plugin.json
```

Fix all errors and warnings before committing.

## What NOT to Do

- ❌ Don't try to package plugins as `.plugin` zip files for local upload — the zip format is broken/unsupported
- ❌ Don't "invoke" skills from commands — commands contain the logic directly
- ❌ Don't hardcode creator names, social links, or file paths in plugin skills meant for multiple users
- ❌ Don't reference `voice.md` as a project file — it's a globally installed skill
- ❌ Don't use `version: "1.0.0"` for new plugins — start at `0.1.0`
