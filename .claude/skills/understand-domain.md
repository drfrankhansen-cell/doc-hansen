---
name: understand-domain
description: "Use when the user wants to extract business domain knowledge from a codebase. Triggers: '/understand-domain', 'map the business logic', 'show domain model', 'extract domain concepts', 'how does the business logic work'."
---

# /understand-domain

Extracts business domain knowledge from codebases and generates interactive flow graphs for visualization.

## Key Workflow

**Phase 0** establishes the project root, handling git worktree redirects to preserve output in the main repository rather than ephemeral worktree checkouts.

**Phase 1** checks whether a knowledge graph already exists. If found and the `--full` flag wasn't used, it skips to derivation; otherwise proceeds with scanning.

**Phase 2** performs lightweight preprocessing via Python script, producing file trees, entry point detection, and file signatures — raw material for subsequent analysis without expensive file scanning.

**Phase 3** derives domain data from existing knowledge graphs, formatting nodes, edges, and layers as structured context.

**Phase 4** dispatches a domain-analyzer subagent that processes the gathered context and outputs domain analysis to an intermediate file.

**Phase 5** validates the analysis output and saves it to the domain graph file, with error tolerance allowing partial saves.

**Phase 6** triggers the dashboard to visualize the generated domain graph.

## Options

- `--full` — Force rescan even if a knowledge graph already exists

## Notable Features

- Works standalone or leverages existing knowledge graphs for efficiency
- Respects `.gitignore` during file enumeration
- Handles git worktrees by redirecting output to prevent data loss
