---
name: obsidian-inbox
description: Triage the Obsidian vault Inbox.md file. Use when the user says "triage inbox", "check inbox", "process inbox", or wants to sort through items they captured offline.
---

# Inbox Triage

The user's inbox lives in `Inbox.md` at the vault root. The user adds items here manually when they're offline — quick thoughts, links, half-formed ideas, tasks, anything. The inbox is never written to by the agent. It is only read and triaged collaboratively.

## Inbox.md Structure

Freeform. The user may write bullets, paragraphs, links, or just fragments. There is no enforced format — this is a capture scratchpad.

## Triage

Triggered when the user says "triage inbox", "check inbox", "process inbox", "let's go through inbox", or similar.

### Steps

1. **Read `Inbox.md`** in full.
2. **If empty**, tell the user the inbox is clear and stop.
3. **Present each item** (or cluster of related items) to the user one at a time. For each item, suggest a destination:
   - **Todo.md** — if it looks like a task or action item
   - **Ideas.md** — if it looks like an idea, feature thought, or product suggestion
   - **Log/** — if it's a point-in-time note, meeting recap, or observation
   - **Reference/** — if it's evergreen knowledge worth maintaining
   - **Discard** — if the user decides it's no longer relevant
4. **Ask the user to confirm** before acting on each item. The user may override your suggestion, add context, or combine items.
5. **Route confirmed items** to their destination using the conventions of that destination (follow the relevant skill — obsidian-todos, obsidian-ideas, log-notes rule, reference-notes rule).
6. **Remove triaged items** from `Inbox.md` as they are processed.
7. **When done**, confirm the inbox is clear.

### Triage rules

- **Never write to the inbox.** Only the user adds items. The agent only reads and triages.
- **Never discard without asking.** Even if an item seems stale or unclear, ask the user first.
- **Preserve the user's words** when routing — don't rephrase their text when moving it to Todo, Ideas, etc.
- **Ask for context if needed.** Inbox items may be cryptic. It's fine to ask "what did you mean by this?" before routing.
- **Batch similar items.** If multiple inbox entries clearly belong to the same destination, present them as a group to speed up triage.
