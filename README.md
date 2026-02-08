# Obsidian Notes Vault

This is a personal Obsidian vault managed collaboratively with a Cursor AI agent. The agent acts as the note-taker — you talk, it writes.

## How it works

The `.cursor/` directory contains rules and skills that teach the agent how to manage this vault.

### Rules (`.cursor/rules/`)

Rules are conventions the agent always follows when working with specific files. They enforce consistency so you don't have to think about formatting.

- **note-taker** — core principle: the agent writes the notes, not you
- **fix-spelling** — auto-corrects typos when capturing your words
- **log-notes** — naming and structure conventions for `Log/` (date-prefixed, time-oriented notes)
- **reference-notes** — naming and structure conventions for `Reference/` (evergreen, living docs)

### Skills (`.cursor/skills/`)

Skills are workflows the agent can execute when you ask for them. They define multi-step processes with specific rules for each.

- **obsidian-todos** — capture tasks and triage/clean up `Todo.md`
- **obsidian-ideas** — capture ideas and groom `Ideas.md`
- **obsidian-inbox** — triage `Inbox.md` items you captured offline into the right destinations
- **obsidian-vault** — general Obsidian formatting and linking conventions

## Vault structure

```
├── Inbox.md        # Offline capture scratchpad — you write, agent triages
├── Todo.md         # Active tasks, backlog, and done items
├── Ideas.md        # Product and project ideas organized by theme
├── Log/            # Time-oriented notes (meetings, investigations, one-off thoughts)
├── Reference/      # Evergreen docs that are continuously updated
```
