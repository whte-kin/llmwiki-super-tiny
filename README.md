# LLMWiki Super Tiny

This is a super-tiny knowledge base starter pack made of just five Markdown files.

It is not a program. Nothing needs to be run. There is no code, no backend, and no database.

The idea is simple: drop these five files into a new project, hand them to Cursor / Codex / Claude Code, and let the agent initialize and maintain a local wiki for you.

This project was inspired by Karpathy's llmwiki idea.
What you have here is a much lighter, smaller, and more immediately usable version of that general direction.

Recommended project names:

- `LLMWiki Super Tiny`
- `Super-Tiny LLMWiki`
- `llmwiki-super-tiny`

---

## Files

This starter pack contains exactly these five files:

1. `01_INIT_KB_PROJECT.md`
2. `02_FORMAT_RULES.md`
3. `03_REPO_PROFILE_SETUP_PROMPT.md`
4. `04_QA_TO_OPS_PROMPT.md`
5. `README.md`

---

## What Each File Does

### `01_INIT_KB_PROJECT.md`

Bootstraps a new knowledge base project.

Give it to an agent when you want the agent to create:

- the folder structure
- the base Markdown files
- the initial template contents

This file is the project scaffold instruction.

### `02_FORMAT_RULES.md`

Defines the formatting rules for the knowledge base.

It covers:

- the required structure of `index.md`
- the rules for `pages/*.md`
- the fixed structure of `repo_profile.md`

This file is the formatting and structure guide.

### `03_REPO_PROFILE_SETUP_PROMPT.md`

Used to set up `repo_profile.md` through conversation.

Give it to an agent when you want the agent to:

- read the current `repo_profile.md`
- ask the user a few focused questions
- clarify scope, viewpoint, granularity, and boundaries
- produce a complete `repo_profile.md`

This file is the repository-profile setup prompt.

### `04_QA_TO_OPS_PROMPT.md`

Used after an important conversation ends.

Give it to an agent when you want the agent to:

- read `repo_profile.md`
- read `index.md`
- inspect relevant pages in `pages/`
- decide whether the conversation is worth preserving
- generate an `ops/` note
- propose page updates or new pages
- wait for user approval
- only then update `pages/` and `index.md`

This file is the conversation-to-ops workflow prompt.

---

## Recommended Order

Use the files in this order:

1. Put these five files into a new directory.
2. Use `01_INIT_KB_PROJECT.md` to create the knowledge base folders and starter files.
3. Use `02_FORMAT_RULES.md` to enforce consistent structure.
4. Use `03_REPO_PROFILE_SETUP_PROMPT.md` to configure `repo_profile.md`.
5. After meaningful conversations, use `04_QA_TO_OPS_PROMPT.md` to capture them into `ops/`.

---

## What This Pack Is For

This pack is not about building software. It is about making a local wiki maintainable with the help of an agent.

It helps with:

- creating a local knowledge base with as few files as possible
- keeping the structure consistent
- growing the wiki through conversations
- maintaining pages without writing code

---

## Good Fit For

- personal knowledge bases
- study notes
- policy and process documentation
- technical documentation
- local wikis maintained with long-term agent assistance

---

## What It Does Not Include

This starter pack does not include:

- executable programs
- a CLI
- a backend service
- a database
- a graph engine
- a search engine

Those are intentionally out of scope for this super-tiny version.

---

## In One Sentence

**LLMWiki Super Tiny** is a five-file starter pack for building and maintaining a local wiki with an agent, without writing code or running a system.
