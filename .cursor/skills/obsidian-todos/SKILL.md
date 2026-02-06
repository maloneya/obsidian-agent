---
name: obsidian-todos
description: Capture and manage todos in the Obsidian vault. Use when the user gives a todo, task, action item, or asks to clean up, triage, or review their todo list.
---

# Todo Management

The user's todo system lives in `Todo.md` at the vault root. There are two core operations: **capture** and **clean up**.

## Todo.md Structure

```markdown
- [ ] exact user text `#project-name` — MM/DD
- [ ] exact user text `#project-name` — MM/DD

# Backlog

- [ ] item moved from active during cleanup
- [ ] older item

# Done

### MM/DD
- [x] completed item `#project-name` — MM/DD
```

Items at the top of the file (before any heading) are the active "must do today" list. No heading needed — they're just the first things you see. **Backlog** is a flat list. **Done** is grouped by date.

## Operation 1: Capture

When the user gives you a todo — explicitly or embedded in conversation:

1. **Write their exact words** as the task text. Do not rephrase, clean up, or editorialize.
2. **Guess the project** from context (current conversation topic, mentioned repos, existing projects in the backlog). Use a lowercase `#tag` inline: `#keybindings`, `#cloud-agents`, `#pq`, etc.
3. **Timestamp it** with current time in HH:MM format at the end of the line.
4. **Add to the top of the file** (active list) by default. If the user says it's not urgent or is a "someday" item, add to the Backlog section.

### Capture format

```markdown
- [ ] user's exact words `#project-tag` — MM/DD
```

### Example

User says: "oh remind me to review the keybinding PRs tomorrow"

```markdown
- [ ] review the keybinding PRs tomorrow `#keybindings` — 02/04
```

If no project is guessable, omit the tag. Don't force it.

### Linking to related notes

When a todo originates from or relates to a specific note in the vault, add a `→ [[Note Name]]` wikilink at the end of the line. This lets the user jump straight to context from the todo list.

```markdown
- [ ] dig into sentry scripts `#observability` — 02/04 → [[Reliability Observability]]
```

Only add links when there's a clear related note. Don't force it.

## Operation 2: Clean Up

Triggered when the user says "clean up todos", "triage", "rewrite my todos", or similar. This replaces the user's old habit of rewriting the file daily.

### Steps

1. **Read `Todo.md`** in full.
2. **Ask the user** to confirm what stays active. Present the current active list and ask:
   - Which of these are must-do today?
   - Any of these done?
3. **Move, don't delete.** Items leaving the active list go to Backlog as a flat list.
4. **Mark done items** with `[x]` and move them to the Done section with today's date.
5. **Rewrite the file** with the cleaned structure.

### Clean up rules

- **Never delete a todo.** Move to Backlog or Done.
- **Preserve the user's original text** on every item — don't reword tasks during cleanup.
- **Keep the active list short** — this is the "only what matters today" list.
- **Merge duplicate items** only if they're clearly the same task. When merging, keep the earlier timestamp and both project tags if different.
