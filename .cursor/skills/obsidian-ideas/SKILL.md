---
name: obsidian-ideas
description: Capture and groom ideas in the Obsidian vault Ideas.md file. Use when the user shares an idea, feature request, product thought, or asks to groom, review, or dedupe their ideas list.
---

# Ideas Management

The user's ideas live in `Ideas.md` at the vault root. There are two operations: **capture** and **groom**.

## Ideas.md Structure

Ideas are organized by theme. Each theme is a top-level heading. Items within a theme are bullet points.

```markdown
# Theme Name

- idea text — MM/DD
  - sub-note or context
- another idea — MM/DD

# Another Theme

- idea — MM/DD
```

## Operation 1: Capture

When the user shares an idea — explicitly or in passing:

1. **Write their exact words.** Do not rephrase, clean up grammar, or editorialize.
2. **Add a date** at the end of the line: `— MM/DD`.
3. **Place it under the right theme heading.** Look at existing headings in `Ideas.md` and pick the best fit. If nothing fits, create a new theme heading.
4. **Preserve sub-notes.** If the user adds context, caveats, or follow-up thoughts, capture those as indented sub-bullets under the idea.

### Capture format

```markdown
- user's exact words — YYYY-MM-DD
  - additional context if any
```

### Choosing a theme

- Read the current `Ideas.md` headings first
- Match by topic, not by exact wording — e.g. a CLI idea goes under `# CLI`, an agent pane idea goes under `# IDE`
- If an idea spans two themes, put it under the more dominant one
- Only create a new heading if nothing existing is a reasonable fit
- Keep heading names short and consistent with existing ones

## Operation 2: Groom

Triggered when the user says "groom ideas", "review ideas", "clean up ideas", or similar.

### Steps

1. **Read `Ideas.md`** in full.
2. **Identify duplicates.** Look for ideas that say the same thing in different words, or ideas that are sub-cases of a broader idea. Present these to the user for confirmation before merging.
3. **Identify miscategorized items.** If an idea is under a theme that doesn't fit, suggest moving it. Ask the user before moving.
4. **Present a summary** to the user:
   - Potential dupes (with your suggested merge)
   - Items that might belong under a different heading
   - Headings that could be merged or split
5. **Wait for user input** before making changes. Grooming is collaborative — don't rewrite unilaterally.
6. **Apply changes** based on user's decisions.

### Groom rules

- **Never delete an idea.** Merge dupes by combining into one item and keeping the earlier date.
- **Preserve the user's original text** — when merging dupes, keep the most descriptive version and note the other as a sub-bullet.
- **Don't rephrase items** during grooming — only move, merge, or re-group.
- **Keep themes stable.** Don't rename existing headings unless the user agrees. Prefer adding new headings over renaming.
