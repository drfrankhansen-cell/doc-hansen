---
name: understand-explain
description: "Use when the user wants a deep explanation of a specific file, function, or class in the codebase. Triggers: '/understand-explain', 'explain this file', 'how does this function work', 'deep dive into X', 'what does src/auth/login.ts do'."
---

# /understand-explain

Provides deep-dive explanations of code components using the knowledge graph.

## Key Workflow

1. Verify `.understand-anything/knowledge-graph.json` exists
2. Locate the target node via grep (by file path or function name)
3. Find all connected edges (imports, calls, dependencies)
4. Read connected nodes to understand the component's relationships
5. Identify the architectural layer
6. Read the actual source file
7. Explain the component's role, structure, connections, and data flow

## Usage

Provide:
- A file path (e.g., `src/auth/login.ts`)
- A function reference (e.g., `src/auth/login.ts:verifyToken`)

The command searches the knowledge graph and delivers a thorough explanation covering:
- What the component does and why
- How it fits into the architecture
- What it depends on and what depends on it
- Data flow through the component
