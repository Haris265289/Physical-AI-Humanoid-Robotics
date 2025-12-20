# Data Model: ROS 2 Fundamentals Module

## Entity: TextbookModule

### Description
Represents a complete module within the AI-Native Textbook, containing multiple chapters focused on a specific topic.

### Fields
- **id** (string, required)
  - Unique identifier for the module (e.g., "01-ros2-fundamentals")
  - Format: {number}-{slug}
  - Used for navigation and content organization

- **title** (string, required)
  - Display title of the module (e.g., "Module 1: The Robotic Nervous System (ROS 2)")
  - Used in navigation and page titles

- **subtitle** (string, optional)
  - Additional descriptive text for the module
  - Provides context about the module's focus

- **description** (string, required)
  - Detailed explanation of what the module covers
  - Used in module overview pages

- **targetAudience** (string[], required)
  - Array of audience types (e.g., ["students", "developers"])
  - Guides content complexity and examples

- **duration** (number, optional)
  - Estimated time to complete the module in hours
  - Helps students plan their learning

- **learningObjectives** (string[], required)
  - Array of specific skills/knowledge students will gain
  - Aligned with functional requirements from spec

- **prerequisites** (string[], optional)
  - Knowledge/skills required before starting the module
  - Helps students assess readiness

- **chapters** (Chapter[], required)
  - Ordered list of chapters in the module
  - Defines the learning sequence

- **createdAt** (string, required)
  - ISO date string when module was created
  - Used for content tracking

- **updatedAt** (string, required)
  - ISO date string when module was last updated
  - Used for content freshness tracking

### Relationships
- Contains 1..n Chapter entities
- Connected to other modules through curriculum structure

---

## Entity: Chapter

### Description
Represents a single chapter within a textbook module, focusing on a specific aspect of the module's topic.

### Fields
- **id** (string, required)
  - Unique identifier within the module (e.g., "01-ros2-architecture")
  - Format: {number}-{slug}

- **title** (string, required)
  - Display title of the chapter
  - Used in navigation and page headers

- **order** (number, required)
  - Sequential position within the module (1, 2, 3, ...)
  - Determines reading sequence

- **contentPath** (string, required)
  - File path to the MDX content file
  - Relative to the docs directory

- **description** (string, required)
  - Brief summary of chapter content
  - Used in chapter listings

- **learningObjectives** (string[], required)
  - Specific skills/knowledge from this chapter
  - Aligned with functional requirements

- **estimatedTime** (number, optional)
  - Estimated reading and practice time in minutes
  - Helps students plan their study

- **sections** (Section[], required)
  - Ordered list of sections within the chapter
  - Defines content structure

- **examples** (Example[], optional)
  - Practical examples and code snippets
  - Reinforces learning concepts

- **exercises** (Exercise[], optional)
  - Practice problems for students
  - Tests understanding

- **createdAt** (string, required)
  - ISO date when chapter was created

- **updatedAt** (string, required)
  - ISO date when chapter was last updated

### Relationships
- Belongs to 1 TextbookModule entity
- Contains 1..n Section entities
- Contains 0..n Example entities
- Contains 0..n Exercise entities

---

## Entity: Section

### Description
A subsection within a chapter, typically representing a focused topic or concept.

### Fields
- **id** (string, required)
  - Unique identifier within the chapter
  - Format: {chapter-id}-{section-number}

- **title** (string, required)
  - Display title for the section
  - Used in table of contents and headings

- **order** (number, required)
  - Position within the chapter (1, 2, 3, ...)
  - Determines content flow

- **content** (string, required)
  - The actual content in MDX format
  - May include text, code, and React components

- **contentType** (enum, required)
  - Type: "text", "concept", "tutorial", "example", "exercise"
  - Helps with content styling and processing

- **difficulty** (enum, optional)
  - Level: "beginner", "intermediate", "advanced"
  - Guides student expectations

- **relatedSections** (string[], optional)
  - Array of IDs for related sections
  - Enables cross-referencing

- **learningOutcomes** (string[], required)
  - What student should understand after reading
  - Validates content effectiveness

- **createdAt** (string, required)
  - ISO date when section was created

- **updatedAt** (string, required)
  - ISO date when section was last updated

### Relationships
- Belongs to 1 Chapter entity
- May reference 0..n other Section entities

---

## Entity: Example

### Description
A practical code example or demonstration within a chapter or section.

### Fields
- **id** (string, required)
  - Unique identifier for the example
  - Format: {chapter-id}-{example-number}

- **title** (string, required)
  - Descriptive title for the example
  - Explains what the example demonstrates

- **description** (string, required)
  - Explanation of the example's purpose
  - Context for why this example matters

- **code** (string, required)
  - The actual code content
  - Properly formatted for syntax highlighting

- **language** (string, required)
  - Programming language identifier (e.g., "python", "xml", "bash")
  - Used for syntax highlighting

- **executable** (boolean, optional)
  - Whether the example can be run by students
  - Default: false

- **expectedOutput** (string, optional)
  - What the example should produce when run
  - Helps students verify their understanding

- **associatedSectionId** (string, required)
  - Links to the section containing this example
  - Maintains content relationships

- **difficulty** (enum, optional)
  - Level: "beginner", "intermediate", "advanced"

- **tags** (string[], optional)
  - Array of tags for categorization (e.g., ["node", "publisher", "service"])

- **createdAt** (string, required)
  - ISO date when example was created

- **updatedAt** (string, required)
  - ISO date when example was last updated

### Relationships
- Belongs to 1 Section entity
- May reference 0..n other Example entities

---

## Entity: Exercise

### Description
A practice problem or activity for students to test their understanding.

### Fields
- **id** (string, required)
  - Unique identifier for the exercise
  - Format: {chapter-id}-{exercise-number}

- **title** (string, required)
  - Descriptive title for the exercise

- **problemStatement** (string, required)
  - Clear description of what the student needs to do

- **instructions** (string, required)
  - Step-by-step guidance for completing the exercise

- **solution** (string, optional)
  - Reference solution (may be hidden initially)

- **difficulty** (enum, required)
  - Level: "beginner", "intermediate", "advanced"

- **estimatedTime** (number, optional)
  - Expected time to complete in minutes

- **associatedSectionId** (string, required)
  - Links to the section containing this exercise

- **hints** (string[], optional)
  - Guiding hints for students who get stuck

- **validationCriteria** (string[], required)
  - How to determine if the solution is correct

- **tags** (string[], optional)
  - Array of tags for categorization

- **createdAt** (string, required)
  - ISO date when exercise was created

- **updatedAt** (string, required)
  - ISO date when exercise was last updated

### Relationships
- Belongs to 1 Section entity
- May reference 0..n other Exercise entities

---

## Validation Rules

### TextbookModule Validation
- id must follow format: {number}-{slug}
- title must not exceed 100 characters
- learningObjectives must contain at least 3 items
- chapters array must not be empty
- duration must be greater than 0 if provided

### Chapter Validation
- id must follow format: {number}-{slug}
- order must be unique within the module
- sections array must not be empty
- contentPath must point to an existing MDX file

### Section Validation
- id must be unique within the chapter
- order must be unique within the chapter
- contentType must be one of the allowed enum values
- content must not be empty

### Example Validation
- id must be unique within the chapter
- language must be a recognized programming language
- executable examples must have expectedOutput

### Exercise Validation
- id must be unique within the chapter
- difficulty must be one of the allowed enum values
- problemStatement must not be empty
- validationCriteria must not be empty