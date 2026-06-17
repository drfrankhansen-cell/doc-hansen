---
name: understand-onboard
description: "Use when the user wants to generate onboarding documentation for a codebase. Triggers: '/understand-onboard', 'create onboarding guide', 'generate getting started guide', 'help new developers understand this project'."
---

# /understand-onboard

Generates comprehensive onboarding materials for new team members by analyzing a project's structured knowledge graph.

## Prerequisites

A knowledge graph must exist at `.understand-anything/knowledge-graph.json` (created via `/understand`).

## Key Workflow

1. **Verify the knowledge graph exists** — the source file must be present
2. **Extract project metadata** — gather name, description, languages, and frameworks
3. **Analyze architecture layers** — identify structural organization
4. **Review the guided tour** — locate the recommended learning sequence
5. **Identify key files** — focus on high-level structural nodes (files, configs, services) rather than granular code elements
6. **Spot complexity areas** — flag challenging sections for careful study
7. **Synthesize findings** — compile into organized sections:
   - Project overview
   - Architecture overview
   - Key concepts
   - Guided tour (step-by-step learning path)
   - File inventory
   - Risk/complexity areas
8. **Format and present** — deliver as readable markdown
9. **Enable persistence** — offer to save and commit the guide to the repository

## Graph Structure Elements Used

- **Nodes**: code (files, functions, classes), configuration, documentation, domain knowledge
- **Edges**: relationships like imports, dependencies, calls, configurations
- **Layers**: architectural divisions
- **Tours**: step-by-step learning paths

Prioritizes efficiency by using targeted searches rather than loading entire datasets into memory.
