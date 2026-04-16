# Initialize the Knowledge Base Project

Follow this file exactly.

Do not explain the design. Do not invent extra structure. Only create the directories and files listed below, and write the exact starter content requested for each file.

## Directory Structure

```text
<project_root>/
  raw/
  ops/
  pages/
  tmp/
  repo_profile.md
  index.md
  README.md
```

## Required Files and Contents

### 1. `README.md`

Write the following content:

```md
# Local Wiki

This is a local knowledge base project.

## Structure

- `raw/`: source materials
- `ops/`: conversation logs and conversation-derived knowledge notes
- `pages/`: wiki pages
- `tmp/`: temporary files
- `repo_profile.md`: repository rules
- `index.md`: page index

## Workflow

1. Put source materials into `raw/`
2. Save reusable conversation outcomes into `ops/`
3. Maintain wiki pages using `repo_profile.md`, `index.md`, and `pages/`
```

### 2. `repo_profile.md`

Write the following content:

```md
# Repository Profile

## Status
unconfigured

## Repository Name

## Purpose

## Domain

## Typical Source Materials

## Primary Viewpoint

## Focus Level

## In Scope

## Out of Scope

## External Concept Policy

## Extraction Guidance

## Notes
```

### 3. `index.md`

Write the following content:

```md
# Index

This file records the current page index of the knowledge base.

Each entry may contain only two fields:
- `name`
- `description`

Example:

- name: Sample Page
  description: A sample page about a topic, with a short explanation and a summary of the page's main sections.
```

### 4. `pages/_PAGE_TEMPLATE.md`

Write the following content:

```md
# <Page Title>

## Overview
One or two short paragraphs explaining what this page is about.

## Other Sections
Add sections as needed, for example:
- History
- Core Concepts
- Key Rules
- Typical Workflow
- Use Cases
- Common Questions

## Related Pages
- [[Related Page A]]
- [[Related Page B]]

## Sources
- Source document 1
- Source document 2
```

### 5. `ops/README.md`

Write the following content:

```md
# ops

This directory stores:

- conversation logs
- conversation-derived knowledge notes
- page suggestion drafts

After any important conversation, the distilled result may be saved here.
```

### 6. `ops/_QA_TEMPLATE.md`

Write the following content:

```md
# <Conversation Topic>

## Time

## Question

## Answer

## Reusable Knowledge
- 

## Related Pages
- 

## Suggested Next Actions
- create a new page or not
- update an existing page or not
- ignore or not
```

## Constraints

- Do not create executable code files.
- Do not create Python, JavaScript, config scripts, or database files.
- Do not create extra directories.
- Only create the directories and Markdown files listed above.

## Execution Order

1. Create the directory structure.
2. Create `README.md`.
3. Create `repo_profile.md`.
4. Create `index.md`.
5. Create `pages/_PAGE_TEMPLATE.md`.
6. Create `ops/README.md`.
7. Create `ops/_QA_TEMPLATE.md`.
8. Confirm that all files contain the requested starter content.

## Final Report

When finished, report only:

- which folders were created
- which Markdown files were created
