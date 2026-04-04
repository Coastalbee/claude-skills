# Ecosystem Role: Dual-Remote Skills Library

## Identity
- **category**: B (reference + customization)
- **origin**: Coastalbee/claude-skills (my fork — push custom skills here)
- **upstream**: alirezarezvani/claude-skills (pull new community skills)
- **blueprint**: Not installed (reference library, CI managed by upstream)

## Access Pattern
All projects in the Coastalbee ecosystem SEARCH this library for pre-built skills.
The orchestra registry (Phase 2) indexes all skills by category for cross-project lookup.

## Inventory (as of install date)
| Category | Count | Notable |
|----------|-------|---------|
| agents | 11 | cs-* prefixed |
| business-growth | 6 | Customer success, sales |
| c-level-advisor | 34 | CEO, CTO, CFO advisory |
| commands | 21 | /changelog, /tdd, /prd |
| engineering | 31 | AgentHub, RAG, MCP, CI/CD |
| engineering-team | 49 | Fullstack, AI/ML, DevOps |
| finance | 4 | DCF, SaaS metrics |
| marketing-skill | 54 | SEO, content, demand gen |
| orchestration | 1 | Multi-agent |
| product-team | 17 | RICE, OKRs, UX research |
| project-management | 12 | Atlassian, Jira |
| ra-qm-team | 28 | ISO 13485, FDA, GDPR |

## Custom Skills
Add custom skills to `skills/custom/` directory to avoid merge conflicts with upstream.

## Sync with Upstream
```bash
git fetch upstream
git merge upstream/main
# Resolve any conflicts in custom/ if needed
git push origin main
```
