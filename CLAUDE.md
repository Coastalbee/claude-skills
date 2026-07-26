<!-- L3 | MAX: 150 lines | Scaffold: 2026-05-27 | Synced: 2026-07-26 -->
# claude-skills — Skill Reference Library

## Role in Ecosystem

Comprehensive skills library for Claude AI and Claude Code — 362+ production-ready skills across 18 domains. Reference repository: teams download and deploy skill packages into their own workflows. Also hosts Coastalbee custom skills under `skills/custom/` with `cb-` prefix.

## Quick Navigation

| Domain | Path | Contents |
|--------|------|----------|
| Engineering (Core) | `engineering-team/` | 26 skills + Playwright Pro + Self-Improving Agent |
| Engineering (POWERFUL) | `engineering/` | 30 advanced skills (AgentHub, RAG, MCP, CI/CD) |
| Product | `product-team/` | 13 product skills + Python tools |
| Marketing | `marketing-skill/` | 43 skills (7 pods) + Python tools |
| C-Level Advisory | `c-level-advisor/` | 28 skills (10 roles + orchestration) |
| Project Management | `project-management/` | 6 PM skills + Atlassian MCP |
| RA/QM Compliance | `ra-qm-team/` | 12 compliance skills (ISO 13485, MDR, FDA, GDPR) |
| Business & Growth | `business-growth/` | 4 skills + Python tools |
| Finance | `finance/` | 2 skills + Python tools |
| Custom (Coastalbee) | `skills/custom/` | cb- prefix skills from Skills Factory |
| Agents | `agents/` | 16 cs-* prefixed agents |
| Standards | `standards/` | Communication, quality, git, security standards |
| Templates | `templates/` | Reusable templates |

*(Table lists the domains present at the 2026-05-27 scaffold. Upstream has since added `business-operations/`, `commercial/`, `research/`, `research-ops/`, `markdown-html/`, and `compliance-os/` — see upstream's `CHANGELOG.md` for the full per-domain breakdown.)*

## Skill Package Structure

```
skill-name/
├── SKILL.md              ← master doc: YAML frontmatter + instructions + quality gates
├── scripts/              ← Python CLI tools (no ML/LLM calls)
├── references/           ← expert knowledge bases (.md)
└── assets/               ← user-facing templates
```

## Coastalbee Custom Skills (cb- prefix)

Custom skills built in Skills Factory are published here:
- Path: `skills/custom/cb-<skill-name>/`
- Available across all Claude Code sessions after restart
- `cb-` prefix indicates Coastalbee-ecosystem-specific skill

## Key Design Principles

1. Skills are self-contained packages — no dependencies between skills
2. Scripts use Python standard library — no ML/LLM calls (keeps skills portable)
3. Each skill must save 40%+ time and improve consistency 30%+
4. Documentation-driven: SKILL.md is the authoritative source per skill
5. Platform-specific guidance > generic advice

## Development Environment

No build system or test framework by design (portability). Python scripts are stdlib-only; if a script ever needs a dependency, keep it to `pip install <package>` at most and document it in that skill's SKILL.md. Validation = each script passing its own `--help`/`--sample` smoke test, plus `scripts/derive_counters.py --check` for doc/counter drift — there is nothing to `npm install` or `pytest` at the repo root.

## Repository Stats

Derived ground truth via `python scripts/derive_counters.py` (run `--check` to verify docs still match — upstream's own README/marketplace.json badges are currently stale against this):

- **452** skills across **20** domains
- **685** Python automation tools
- **759** reference guides
- **136** agents
- **116** slash commands
- **95** marketplace plugins on disk (**88** registered — 7-plugin registration gap, inherited from upstream)
- **Version**: v2.11.2 (synced from upstream 2026-07-26)

## Git Workflow

Branch strategy: `feature/ → dev → main` (PR only). Main requires PR approval.

Conventional commits: `feat(domain): description`, `fix(tool): description`, `docs(workflow): description`

> **⛔ HARD RULE (upstream) — PR TARGET IS ALWAYS `dev`, NEVER `main`.** Every PR must use `--base dev`; `main` only receives periodic `dev → main` promotion PRs from the upstream maintainer. Branch protection blocks direct pushes to `main`.

## Publishing Constraints (ClawHub, non-negotiable — upstream)

1. `cs-` prefix applies only on slug conflicts, only on the ClawHub registry — never rename repo folders/local skill names to match.
2. No paid/commercial API dependencies (free-tier or BYOK only).
3. Rate limit: 5 new skills/hour on ClawHub — use the drip timer for bulk publishes.
4. `plugin.json` must carry the required schema fields; only `source` and `attribution` are approved extensions, and all `skills` paths must be relative + `./`-prefixed (enforced by `scripts/check_plugin_json.py --all` in CI).
5. ClawHub package version must match the repo release version.

## Subdirectory CLAUDE.md → README.md

Subdirectory CLAUDE.md files in this repo have been renamed to README.md (prevents unintentional L3 loading in nested sessions). The root CLAUDE.md (this file) is the only active L3 context.

## Ecosystem Positioning

- **Used by**: all projects for pre-built skills
- **Extended by**: Skills Factory (`Z:\Projects\Claude Code Skills & Agents Factory\`)
- **Custom output**: `skills/custom/cb-*` — Coastalbee-specific skills
- **Registry**: `Z:\Projects\.orchestra\registry.json`
