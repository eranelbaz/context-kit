---
description: "Save a comprehensive context snapshot with a name for later retrieval"
---

First, get the current git branch name using `git branch --show-current`.

Ask me for a name for this context snapshot, suggesting the current git branch name as the default. Wait for my response before proceeding.

Once I provide a name, check if `.claude/contexts/<name>.md` already exists. If it does, tell me and ask whether to overwrite it or pick a different name. Wait for my response before proceeding.

If overwriting, first read the existing file so you can produce a "Changes Since Last Save" section.

Then review our entire conversation so far and produce a comprehensive context snapshot. Write it to `.claude/contexts/<name>.md`, creating the `.claude/contexts/` directory if it doesn't exist.

Use this exact structure:

---

# Context Snapshot: <name>
*Saved: [insert current date and time]*

## Changes Since Last Save
A concise bullet list of what is new or different compared to the previous snapshot — decisions made, progress on tasks, files added or changed, direction shifts, resolved questions, etc. If this is a new snapshot (not an overwrite), write "Initial save."

## Project Goals & Plan
Summarize the overall purpose of the project and any architecture, approach, or strategy we've discussed.

## Key Decisions Made
A bullet list of every significant decision reached during this session, with a brief note on the reasoning behind each one.

## Current Task & Next Steps
What we were actively working on when this snapshot was taken, followed by a clear numbered list of immediate next steps to continue the work.

## Relevant Files & Paths
A bullet list of every file or directory mentioned or modified, with a one-line description of its role.

## Context & Constraints
Any preferences, constraints, conventions, or other context established in this session that a fresh Claude instance would need to know to pick up seamlessly — coding style, naming conventions, things to avoid, environment details, etc.

---

After writing the file, confirm it was saved and tell me I can start a new session and begin with:
"Run `/load-context` to resume."
