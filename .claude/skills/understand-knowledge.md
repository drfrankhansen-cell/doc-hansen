---
name: understand-knowledge
description: "Use when the user wants to visualize a Karpathy-pattern LLM wiki as a knowledge graph. Triggers: '/understand-knowledge', 'visualize my wiki', 'map my knowledge base', 'graph my LLM wiki'."
---

# /understand-knowledge

Analyzes a Karpathy-pattern LLM wiki — a three-layer knowledge base with raw sources, wiki markdown files, and schema — to generate an interactive knowledge graph.

## Key Workflow

**Phase 1 (Detect):** Run `parse-knowledge-base.py` to identify the wiki structure and confirm it has `index.md`, wikilinks (`[[target]]` syntax), and related files.

**Phase 2 (Scan):** The detection script extracts article nodes, sources, topics, and wikilink edges into `scan-manifest.json`.

**Phase 3 (Analyze):** Dispatch `article-analyzer` subagents in batches of 10–15 articles to uncover implicit relationships and claims, writing results to `analysis-batch-{N}.json` files.

**Phase 4 (Merge):** Run `merge-knowledge-graph.py` to combine scan and analysis outputs, deduplicate entities, and build layers and tour steps from `index.md`.

**Phase 5 (Save):** Validate the assembled graph, save it to `knowledge-graph.json`, write metadata, clean up intermediates, and trigger the dashboard.

## Design Notes

- The parse script handles deterministic extraction (wikilinks, headings, categories)
- LLM agents focus on inference-based implicit knowledge
- Categories derive from `index.md` section headings, not filenames
- The graph uses `kind: "knowledge"` for force-directed layout in the dashboard

Works seamlessly with the `karpathy-llm-wiki` skill.
