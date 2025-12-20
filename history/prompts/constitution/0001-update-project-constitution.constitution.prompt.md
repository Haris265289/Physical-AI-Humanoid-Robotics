---
id: 1
title: "Update Project Constitution"
stage: constitution
date_iso: 2025-12-17
surface: agent
model: claude-sonnet-4-5-20250929
feature: "none"
branch: master
user: unknown
command: /sp.constitution
labels: ["constitution", "project-setup", "spec-driven"]
links:
  spec: null
  ticket: null
  adr: null
  pr: null
files_yaml:
  - ".specify/memory/constitution.md"
tests_yaml:
  - "none"
---

# PHR-0001: Update Project Constitution

## Prompt Text

```
/sp.constitution

Project: AI-Native Textbook with RAG Chatbot

Purpose:
Build a spec-driven textbook using Spec-Kit Plus and Claude Code, published with
Docusaurus on GitHub Pages, with an embedded RAG chatbot that answers only from book content.

Principles:
- Spec-driven
- Accurate and clear
- Reproducible

Standards:
- Format: Docusaurus MDX
- Source-backed claims only
- No hallucinations

RAG:
- Embedded chatbot
- Stack: OpenAI Agents/ChatKit, FastAPI, Neon, Qdrant (free tier)
- Content-only + selected-text-only answers
- Cite sections

Success:
- Build and deploy pass
- Accurate RAG answers
- Spec-Kit Plus validation passes
- Book builds successfully with Docusaurus
```

## Response Text

Updated the project constitution to reflect the AI-Native Textbook with RAG Chatbot project, changing the title, adding a RAG System Fidelity principle, and updating technology stack and constraints to match the specified requirements.

## Outcome Impact

Successfully updated the project constitution file (.specify/memory/constitution.md) to align with the AI-Native Textbook with RAG Chatbot project goals, including specific requirements for RAG functionality, technology stack, and content accuracy.

## Tests Summary

none

## Files Summary

- .specify/memory/constitution.md: Updated project constitution with new principles and constraints

## Next Prompts

- /sp.specify to create the initial feature specification
- /sp.plan to develop the architectural plan
- /sp.tasks to generate implementation tasks

## Reflection Note

The constitution update successfully transformed the original "Physical AI & Humanoid Robotics" project into the "AI-Native Textbook with RAG Chatbot" project, preserving core Spec-Kit Plus methodology while adapting to the new domain and requirements.

## Failure Modes Observed

None

## Next Experiment to Improve Prompt Quality

N/A
