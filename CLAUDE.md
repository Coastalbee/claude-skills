<!-- L3 | MAX: 150 lines | Scaffold: 2026-05-27 -->
# claude-skills — Skill Reference Library

## Role in Ecosystem

Comprehensive skills library for Claude AI and Claude Code — 268+ production-ready skills across 9 domains. Reference repository: teams download and deploy skill packages into their own workflows. Also hosts Coastalbee custom skills under `skills/custom/` with `cb-` prefix.

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

## Repository Stats

- **205** production-ready skills
- **268** Python automation tools (all verified `--help` passing)
- **384** reference guides
- **16** agents
- **19** slash commands
- **Version**: v2.1.2

## Git Workflow

Branch strategy: `feature/ → dev → main` (PR only). Main requires PR approval.

Conventional commits: `feat(domain): description`, `fix(tool): description`, `docs(workflow): description`

## Subdirectory CLAUDE.md → README.md

Subdirectory CLAUDE.md files in this repo have been renamed to README.md (prevents unintentional L3 loading in nested sessions). The root CLAUDE.md (this file) is the only active L3 context.

## Ecosystem Positioning

- **Used by**: all projects for pre-built skills
- **Extended by**: Skills Factory (`Z:\Projects\Claude Code Skills & Agents Factory\`)
- **Custom output**: `skills/custom/cb-*` — Coastalbee-specific skills
- **Registry**: `Z:\Projects\.orchestra\registry.json`
