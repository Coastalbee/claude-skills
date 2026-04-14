---
name: bz-paper-search
description: Semantic search and synthesis over the Project_Bz_PAPER OCR corpus (27,920 chunks, 103 works). Uses Honeycomb Haven RAG search server at port 8765. Triggers on "/bz-paper-search [query]", "search paper corpus", "find in bz papers", "search scanned books", "query honeycomb".
version: "1.0"
generated_from: "phase3-rag-pipeline :: 2026-04-10"
user-invocable: true
allowed-tools: Bash, Read
context: fork
---

## Step 0 — Runtime Configuration

RAG server: `http://localhost:8765`
API key env: `RAG_API_KEY` (value: `coastalbee2026`)
Collection: `bz_paper` | 27,920 chunks | 103 works
Embedding: `nomic-embed-text:latest` (768 dims, [Q] prefix for queries)
Synthesis: `llama3.1:8b` → `llama3.2:3b` fallback

---

## EXECUTE NOW

**Arguments: `$ARGUMENTS`**

Parse:
- Query string → what to search for
- `--type [book|magazine|misc|academic]` → filter by document_type
- `--cat [staging_category]` → filter by staging bucket (e.g. `2026`, `09-INBOX`, `10-Continued`)
- `--doc [document_id]` → search within a specific work only
- `--year [YYYY]` → filter by publication_year
- `--limit N` → number of results (default: 10, max: 100)
- `--conf F` → minimum OCR confidence 0.0–1.0 (default: 0.35)
- `--mode [search|synthesize|extract|works|chunks]` → operation mode (default: search)
- `--no-synth` → retrieve passages only, skip LLM synthesis

---

### Phase 1: Health Check

Before any query, verify the server is running:

```bash
curl -s http://localhost:8765/health
```

If `status != "ok"`:
- If `qdrant: false` → Qdrant Docker container may be stopped. Inform user: "Qdrant is not responding. Start with: `docker start qdrant`"
- If `ollama: false` → Ollama may be stopped. Inform user: "Ollama is not responding. Start with: `docker start ollama`"
- If server connection refused entirely → Start the search server:
  ```bash
  cd "Z:/Honeycomb Haven/FileOrgScripts" && RAG_API_KEY=coastalbee2026 uvicorn src.rag_search:app --host 0.0.0.0 --port 8765 &
  sleep 4
  ```

---

### Phase 2: Route by Mode

#### Mode: search (default)

Semantic search — returns ranked passages with metadata, no LLM synthesis.

Build the filter payload from arguments:
```bash
curl -s -X POST \
  -H "X-API-Key: coastalbee2026" \
  -H "Content-Type: application/json" \
  -d '{
    "query": "[QUERY]",
    "limit": [LIMIT],
    "min_confidence": [CONF],
    "document_type": [TYPE_OR_NULL],
    "staging_category": [CAT_OR_NULL],
    "document_id": [DOC_ID_OR_NULL],
    "publication_year": [YEAR_OR_NULL]
  }' \
  http://localhost:8765/search
```

Omit null fields from the JSON payload.

---

#### Mode: synthesize

Retrieve relevant passages AND synthesize an answer via local LLM. Takes 30–120s.

```bash
curl -s -X POST \
  -H "X-API-Key: coastalbee2026" \
  -H "Content-Type: application/json" \
  -d '{
    "query": "[QUERY]",
    "limit": [min(LIMIT, 10)],
    "min_confidence": [CONF],
    "document_type": [TYPE_OR_NULL],
    "staging_category": [CAT_OR_NULL],
    "document_id": [DOC_ID_OR_NULL]
  }' \
  http://localhost:8765/synthesize
```

Response includes `answer` (LLM text), `model` (which model was used), and `sources` (passages used).

---

#### Mode: extract

Raw passage extraction — similar to search but without scoring filter, ideal for pulling verbatim text from a specific work.

```bash
curl -s -X POST \
  -H "X-API-Key: coastalbee2026" \
  -H "Content-Type: application/json" \
  -d '{
    "query": "[QUERY]",
    "limit": [LIMIT],
    "min_confidence": [CONF],
    "document_id": [DOC_ID_OR_NULL]
  }' \
  http://localhost:8765/extract
```

---

#### Mode: works

Browse or search the catalog of indexed works.

List all works:
```bash
curl -s -H "X-API-Key: coastalbee2026" \
  "http://localhost:8765/works?limit=50"
```

Filter by type or staging category:
```bash
curl -s -H "X-API-Key: coastalbee2026" \
  "http://localhost:8765/works?document_type=[TYPE]&staging_category=[CAT]&limit=50"
```

Get detail for a specific work:
```bash
curl -s -H "X-API-Key: coastalbee2026" \
  "http://localhost:8765/works/[DOCUMENT_ID]"
```

---

#### Mode: chunks

Retrieve all chunks for a specific work in order. Use when you need full-text reconstruction of a document.

```bash
curl -s -H "X-API-Key: coastalbee2026" \
  "http://localhost:8765/document/[DOCUMENT_ID]/chunks?limit=100&offset=0"
```

Returns chunks ordered by `chunk_index` with `total`, `returned`, and pagination `offset`.

---

### Phase 3: Parse Response

For search/extract responses, extract:
- `total` — how many hits returned
- Each result: `score`, `document_id`, `work_title`, `section_heading`, `page_range`, `text`

For synthesize responses, extract:
- `answer` — the LLM-generated response
- `model` — which model was used (llama3.1:8b or llama3.2:3b)
- `sources` — list of passages used for synthesis

For works responses, extract the `works` array.

---

### Phase 4: Output

#### search / extract output:
```
BZ PAPER SEARCH: [query]
Mode: search | Filters: [active filters or "none"]
Results: N passages found

[1] [Work Title] — [document_id]
    Type: [document_type] | Cat: [staging_category] | Pages: [page_range]
    Section: [section_heading]
    Score: [score]
    ---
    [first 400 chars of text]

[2] ...

CORPUS STATS: 103 works | 27,920 chunks | nomic-embed-text:latest
```

#### synthesize output:
```
BZ PAPER SYNTHESIZE: [query]
Model: [model_used] | Sources: N passages

ANSWER:
[answer text]

SOURCES USED:
[1] [Work Title] p.[page_range] — [section_heading]
[2] ...

Note: Synthesis uses local LLM (no external API calls).
```

#### works output:
```
BZ PAPER CATALOG
Total works: [total] | Showing: [limit]

[document_id]  [work_title]  [document_type]  [staging_category]  [chunk_count] chunks
...
```

---

### Phase 5: Pipeline Hook

After returning results, offer:

```
-> Surface insights into vault? Run /surface on retrieved passages.
-> Find connections to existing notes? Run /connect [topic].
-> Need full-text reconstruction of a work? Use --mode chunks --doc [document_id].
-> Synthesize an answer? Re-run with --mode synthesize (adds ~60s for LLM).
-> Build an essay from these passages? Run /essay-seed [topic].
```

Do not auto-chain. The user decides what to do with retrieved passages.

---

## Corpus Reference

| Staging Category | Works | Notes |
|-----------------|-------|-------|
| (root) | 13 | BeachCombing, BZ old school, 100M Leads, encyclopedias, etc. |
| 09-INBOX | 52 | Mixed — guides, psychology, how-to, travel, humor |
| 10-Continued | 22 | Arts, crafts, gardening, hiking, coloring books |
| 2026 | 16 | Marketing textbook (IMC), International Business textbook, estate planning, etc. |

| Document Type | Count | Examples |
|--------------|-------|---------|
| book | 9 | IMC Case Book, International Business Textbook 2003, Bicyclists Guide |
| magazine | ~20 | BeachCombing, International Living, assorted monthly mags |
| misc | ~74 | Humor, old school work, digital marketing, 100M Leads |

Key document_ids:
- `beachcombing-magazine` — 1,257 chunks, BeachCombing sea glass magazine
- `2026__imc-case-book` — 282 chunks, IMC marketing case studies book
- `iritable-bowel-2023` — 189 chunks, Hill's International Business Textbook (misnamed)
- `2026__magazine-articles` — 197 chunks, Hill's International Business Textbook (misnamed)
- `international-living` — 83 chunks, International Living expat magazine
- `100mleads-alex-hormozi` — 281 chunks, Hormozi lead generation book

---

## Known Limitations

- `iritable-bowel-2023` and `2026__magazine-articles` are both Hill's International Business textbook (2003) — two separate scans. Payloads corrected to `work_title="International Business Textbook 2003"`, `document_type="book"`.
- BeachCombing Magazine physically contains the IMC Case Book PDF (pages 161–420+). The 130 shared chunks between `beachcombing-magazine` and `2026__imc-case-book` are IMC content that was accidentally included in BeachCombing's scan job.
- `vectors_count` in /stats shows 0 (Qdrant INT8 quantization behavior) — `points_count: 27,920` is the correct figure.
- `/document/{id}/chunks` fetches up to 1,000 chunks per request (works with up to 1,257 chunks total — BeachCombing is the largest at 1,257).
- OCR confidence for many scanned documents is 0.35–0.55 — this is expected for older scans. The `min_confidence` default (0.35) accepts all indexed chunks.
- Author field is null for most works — author backfill from title parsing is a pending enhancement.

---

## Quality Gates

- Always check /health before querying — if server is down, start it before proceeding
- Never modify any files in `Z:/Honeycomb Haven/Project_Bz_PAPER/` — that is the source corpus (read-only)
- Never call the Qdrant REST API directly — route everything through the FastAPI server at port 8765
- Synthesis requires Ollama to be running — if /synthesize fails with 503, check `ollama: false` in /health
- This is a READ-ONLY skill — no writes to Qdrant, SQLite, or any corpus files
