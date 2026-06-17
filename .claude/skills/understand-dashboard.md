---
name: understand-dashboard
description: "Use when the user wants to launch the interactive visual dashboard for their codebase knowledge graph. Triggers: '/understand-dashboard', 'open the dashboard', 'visualize the graph', 'show me the knowledge graph'."
---

# /understand-dashboard

Launches an interactive web dashboard to visualize a codebase's knowledge graph.

## Key Steps

1. **Locates the project**: Uses the provided path argument or current working directory
2. **Verifies the knowledge graph**: Checks for `.understand-anything/knowledge-graph.json`
3. **Finds dashboard code**: Searches multiple installation paths, prioritizing `${CLAUDE_PLUGIN_ROOT}/packages/dashboard/`
4. **Installs dependencies**: Runs `pnpm install` and builds the core package
5. **Starts dev server**: Launches Vite with the knowledge graph directory specified
6. **Captures access token**: Extracts the tokenized URL from server output
7. **Reports status**: Provides the full dashboard URL with token parameter

## Critical Detail

The dashboard requires an access token. **Always include the `?token=` parameter in the URL you share.** Without it, users encounter an access gate blocking the interface.

The server runs in the background and uses port 5173 by default, with automatic fallback to the next available port if needed.
