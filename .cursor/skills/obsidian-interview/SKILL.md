---
name: obsidian-interview
description: Manage interview question templates and candidate feedback in the Obsidian vault. Use when the user mentions interviews, candidates, interview questions, rubrics, feedback summaries, or hire/no-hire decisions.
---

# Interview Management

Interview content lives in two places:
- **`templates/`** — reusable question templates (one per question)
- **`Interviews/`** — per-candidate interview notes (created from templates)

## Operation 1: Create Template

Triggered when the user shares a Notion link to an interview question or says "create interview template."

### Steps

1. **Read the Notion doc** using the Notion MCP. Extract:
   - Question title
   - The prompt/problem statement for each part
   - Known solutions and key insights
   - Rubric criteria (if present)
2. **Create the template** at `templates/Interview - QUESTION_NAME.md`

### Template format

```markdown
---
tags: [interview]
---

[Question Name — Notion Doc](notion-url)

{{date}}

## Notes

### Part 1: Part Title
> high-level summary of what this part is about — a sentence or two so the interviewer can glance at it during note-taking

-

### Part 2: Part Title
> high-level summary

-

### Overall Impression
-

---

## What to Look For

- signal 1
- signal 2
- signal 3

## Part N: Part Title

**Overview:** one-paragraph summary of what this part tests

**Key things to watch for:**
- what good looks like
- common mistakes
- edge cases that matter

**Known solutions:**
- Solution approach 1 — brief description, complexity
- Solution approach 2 — brief description, complexity

---

## Rubric

### Strong Hire
- criteria from Notion doc

### Hire
- criteria from Notion doc

### No Hire
- criteria from Notion doc
```

### Template rules

- **Don't include prompts to paste.** The interviewer sources those from the Notion doc directly.
- **Don't include a CoderPad link.** Each candidate gets a unique pad.
- **"What to Look For"** should be 3–5 high-level signals, not a wall of text. These are glanceable reminders.
- **Part overviews** should be concise — what the part tests, not a full solution walkthrough.
- **Known solutions** are for the interviewer's reference, not to share with the candidate. Include complexity.
- **Rubric** should map directly to the Notion doc's rubric. Don't invent criteria.
- If the Notion doc doesn't have a rubric section, note that and ask the user for rubric details.
- **Notes sections** include a brief high-level summary (as a blockquote) of what that part covers, so the interviewer can glance at context while taking notes. The actual notes area is empty — the interviewer fills it during the interview.

## Operation 2: Create Interview Note

Triggered when the user says they have an interview, names a candidate, or asks to start an interview note.

### Steps

1. **Ask which question** if not obvious from context. List available interview templates from `templates/`.
2. **Create the note** at `Interviews/CANDIDATE_NAME - QUESTION_NAME - MM-DD.md` by copying the template content.
3. **Fill in `{{date}}`** with today's date.

## Operation 3: Summarize Feedback

Triggered when the user says "summarize feedback", "write up interview", "how did they do", or shares post-interview notes.

### Steps

1. **Read the interview note** with the user's raw notes.
2. **Read the corresponding template** to get the full rubric and known solutions.
3. **Compare the candidate's performance** (from the user's notes) against the rubric criteria.
4. **Write a feedback summary** appended to the interview note.

### Feedback summary format

Append this to the end of the interview note:

```markdown
## Feedback Summary

**Recommendation:** Strong Hire / Hire / No Hire

### Part-by-Part Assessment

**Part 1: Part Title**
- What they did: brief summary of approach
- Rubric alignment: which criteria they met or missed
- Signal: positive/negative/mixed

**Part 2: Part Title**
- ...

### Strengths
- strength 1
- strength 2

### Concerns
- concern 1
- concern 2

### Overall
One-paragraph synthesis suitable for pasting into a hiring doc or Notion.
```

### Feedback rules

- **Ground everything in the user's notes.** Don't invent observations the user didn't write down.
- **Map explicitly to rubric criteria.** For each rubric bullet, say whether the candidate demonstrated it or not based on the notes.
- **Be direct about the recommendation.** The user wants a clear signal, not hedging.
- **Flag gaps.** If the notes don't cover a rubric area, say so — "notes don't mention X, can't assess."
- **Keep the user's voice.** Quote their notes where useful rather than rephrasing.
