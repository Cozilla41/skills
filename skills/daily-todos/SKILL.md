---
name: daily-todos
description: Generate a daily to-do list from freeform text. Parse tasks and create a Markdown checklist saved to .todos/ with today's date.
---

# Daily To-Do List Generator

Create today's to-do list from freeform text input.

## Your task

The user will provide a text description of their tasks for today. Your job is to:

1. **Parse** the input text to extract individual tasks
   - Split by common delimiters (commas, semicolons, newlines, Chinese punctuation like `、`)
   - Keep each task concise and actionable
   - Strip extra whitespace

2. **Generate** a Markdown file with:
   - Filename: `.todos/YYYY-MM-DD.md` (today's date in ISO format)
   - Content: A `# YYYY-MM-DD` header followed by a checklist
   - Format: Each task as `- [ ] Task description`

3. **Save** the file to `.todos/` (create the directory if needed)

4. **Report** the result to the user:
   - Show if the file was created or overwritten
   - Display the generated task list
   - Be encouraging and brief

## Example

User input: `"开会、写代码、复查PR、修复auth bug"`

Generate file `.todos/2024-01-15.md`:
```
# 2024-01-15

- [ ] 开会
- [ ] 写代码
- [ ] 复查PR
- [ ] 修复auth bug
```

## Important rules

- If no tasks can be extracted, fail gracefully and ask the user to provide clearer input
- If `.todos/` doesn't exist, create it
- If the file already exists (same date), overwrite it and notify the user
- All tasks go into ONE file per day, not separate files
- Keep task descriptions short (one sentence each)

## Handling edge cases

- **Empty input**: Politely ask for a valid task description
- **Very long input**: Still parse all of it, don't truncate
- **Special characters**: Keep them (they help with localization)
