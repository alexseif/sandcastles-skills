---
name: grill-me
description: >-
  Interactive interview skill that resolves design dependencies one question at a time.
  Enforces Objective.md and Spec.md establishment, conflict checking, sub-objective forking,
  and a mandatory follow-up confirmation for any action generating or modifying over 5 lines.
---

# Grill Me Skill

This skill governs interactive design interviews and decision alignment.

## Core Protocol Rules

### 1. Objective & Spec Establishment (Step 0a & 0b)
- **Step 0a**: Establish and record the High-Level Purpose in `OBJECTIVE.md`.
- **Step 0b**: Establish and record concrete specifications, tech stack, constraints, and formats in `SPEC.md`.

### 2. Objective & Spec Alignment & Conflict Resolution
- Evaluate every follow-up question, design decision, and proposed option against `OBJECTIVE.md` and `SPEC.md`.
- **If a decision/request conflicts**:
  - **Option A (Update)**: Explicitly update and broaden `OBJECTIVE.md` / `SPEC.md` with user agreement.
  - **Option B (Sub-Objective Fork)**: Fork the conflicting topic into a separate sub-objective or new branch to keep concerns cleanly isolated.

### 3. Sequential Interviewing
- Ask design questions **one at a time**.
- Present clear options using the `ask_question` tool.
- Always include a recommended option prefixed with `(Recommended)`.

### 4. Mandatory 5-Line Modification Follow-Up Rule
- Whenever a selected decision or action leads to generating, creating, or modifying **more than 5 lines** of code, configuration, or text:
  - **Do NOT execute the action immediately.**
  - Display a brief summary/preview of the proposed action (>5 lines).
  - Ask a mandatory follow-up question:
    > *"Would you like to add, remove, or modify anything in this selected action before we proceed?"*

### 5. User Refinement Loop
- Incorporate any user additions or edits into the proposed structure.
- Re-confirm with the user until explicit sign-off ("yes" or "proceed") is granted.
