# context-kit

Save and load named conversation context snapshots across Claude Code sessions. Never lose track of where you left off, or use snapshots to launch multiple conversations from a shared context.

## What it does

context-kit gives you two slash commands that persist your conversation state to named snapshot files so you can pick up exactly where you left off in a new session.

| Command | Description |
|---------|-------------|
| `/context-kit:save-context` | Snapshot the full conversation into a named file under `.claude/contexts/` |
| `/context-kit:load-context` | Load a saved snapshot and resume with a short recap |

## Install

```bash
claude plugin marketplace add eranelbaz/context-kit
claude plugin install context-kit
```

Or from inside Claude Code:

```
/plugin marketplace add eranelbaz/context-kit
/plugin install context-kit
```

## Usage

### Save your context

Run this whenever you reach a meaningful checkpoint — after planning, after a big decision, before switching tasks, or when wrapping up for the day:

```
/context-kit:save-context
```

Claude will suggest your current git branch as the default name and save the snapshot to `.claude/contexts/<name>.md`. You can accept the default or pick a different name. If a snapshot with that name already exists, it asks before overwriting and includes a "Changes Since Last Save" diff.

### Resume in a new session

Start a fresh Claude Code session and run:

```
/context-kit:load-context
```

If you have one snapshot, it loads automatically. If you have multiple, it lists them and asks which one to load. Claude gives you a short recap and you're ready to continue.

## How it works

Each snapshot is a structured markdown file containing:

- **Changes Since Last Save** — what's new since the last snapshot (on overwrites)
- **Project Goals & Plan** — what you're building and how
- **Key Decisions** — what was decided and why
- **Current Task & Next Steps** — where you are and what's next
- **Relevant Files & Paths** — everything touched or discussed
- **Context & Constraints** — coding style, conventions, things to avoid

The files are plain markdown, so you can read or edit them yourself.

## Parallel conversations

Save your planning context once, then spin up multiple Claude Code sessions that all start from the same snapshot:

```
# Session 1: plan the work
/context-kit:save-context

# Session 2, 3, 4: open new terminals and load the same context
/context-kit:load-context
```

Each session picks up the full picture — goals, decisions, constraints — so you can divide work across parallel conversations without re-explaining.

## Tip

Add `.claude/contexts/` to your `.gitignore` — these are working files, not something you'd typically commit.

```
echo ".claude/contexts/" >> .gitignore
```

## License

MIT
