# Knowledge Base Format Rules

This document defines the required format for the three core file types in this knowledge base:

- `index.md`
- `pages/*.md`
- `repo_profile.md`

The goal is consistency, readability, and reliable agent maintenance.

## General Principles

1. This is a knowledge base, not a software project.
2. No executable code is needed.
3. Do not introduce extra data structures unless explicitly requested.
4. Keep pages clear, stable, and easy to extend.
5. Keep the index compact, information-dense, and easy to retrieve from.

---

## I. `index.md`

### Purpose

`index.md` is the page-level index of the knowledge base.

It is not meant to hold full content. Its job is to support:

- page discovery
- semantic recall
- routing future updates
- deciding where new material belongs

### Required Header

The file must begin with:

```md
# Index

This file records the current page index of the knowledge base.
```

### Entry Format

Each page entry may contain only two fields:

- `name`
- `description`

Use this format:

```md
- name: Probabilistic Modeling
  description: A page about probabilistic modeling in machine learning, explaining how distributions are used instead of point estimates to represent predictions and uncertainty. Covers motivation, probabilistic classification, probabilistic regression, uncertainty, and the philosophical shift in modeling.
```

### Rules for `name`

- `name` must match the page title.
- Each page must have exactly one unique `name`.
- Duplicate names are not allowed.
- Do not add explanatory suffixes unless they are part of the actual page title.

### Rules for `description`

Each `description` must include:

1. what the page is about
2. a short explanation of the topic
3. the page's main sections or major content blocks

### Length

- Keep it to 1 or 2 sentences.
- Do not make it too long.
- Do not turn it into a full summary.

### Style

- No promotional wording
- No vague filler
- Avoid phrases like "very important" unless they add real meaning
- Prefer retrieval-friendly wording
- If helpful, include common alternate wording or near-synonyms naturally

### When to Update the Index

You must update `index.md` whenever:

- a new page is created
- a page title changes
- a page's structure changes in a meaningful way
- a page gains a major new section

---

## II. `pages/*.md`

### Purpose

`pages/*.md` are the final user-facing objects in the knowledge base.

Each page should represent a distinct topic, such as:

- a concept
- a policy
- a process
- a method
- a technical subject

### Naming Rules

- One page per file
- The filename should closely match the page title
- Keep filenames stable
- Use `[[Page Name]]` for cross-page links

### Semi-Fixed Structure

Pages do not need to share an identical section structure.

They may behave more like wiki pages, with headings that fit the topic.

However, the following three sections are mandatory:

- `## Overview`
- `## Related Pages`
- `## Sources`

Recommended minimum structure:

```md
# <Page Title>

## Overview
One or two short paragraphs explaining the topic.

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

### Structure Rules

- The page title must be an H1.
- `Overview`, `Related Pages`, and `Sources` must be H2 headings.
- Other sections may be freely named and should also use H2 headings.
- Pages may add or remove sections depending on the topic.
- Not all pages need the same set of sections.

### Writing Rules

- Prioritize clarity over style
- Avoid vague summaries
- Avoid empty openings like "This page introduces..."
- Write reusable knowledge wherever possible
- For policy and process pages, prioritize rules and steps
- For concept pages, prioritize definition, core content, and related pages
- Let the structure grow naturally when needed; do not force every page into the same mold

### Linking Rules

- Prefer `[[Page Name]]` for internal links
- Avoid repeatedly mentioning existing pages as plain text without linking
- If a section clearly depends on another page, link it explicitly
- `[[Page Name]]` is allowed not only in `Related Pages`, but anywhere in the body

### When to Create a New Page

Create a new page only if all of the following are true:

1. the topic can stand on its own
2. the source material gives it meaningful coverage
3. it is likely to be referenced independently later

If it is only mentioned in passing, keep it inside an existing page instead.

### How to Update Existing Pages

When updating a page, prefer these kinds of changes:

- add core content
- add topic-specific sections
- add related-page links
- add sources

Do not rewrite the entire page style just because new material arrives, unless the page is already messy.

---

## III. `repo_profile.md`

### Purpose

`repo_profile.md` is the single source of rules for the knowledge base.

It defines:

- scope
- granularity
- primary viewpoint
- page-writing guidance
- what should be included
- what should be excluded

### Required Structure

`repo_profile.md` must always keep this exact section structure:

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

Do not rename these sections.

### Rules for `Status`

- Use `unconfigured` during setup.
- Change it to `configured` after the user confirms the profile.
- Do not use any other values.

### What Each Section Should Contain

#### `Repository Name`
The name of the knowledge base.

#### `Purpose`
Why this knowledge base exists.

#### `Domain`
The domain or subject area.

#### `Typical Source Materials`
The kinds of materials that usually get added.

#### `Primary Viewpoint`
The main angle of understanding, such as theoretical, practical, procedural, institutional, or engineering.

#### `Focus Level`
The preferred level of granularity, such as broad themes, mid-sized concepts, or finer details.

#### `In Scope`
What should be included.

#### `Out of Scope`
What should be excluded.

#### `External Concept Policy`
How boundary or external concepts should be handled.

#### `Extraction Guidance`
Special instructions for organizing material and writing pages.

#### `Notes`
Any additional guidance.

### Content Rules

- Use concise natural language
- Avoid prompt-engineering jargon
- Do not invent content the user did not state
- It is fine to leave uncertain sections blank
- It is better to omit than to guess

---

## IV. Maintenance Rules

Any agent maintaining this knowledge base must follow these rules:

1. Pages are the primary user-facing objects.
2. `index.md` must stay in sync with the pages.
3. `repo_profile.md` is the single rule source.
4. Do not introduce programs, databases, servers, or unnecessary complexity.
5. Do not casually rename or restructure required sections.
6. Do not turn the index into page content.
7. Do not let pages devolve into disorganized notes.
