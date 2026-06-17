---
name: understand
description: "Use when the user wants to analyze, visualize, or understand a codebase. Triggers: '/understand', 'analyze this codebase', 'create knowledge graph', 'map the architecture', 'scan the project'."
---

# /understand

Analyzes a codebase to generate an interactive knowledge graph (`knowledge-graph.json`) that visualizes architecture, components, and relationships through a dashboard interface.

## Command Options

- `--full` — Force complete rebuild
- `--auto-update` / `--no-auto-update` — Toggle automatic updates on commits
- `--review` — Run full LLM validation instead of deterministic checks
- `--language <lang>` — Generate content in specified language (ISO 639-1 or friendly names)
- Directory path argument to analyze a specific project

## Seven-Phase Analysis Pipeline

**Phase 1 — SCAN:** Discovers all project files, detects languages/frameworks, extracts metadata from README and package manifests.

**Phase 1.5 — BATCH:** Computes semantic groupings of files for efficient parallel analysis.

**Phase 2 — ANALYZE:** Dispatches up to 5 concurrent subagents analyzing file batches, producing GraphNode and GraphEdge objects. Merges results with deduplication and normalization.

**Phase 3 — ASSEMBLE REVIEW:** Validates the merged graph structure and cross-batch edge integrity.

**Phase 4 — ARCHITECTURE:** Identifies logical layers using language context and framework patterns; assigns nodes to layers.

**Phase 5 — TOUR:** Creates a guided learning path through the codebase starting from the entry point.

**Phase 6 — REVIEW:** Runs inline deterministic validation (or full LLM review with `--review`) to catch missing fields, dangling references, and orphaned nodes.

**Phase 7 — SAVE:** Writes final graph, generates fingerprint baselines for incremental updates, persists metadata, cleans intermediate files.

## Graph Structure

The knowledge graph contains 13 node types (file, function, class, module, concept, config, document, service, table, endpoint, pipeline, schema, resource) connected by 26 edge types organized into categories: structural, behavioral, data flow, dependencies, semantic, infrastructure, and schema/data.

## Incremental Updates

If the codebase hasn't changed since the last run, the tool offers three options: full rebuild, LLM review only, or skip. Changed files trigger selective re-analysis while preserving unchanged node references.

## Language & Localization

Supports 10+ languages via ISO codes or friendly names. Language preference is persisted in config to ensure consistency across incremental runs.

Output is saved to `.understand-anything/knowledge-graph.json`. Upon completion, automatically triggers `/understand-dashboard`.
