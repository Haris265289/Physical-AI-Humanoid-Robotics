<!-- SYNC IMPACT REPORT
Version change: 1.0.0 → 1.1.0
Modified principles: All principles updated to reflect AI-Native Textbook with RAG Chatbot project
Added sections: None
Removed sections: None
Templates requiring updates: ⚠ pending (.specify/templates/plan-template.md, .specify/templates/spec-template.md, .specify/templates/tasks-template.md)
Follow-up TODOs: None
-->

# AI-Native Textbook with RAG Chatbot Constitution

## Core Principles

### I. Spec-Driven Content Generation
Content must be created based on well-defined specifications using Spec-Kit Plus methodology. All textbook content follows a structured, testable approach where requirements are clearly defined before implementation.

### II. Technical Accuracy and Clarity
All content must be technically accurate, clearly explained, and verifiable. Claims must be supported by evidence or citations, with no hallucinated facts, APIs, or tools.

### III. Reproducibility and Determinism
All processes, especially the RAG system's embedding and indexing pipeline, must be deterministic and reproducible. This ensures consistent results across deployments and updates.

### IV. AI-Native Documentation Design
The textbook design embraces AI interaction patterns, with content structured to support RAG systems and AI comprehension while maintaining traditional readability.

### V. Constraint-Focused Development
Development must work within free-tier service limitations (OpenAI, Neon Postgres, Qdrant Cloud) without compromising core functionality.

### VI. Source Integrity
All content and code must be derived from verified sources with proper attribution. No fabricated information should be introduced into the textbook or supporting systems.

### VII. RAG System Fidelity
The RAG chatbot must strictly answer from indexed textbook content only, with proper citations to specific sections. No external knowledge or hallucinated responses are permitted.

## Additional Constraints

- Technology stack: Docusaurus for documentation, OpenAI Agents/ChatKit for chatbot, FastAPI for backend, Neon for metadata, Qdrant for vector storage
- Deployment: GitHub Pages for static content, with backend services hosted separately
- Content format: Docusaurus MDX with embedded interactive elements
- RAG requirements: Answers must strictly derive from indexed textbook content only, with section citations
- Performance: Response times under 3 seconds for chat queries
- Accuracy: All claims must be backed by textbook content; selected-text-only answers when possible

## Development Workflow

- Content development follows Spec-Kit Plus: spec → plan → tasks → implementation
- All content changes trigger RAG re-indexing
- Pull requests must verify both content accuracy and system functionality
- Testing includes both traditional validation and RAG functionality verification
- RAG accuracy testing ensures responses are properly sourced from textbook content

## Governance

This constitution governs all aspects of the AI-Native Textbook with RAG Chatbot development. All contributions must align with these principles, and any amendments require explicit approval and documentation.

**Version**: 1.1.0 | **Ratified**: 2025-12-17 | **Last Amended**: 2025-12-17
