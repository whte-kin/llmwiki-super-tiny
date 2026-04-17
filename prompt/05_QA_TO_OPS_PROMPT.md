# Prompt for Converting a Conversation into `ops/`

Give this file directly to Cursor / Codex / Claude Code.

Use it at the end of an important conversation, before starting a fresh context.

Its purpose is to help the agent review the current knowledge base, decide whether the conversation should be preserved, write an `ops/` note, propose page changes, and wait for user approval before touching the actual pages.

---

## Your Role

You are maintaining a local knowledge base.

This is not a software task. Nothing needs to be run.

At the end of a conversation, your job is to:

1. inspect the current knowledge base
2. decide whether the conversation produced reusable knowledge
3. if so, write a note into `ops/`
4. preserve enough context for future work

---

## What You Must Read First

Before doing anything else, read:

- `repo_profile.md`
- `index.md`
- the most relevant pages under `pages/`

When working from `index.md`, narrow down to relevant pages progressively instead of reading everything blindly.

If needed, you may also read:

- previous notes in `ops/`

---

## Your Goal

You are responsible for a closed-loop workflow:

1. distill reusable knowledge from the conversation
2. generate an `ops/` document
3. return a page-change proposal to the user
4. wait for explicit user approval
5. only after approval, modify existing pages or create new ones
6. if the user revises the plan, regenerate both the `ops/` note and the page proposal
7. repeat until the user explicitly approves

In other words:

- `pages/` are the derived layer
- `ops/` is where the current conversation is first captured
- generate `ops/` and the page proposal first
- only edit `pages/` after user approval

---

## When to Write to `ops/`

Consider writing an `ops/` note if the conversation does any of the following:

1. establishes a new knowledge point
2. corrects an existing understanding
3. adds an important detail to an existing page
4. produces a policy, process, rule, principle, or judgment worth keeping
5. is explicitly marked by the user as worth preserving

If the conversation is just casual, repetitive, or too unstable to preserve, do not create an `ops/` note.

---

## What You Must Decide Before Writing `ops/`

Before generating an `ops/` note, determine:

1. which existing pages are related
2. whether the conversation mostly repeats what already exists
3. whether the material is strong enough to justify a new page
4. whether it should instead be treated as an update to an existing page

This decision must be based on:

- `index.md`
- the current content in `pages/`

---

## What You Must Generate

If the conversation is worth preserving, generate two things first:

1. one Markdown file inside `ops/`
2. one page proposal for the user to review

Suggested file naming pattern:

```text
ops/YYYY-MM-DD_<topic>.md
```

Example:

```text
ops/2026-04-16_saas_procurement_flow.md
```

---

## Required `ops/` Template

Every generated `ops/` note must use this structure:

```md
# <Topic>

## Time
<Current date or timestamp>

## Conversation Question
<What the user was trying to solve>

## Conclusion
<The stable conclusion reached in the conversation>

## Reusable Knowledge
- <Knowledge point 1>
- <Knowledge point 2>

## Related Pages
- <Existing page A>
- <Existing page B>

## Page Proposal
- update: <page to update>
- create: <page that may need to be created>
- ignore: <content that should stay out of the knowledge base>

## Notes
<Uncertainty, boundary conditions, or follow-up comments>
```

---

## Writing Rules

### 1. Distill the Conclusion

Do not dump the entire conversation into the note.

Capture the durable result.

### 2. Preserve the Original Problem

Make it clear what the user was actually trying to solve.

Without that, the note will be hard to interpret later.

### 3. Make `Reusable Knowledge` Reusable

Do not write conversational fragments.

Write statements that could later be folded into pages.

### 4. Ground `Related Pages` in the Existing Knowledge Base

Do not guess page links loosely.

Check:

- `index.md`
- relevant files in `pages/`

### 5. Do Not Execute the Page Proposal Yet

The proposal must be shown to the user first.

No page updates are allowed until the user explicitly approves.

---

## Required Page Proposal Format

After generating the `ops/` note, return a page proposal to the user using this structure:

```md
## Page Proposal

- ops file:
  - <path to the generated ops file>

- update:
  - <Page A>: <what should be added or changed>
  - <Page B>: <what should be added or changed>

- create:
  - <New Page A>: <why this deserves its own page>
  - <New Page B>: <why this deserves its own page>

- ignore:
  - <what should stay out of the knowledge base, and why>
```

Requirements:

- every `update` item must explain the intended change
- every `create` item must explain why it deserves a separate page
- `ignore` is optional, but if present it must explain the exclusion clearly
- never return only page names without reasoning

---

## Approval Rules

### 1. Never Edit Pages by Default

Once the `ops/` note and page proposal are ready, stop and wait.

Do not modify `pages/` yet.

Only proceed if the user clearly says something equivalent to:

- approved
- go ahead
- apply this
- update it that way
- create those pages

### 2. If the User Rejects or Adjusts the Proposal

If the user says things like:

- do not change that page
- add one more page to the proposal
- do not create that page
- revise the conclusion
- include this additional point

then you must not edit the pages yet.

Instead, you must:

1. reconsider the conversation outcome
2. regenerate the `ops/` note
3. regenerate the page proposal
4. return the revised version for approval

### 3. Only the Final Approved Version May Be Executed

Only after explicit approval may you:

- update existing pages
- create new pages
- update `index.md`

---

## What to Do After Approval

Once the user approves the current proposal, move to execution and do the following:

1. update or create the pages listed in the approved proposal
2. follow the rules in `prompt/02_FORMAT_RULES.md`
3. update `index.md` accordingly
4. return a concise summary of the actual changes made

During execution:

- page structures may vary by topic, but `Overview`, `Related Pages`, and `Sources` are required
- `[[Page Name]]` links may appear both in `Related Pages` and in the main body
- do not write any proposal that was not explicitly approved

---

## When to Suggest `create`

Use `create` only if all of the following are true:

1. the topic is clearly independent
2. it can be explained on its own
3. it is likely to be referenced separately later

Otherwise, prefer `update`.

---

## If the Conversation Is Not Worth Preserving

If the conversation did not produce stable knowledge, do not force an `ops/` note.

Instead, say clearly:

- there is no stable knowledge worth preserving from this conversation
- no `ops/` note will be created
- why

---

## What You Must Report

### Case 1: An `ops/` Note Was Generated but Not Yet Approved

Report:

1. which `ops/` file was created
2. which existing pages are related
3. the current `update` proposals
4. the current `create` proposals
5. anything placed under `ignore`
6. that no page has been modified yet because approval is still pending

### Case 2: The User Approved and Execution Was Completed

Report:

1. which approved `ops/` version was used
2. which pages were updated
3. which new pages were created
4. what changed in `index.md`
5. the core knowledge that was added or corrected

### Case 3: No `ops/` Note Was Generated

If nothing was generated, explain why.

---

## Suggested Workflow

Follow this order:

1. read `repo_profile.md`
2. read `index.md`
3. inspect the most relevant pages
4. review the conversation outcome
5. decide whether it is worth preserving
6. if yes, generate the `ops/` note
7. generate the page proposal
8. return both for approval
9. if the user revises the plan, go back and regenerate
10. if the user approves, update `pages/` and `index.md`
11. return the execution summary

---

## Suggested Opening

When the user drops this file into the conversation, you may begin like this:

> I’ll first review `repo_profile.md`, `index.md`, and the most relevant pages.  
> Then I’ll decide whether this conversation should be preserved in `ops/`.  
> If so, I’ll generate an `ops/` note and a page proposal for your review.  
> I won’t modify any pages until you explicitly approve the proposal.

---

## End Goal

The goal is for every important conversation to end with:

- a structured record when appropriate
- clear connections to the existing knowledge base
- an explicit, reviewable page proposal
- page edits only after approval
- a repeatable loop for revising the proposal until the user agrees
