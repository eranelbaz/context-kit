---
description: "Load a previously saved context snapshot and resume where you left off"
---

Check if the `.claude/contexts/` directory exists and list all `.md` files in it.

If the directory doesn't exist or is empty, stop and tell me: "No context snapshots found. Run `/save-context` first to create one."

Get the current git branch name using `git branch --show-current`. If a snapshot matching the current branch name exists, suggest it as the default choice.

If there is exactly one snapshot, load it automatically.

If there are multiple snapshots, list them with their names and last-saved dates, and ask me which one to load — with the current branch's snapshot highlighted as the suggested default.

Once a snapshot is selected, read the file and fully internalize everything in it — project goals, decisions, current task, next steps, relevant files, and any constraints or conventions. Do not summarize it back to me at length. Just confirm you've loaded it with a short 3-5 bullet recap of the most important things to know, then say you're ready to continue.
