# World models and document agents

The survey uses “document world model” as a forward-looking design lens rather than as a single established model class. The aim is to connect document parsing with state estimation, prediction, planning, and verification.

## State representation

A document state can be represented as a typed graph or structured object:

```text
Document
├── Page(s)
│   ├── Region: text | title | table | figure | formula | header | footer
│   ├── Geometry: box, reading order, containment, adjacency
│   └── Content: tokens, pixels, markup, confidence
├── Cross-page entities and references
├── Document-level intent and task state
└── Evidence links and unresolved uncertainty
```

## Agent loop

1. Observe the page, metadata, or retrieval result.
2. Construct or update the structured state.
3. Predict missing relations or identify contradictions.
4. Select a tool: crop/zoom, OCR, layout detector, renderer, retriever, calculator, or verifier.
5. Execute the tool and attach evidence to the state.
6. Answer, revise, abstain, or request human verification.

## Research questions

- Can a parser preserve uncertainty instead of forcing a single serialization?
- Can a world model predict document structure before high-resolution recognition?
- How should an agent trade token budget against evidence completeness?
- What constitutes a grounded action when the target is a table cell, formula, or cross-page reference?
- How can state updates be audited and replayed?

## Evaluation boundary

Agentic document systems should be evaluated separately for perception, state consistency, tool selection, evidence grounding, and final task success. A fluent final answer is not evidence that the internal document state is correct.
