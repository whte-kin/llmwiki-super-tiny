# LLMWiki Super Tiny

This is a super-tiny knowledge base starter pack made of five prompt Markdown files (in `prompt/`), plus this README as an operator guide.

It is not a program. Nothing needs to be run. There is no code, no backend, and no database.

The idea is simple: create a new project, drop the `prompt/` folder into it, then hand the prompt files to Cursor / Codex / Claude Code to initialize and maintain a local wiki for you.

Do not copy this `README.md` into the new project. It is only a guide for how to use the prompt files.

This project was inspired by Karpathy's llmwiki idea.
What you have here is a much lighter, smaller, and more immediately usable version of that general direction.

---

## Files

This starter pack contains exactly these six files (five prompts in `prompt/` + this README):

1. `prompt/01_INIT_KB_PROJECT.md`
2. `prompt/02_FORMAT_RULES.md`
3. `prompt/03_REPO_PROFILE_SETUP_PROMPT.md`
4. `prompt/04_RAW_TO_PAGE_PROMPT.md`
5. `prompt/05_QA_TO_OPS_PROMPT.md`
6. `README.md`

---

## What Each File Does

### `prompt/01_INIT_KB_PROJECT.md`

Bootstraps a new knowledge base project.

Give it to an agent when you want the agent to create:

- the folder structure
- the base Markdown files
- the initial template contents

This file is the project scaffold instruction.

### `prompt/02_FORMAT_RULES.md`

Defines the formatting rules for the knowledge base.

It covers:

- the required structure of `index.md`
- the rules for `pages/*.md`
- the fixed structure of `repo_profile.md`

This file is the formatting and structure guide.

### `prompt/03_REPO_PROFILE_SETUP_PROMPT.md`

Used to set up `repo_profile.md` through conversation.

Give it to an agent when you want the agent to:

- read the current `repo_profile.md`
- ask the user a few focused questions
- clarify scope, viewpoint, granularity, and boundaries
- produce a complete `repo_profile.md`

This file is the repository-profile setup prompt.

### `prompt/04_RAW_TO_PAGE_PROMPT.md`

Used when you have a new source document in `raw/` and want to turn it into a wiki-shaped page under `pages/`, or merge it into an existing page.

Give it to an agent when you want the agent to:

- read `repo_profile.md` and `prompt/02_FORMAT_RULES.md`
- use `index.md` to identify likely related pages first (progressive lookup)
- update or create `pages/*.md` based on the source content (do not preserve the source outline as the wiki outline)
- keep `index.md` in sync whenever pages are created, retitled, or materially restructured

This file is the raw-to-pages workflow prompt.

### `prompt/05_QA_TO_OPS_PROMPT.md`

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

For a new repo, the typical setup order is: `prompt/01_INIT_KB_PROJECT.md` → `prompt/02_FORMAT_RULES.md` → `prompt/03_REPO_PROFILE_SETUP_PROMPT.md`, then use the workflow prompts as needed (see the next section).

---

## How to Use These Prompts (in a knowledge-base repo)

This section is a practical “how to run the workflow” guide.

You typically do one of the following:

1. **Repo setup / reset**
   - Attach `prompt/01_INIT_KB_PROJECT.md` to an agent to scaffold the project structure and starter files.
2. **(Re)configure repository scope**
   - Attach `prompt/03_REPO_PROFILE_SETUP_PROMPT.md` and let the agent ask a few questions, then update `repo_profile.md`.
3. **Turn a raw source into a wiki page (or merge into an existing page)**
   - Attach the raw source file under `raw/` and attach `prompt/04_RAW_TO_PAGE_PROMPT.md`.
   - The agent should:
     - read `index.md` first to find likely related pages
     - only then open the relevant `pages/*.md`
     - update or create `pages/*.md`
     - update `index.md` whenever a page is created, retitled, or materially restructured
4. **Capture an important conversation into `ops/`**
   - At the end of a conversation, attach `prompt/05_QA_TO_OPS_PROMPT.md`.
   - The agent should write an `ops/` note and propose page changes, then wait for explicit approval before touching `pages/`.

Notes:

- This README is the place to document “how to use the prompts”. Avoid putting user-facing usage instructions inside the prompts themselves, as that can interfere with model behavior.
- Always keep `index.md` synced with `pages/` (new page, retitle, or major structural change).

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

**LLMWiki Super Tiny** is a five-prompt starter pack (plus a README guide) for building and maintaining a local wiki with an agent, without writing code or running a system.
