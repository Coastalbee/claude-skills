---
description: Generate ecosystem status report and optionally archive finished artifacts to .orchestra/archive/
---

# cb-dashboard

## Triggers
- `/cb-dashboard` — generate status report
- `/cb-dashboard --archive` — generate report + archive new finished work
- `/cb-dashboard --json` — output raw JSON instead of markdown

## What It Does

1. **Aggregates state** from all ecosystem projects:
   - Ars-Contexta: note count, edge count, essay seeds, incoming queue
   - CAL: asset count, L2 enrichment progress
   - RAG Pipeline: works indexed, chunks, API health
   - Honeycomb Haven: files organized, upload status
   - substack2md: articles scraped, publications mapped
   - 00-writer: drafts count, active ICP, voice profile
   - Personal.ai: memories imported (if applicable)

2. **Writes status report** to `.orchestra/status/ecosystem-status.md`

3. **If --archive flag**: Copies newly finished artifacts to `.orchestra/archive/` and updates `archive/index.json`

## Output Location
`.orchestra/status/ecosystem-status.md`

## Report Structure
```
# Ecosystem Status — {timestamp}

## Pipeline Health
| Stage | Count | Δ Last Run | Bottleneck? |
|-------|-------|------------|-------------|

## RAG Pipeline
- Works indexed: ...
- Chunks: ...
- API health: ...

## Archive Summary
| Category | Artifacts | Last Updated |

## Recent Activity
- Last synthesis batch: ...
- Last enrichment run: ...

## Bottlenecks & Alerts
- ...
```

## Archive Behavior (--archive flag)
Copies artifacts matching these criteria:
- Ars-Contexta notes with `status: verified` → `archive/synthesis/`
- CAL assets with `level_2` block → `archive/assets/`
- RAG `/synthesize` responses → `archive/rag-outputs/`
- Essays with `status: published` → `archive/essays/`

Updates `archive/index.json` with metadata for each archived artifact.

## Data Sources Read
| Project | Files Read |
|---------|------------|
| Ars-Contexta | `notes/*.md`, `incoming/*.md`, `essay-seeds/*.md` |
| CAL | `ASSET_INDEX.json` |
| RAG Pipeline | `rag_state.db`, Qdrant stats via API |
| Honeycomb Haven | CSV logs in staging directory |
| substack2md | `config.yaml`, vault file counts |
| 00-writer | `context/drafts/`, `context/ICP/` |

## Prerequisites
- Must be run from `.orchestra` directory OR pass `--root Z:\Projects\.orchestra`
- RAG API must be running for RAG stats (graceful skip if unavailable)

## Example Usage
```bash
# From .orchestra directory
/cb-dashboard

# With archiving
/cb-dashboard --archive

# JSON output for programmatic use
/cb-dashboard --json > status.json
```

## Related Skills
- `/cb-archive` — manual archive single artifact (planned)
- `/cb-search` — search archive by metadata (planned)
