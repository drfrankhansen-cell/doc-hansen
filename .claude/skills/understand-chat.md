---
name: understand-chat
description: "Use when the user wants to ask questions about a codebase using its knowledge graph. Triggers: '/understand-chat', 'how does X work', 'what calls Y', 'explain the authentication flow', 'what depends on Z'."
---

# /understand-chat

Explore a codebase by querying its knowledge graph.

## Quick Start

1. **Verify the knowledge graph exists** at `.understand-anything/knowledge-graph.json` (run `/understand` first if it doesn't)
2. **Ask your question** with relevant keywords about the codebase
3. **The system will**:
   - Search node names, summaries, and tags for matches
   - Trace connections via edges (imports, calls, dependencies)
   - Identify relevant architectural layers
   - Provide context-specific answers

## Key Concepts

The knowledge graph contains **nodes** (code files, functions, classes, concepts, configs, endpoints, etc.) connected by **edges** (imports, calls, dependencies, etc.). This structure maps both code structure and conceptual relationships.

## Effective Queries

Ask about:
- Specific files, functions, or classes
- Features or architectural components
- How parts of the system connect
- Dependencies and data flows
- Domain concepts and their implementations

**Example**: "How does authentication work?" or "What calls the payment processor?"

The response will reference actual locations in your codebase with summaries and relationship paths.
