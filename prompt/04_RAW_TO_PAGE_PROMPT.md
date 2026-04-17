# Raw → Wiki Page

Turn the provided raw source into wiki-shaped pages under `pages/`, merging into existing pages or appending subsections when appropriate, and keep `index.md` in sync.

Page format follows `prompt/02_FORMAT_RULES.md`.

If the user provides explicit routing directives (such as `MODE`, `TARGET_PAGE`, `SUBSECTION_TITLE`), follow them. Otherwise, infer routing from `index.md` and relevant pages.

---

## Files you must read first

In order:

1. `repo_profile.md`
2. `prompt/02_FORMAT_RULES.md`
3. The user's **full raw source** (grasp topic and keywords first)
4. `index.md` (see **Progressive lookup** below)
5. Only `pages/*.md` that the index or semantics suggests are **likely relevant** (do not read all of `pages/` by default)

---

## Progressive lookup (index first, then drill down)

Goal: read little, read the right things; avoid scanning every page upfront.

1. **Read `index.md` first**  
   From each entry's `name` and `description`, decide **which wiki pages might relate** to the raw topic, terms, and domain. List zero or more **candidate page titles** (matching `name`).

2. **Then read candidate `pages/` files**  
   Open only files that match those titles (filenames usually align with titles; if unsure, match `name` from the index to H1 or filename under `pages/`).  
   If that is still not enough to decide (e.g. check whether a subsection already exists), **incrementally** open adjacent pages—do not read every `pages/*.md` in one pass.

3. **No clear candidates**  
   If nothing in the index clearly matches, consider creating a new page; optionally skim **filenames only** under `pages/` (not full text) to avoid duplicate pages.

---

## Keeping `index.md` in sync (required)

Whenever this task **changes** or **adds** files under `pages/`, update `index.md` accordingly:

| Change | Requirement for `index.md` |
|--------|----------------------------|
| **New** wiki page | Add an entry: `name` = that page's H1; `description` per Index rules in `prompt/02_FORMAT_RULES.md` (1–2 sentences: topic + main blocks). |
| **Existing** page edited with **material** changes to topic, structure, or main sections | Update that entry's `description` (verify `name` still matches H1; if the user retitled the page, update `name`). |
| Typos/punctuation only, **no** topic or structure change | May skip `index.md` (if unsure, update `description` one line for retrieval accuracy). |

If one round both creates and edits multiple pages, **every** affected page must have a corresponding add or update in `index.md`.

---

## Content vs structure (important)

- **Use only the source's meaning and facts**; do not copy its section numbering or outline depth.
- **Wiki-shaped pages** require `## Overview`, `## Related Pages`, `## Sources`; add thematic `## …` sections as needed (see **Content Organization Rules** in `prompt/02_FORMAT_RULES.md`).
- In `## Sources`, list the raw path used (e.g. `raw/filename.md`).

---

## Routing (pick one and execute)

Before editing files, state your choice in one or two sentences:

| Situation | Action |
|-----------|--------|
| Same topic as an existing page; supplement or revise | **merge** into that page or into the right subsection |
| Clearly a **named** subtopic under a theme, not worth a new page | **subsection** (`TARGET_PAGE` + `SUBSECTION_TITLE`) |
| New topic; no good index entry | **new_page** + new `index.md` entry |
| Touches multiple pages | Use the **primary** page for merge/subsection; in `## Related Pages` link others with `[[Page Name]]` (only existing pages; do not invent pages) |

If **MODE** is **auto** and `TARGET_PAGE` is empty: match semantically using `index.md` `name` and `#` titles in `pages/`; if ambiguous, list 1–2 candidates in the reply and pick the best (prefer the user's open file or recently edited same-title topic).

---

## Checklist (self-check when done)

- [ ] Used progressive lookup: `index` then `pages`; did not read all pages without cause.
- [ ] Target `pages/` file: H1 title; all three required H2 sections present.
- [ ] If new: `index.md` has an entry; `name` **exactly** matches H1.
- [ ] If existing page materially changed: corresponding `index.md` entry updated (see above).
- [ ] If merge/subsection: no huge duplicate blocks; clear levels (avoid `## 1.` lecture-style numbering as the main skeleton).
- [ ] `## Sources` includes this raw reference.
- [ ] No unrelated executable code or config (unless `repo_profile` allows and the user asked).

---

## Short reply to the user

In a few sentences: which of **new / merge / subsection** you chose; which paths changed; **`index.md` adds or updates** (if any); which **index candidates** you used in progressive lookup.
