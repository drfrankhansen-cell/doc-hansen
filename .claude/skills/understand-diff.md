---
name: understand-diff
description: "Use when the user wants to analyze the impact of code changes or a pull request. Triggers: '/understand-diff', 'what does this PR affect', 'analyze the diff', 'blast radius of this change', 'what breaks if I change X'."
---

# /understand-diff

Analyzes git diffs and pull requests by cross-referencing changes against a knowledge graph.

## Prerequisites

A knowledge graph must exist at `.understand-anything/knowledge-graph.json` (created via `/understand`).

## Core Steps

1. Identify changed files using `git diff` commands
2. Extract project metadata from the knowledge graph
3. Locate nodes matching each changed file path
4. Map connected edges (1-hop) to find upstream callers and downstream dependencies
5. Identify affected architectural layers
6. Generate structured analysis with risk assessment

## Output Structure

The analysis covers:
- **Changed Components** — directly modified code with summaries
- **Affected Components** — downstream and upstream dependencies that may be impacted
- **Affected Layers** — which architectural layers are involved and cross-layer concerns
- **Risk Assessment** — based on node complexity, edge count, and blast radius

## Dashboard Integration

After analysis, writes `.understand-anything/diff-overlay.json` containing:
- Changed file paths
- Node IDs for modified and affected components
- Generation timestamp and base branch reference

Run `/understand-dashboard` afterwards to visualize the diff overlay.
