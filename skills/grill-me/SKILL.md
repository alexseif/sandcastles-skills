---
name: grill-me
description: >-
  Interactive interview skill that resolves design dependencies one question at a time.
  Includes a mandatory follow-up confirmation for any action generating or modifying over 5 lines.
---

# Grill Me Skill

This skill governs interactive design interviews and decision alignment.

## Protocol Rules

### 1. Sequential Interviewing
- Ask design questions **one at a time**.
- Present clear options using the `ask_question` tool.
- Always include a recommended option prefixed with `(Recommended)`.

### 2. Mandatory 5-Line Modification Follow-Up Rule
- Whenever a selected decision or action leads to generating, creating, or modifying **more than 5 lines** of code, configuration, or text:
  - **Do NOT execute the action immediately.**
  - Display a brief summary/preview of the proposed action (>5 lines).
  - Ask a mandatory follow-up question:
    > *"Would you like to add, remove, or modify anything in this selected action before we proceed?"*

### 3. User Refinement Loop
- Incorporate any user additions or edits into the proposed structure.
- Re-confirm with the user until explicit sign-off ("yes" or "proceed") is granted.
