# Data Model: AI-Robot Brain Module with NVIDIA Isaac

## Entity Definitions

### TextbookModule
- **name**: string (e.g., "Module 3: The AI-Robot Brain (NVIDIA Isaac)")
- **moduleId**: string (e.g., "03-ai-robot-brain")
- **title**: string (main title of the module)
- **description**: string (brief description)
- **chapters**: Chapter[] (ordered list of chapters in the module)

### Chapter
- **id**: string (unique identifier like "01-isaac-sim")
- **title**: string (chapter title)
- **contentPath**: string (path to MDX file)
- **order**: number (sequence in the module)
- **learningObjectives**: string[] (what students should learn)
- **prerequisites**: string[] (required knowledge)
- **sections**: Section[] (subsections of the chapter)

### Section
- **id**: string (unique identifier)
- **title**: string (section title)
- **content**: string (MDX content)
- **order**: number (sequence in the chapter)
- **examples**: Example[] (code or practical examples)

### Example
- **id**: string (unique identifier)
- **title**: string (example title)
- **description**: string (what the example demonstrates)
- **code**: string (the actual code/config)
- **language**: string (programming language or configuration format)
- **expectedOutcome**: string (what should happen when executed)

## Key Data Relationships

### Module-Chapters Relationship
- One TextbookModule contains multiple Chapters (1:M)
- Chapters are ordered within the module
- Each Chapter belongs to exactly one Module

### Chapter-Sections Relationship
- One Chapter contains multiple Sections (1:M)
- Sections are ordered within the chapter
- Each Section belongs to exactly one Chapter

### Chapter-Examples Relationship
- One Chapter can have multiple Examples (1:M)
- Examples support specific Sections within the Chapter
- Each Example demonstrates specific concepts from the Chapter

## Data Validation Rules

### Module Validation
- moduleId must follow format: "0[0-9]+-[a-z0-9-]+"
- name must be 10-100 characters
- title must be unique across all modules

### Chapter Validation
- id must be unique within the module
- contentPath must point to existing MDX file
- order must be sequential within the module (1, 2, 3...)

### Section Validation
- title must be 5-100 characters
- content must contain at least 100 words
- order must be sequential within the chapter

## State Transitions (if applicable)

### Chapter Completion States
- **DRAFT**: Initial state, content being developed
- **REVIEW**: Content complete, undergoing review
- **PUBLISHED**: Content approved and available to students
- **ARCHIVED**: Content deprecated but maintained for reference

## API Contract Considerations

### Content API Structure
```
{
  "id": string,
  "title": string,
  "module": string,
  "content": string,
  "sections": [
    {
      "id": string,
      "title": string,
      "content": string
    }
  ],
  "metadata": {
    "author": string,
    "lastUpdated": string,
    "tags": string[]
  }
}
```

This structure supports the RAG system indexing requirements while maintaining compatibility with Docusaurus documentation format.