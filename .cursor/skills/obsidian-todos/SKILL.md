---
name: obsidian-todos
description: Capture and manage todos in the Obsidian vault. Use when the user gives a todo, task, action item, or asks to clean up, triage, or review their todo list.
---

# Todo Management

The user's todo system lives in `Todo.md` at the vault root. There are two core operations: **capture** and **clean up**.

## Todo.md Structure

```markdown
---
date: YYYY-MM-DD
---

# Today

- [ ] exact user text `#project-name` — HH:MM
- [ ] exact user text `#project-name` — HH:MM

# Backlog

## project-name
- [ ] item moved from Today during cleanup
- [ ] older item

## another-project
- [ ] item
```

The **Today** section is the "must do today" list. The **Backlog** section is organized by project and holds everything else.

## Operation 1: Capture

When the user gives you a todo — explicitly or embedded in conversation:

1. **Write their exact words** as the task text. Do not rephrase, clean up, or editorialize.
2. **Guess the project** from context (current conversation topic, mentioned repos, existing projects in the backlog). Use a lowercase `#tag` inline: `#keybindings`, `#cloud-agents`, `#pq`, etc.
3. **Timestamp it** with current time in HH:MM format at the end of the line.
4. **Add to the Today section** by default. If the user says it's not urgent or is a "someday" item, add directly to the appropriate Backlog project section.

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

## Operation 2: Clean Up

Triggered when the user says "clean up todos", "triage", "rewrite my todos", or similar. This replaces the user's old habit of rewriting the file daily.

### Steps

1. **Read `Todo.md`** in full.
2. **Ask the user** to confirm what stays in Today. Present the current Today list and ask:
   - Which of these are must-do today?
   - Any of these done?
3. **Move, don't delete.** Items leaving Today go to the Backlog under their project heading. Create project headings as needed.
4. **Mark done items** with `[x]` and move them to a `## Done` section at the bottom with today's date.
5. **Update the frontmatter date** to today.
6. **Rewrite the file** with the cleaned structure.

### Clean up rules

- **Never delete a todo.** Move to Backlog or Done.
- **Preserve the user's original text** on every item — don't reword tasks during cleanup.
- **Keep Today short** — this is the "only what matters today" list.
- **Merge duplicate items** only if they're clearly the same task. When merging, keep the earlier timestamp and both project tags if different.
- **Remove empty project headings** from Backlog if all items moved out.

### Done section format

```markdown
## Done

### 02/04
- [x] shipped the notification throttler `#interviews` — 02/04
- [x] merged keybinding PR `#keybindings` — 02/04
```
