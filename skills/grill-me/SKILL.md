---
name: grill-me
description: >-
  Interactive interview skill that resolves design dependencies one question at a time.
  Enforces Objective.md and Spec.md establishment, section-by-section interviewing,
  <topic>-<action>-spec.md naming conventions, collision detection, and a mandatory
  follow-up confirmation for any action generating or modifying over 5 lines.
  Aliases: brainstorm with me, think with me, interview me, grill me.
---

# Grill Me Skill

This skill governs interactive design interviews and decision alignment.

## Core Protocol Rules

### 1. Objective & Spec Establishment (Step 0a & 0b)
- **Step 0a**: Establish and record the High-Level Purpose in `OBJECTIVE.md`.
- **Step 0b**: Establish concrete specifications via section-by-section interviewing, saving to `<topic>-<action>-spec.md`. Root `SPEC.md` acts as "The System Bible".

### 2. Section-by-Section `SPEC.md` Interview Protocol
- **Never Assume Spec Sections**: Do NOT populate any section of `SPEC.md` based on assumptions.
- **Dedicated Sequential Interview Questions**:
  - **Question A (Section 2: Description of Specifications)**: First present `OBJECTIVE.md` to ground the context, then interview the user explicitly on the concrete specifications desired to achieve that objective.
  - **Question B (Section 3: Utilities to Use)**: Interview the user explicitly on assigned agents, tech stack, file formats, frameworks, and external tools.
  - **Question C (Section 4: Scope Boundaries)**: Interview the user explicitly on explicit boundary controls (Do's & Don'ts).

### 3. Feature Naming Schema & Collision Detection
- All feature specifications and downstream execution files MUST follow the strict naming schema: `<topic>-<action>-spec.md`, `<topic>-<action>-plan.md`, `<topic>-<action>-todo.md`, `<topic>-<action>-test.md`.
- **Collision Detection**: If a conversation or requirement touches an existing spec:
  - **Option A (Update)**: Expand existing spec file with explicit user consent.
  - **Option B (New Spec)**: Create a new spec file with a refined topic/action name.

### 4. Semantic Trigger Aliases
Invoked naturally via: *"brainstorm with me"*, *"think with me"*, *"interview me"*, *"grill me"*.

### 5. Mandatory 5-Line Modification Follow-Up Rule
- Whenever a selected decision or action leads to generating, creating, or modifying **more than 5 lines** of code, configuration, or text:
  - **Do NOT execute the action immediately.**
  - Display a brief summary/preview of the proposed action (>5 lines).
  - Ask a mandatory follow-up question:
    > *"Would you like to add, remove, or modify anything in this selected action before we proceed?"*

### 6. User Refinement Loop
- Incorporate any user additions or edits into the proposed structure.
- Re-confirm with the user until explicit sign-off ("yes" or "proceed") is granted.
