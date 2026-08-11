---
name: grill-me
description: >-
  Interactive interview skill that resolves design dependencies one question at a time.
  Enforces Objective.md and Spec.md establishment, section-by-section interviewing,
  immediate section writing, input routing, downstream tagging, <topic>-<action>-spec.md naming conventions,
  and a mandatory follow-up confirmation for any action generating or modifying over 5 lines.
---

# Grill Me Skill

This skill governs interactive design interviews and decision alignment.

## Core Protocol Rules

### 1. Objective & Spec Establishment (Step 0a & 0b)
- **Step 0a**: Establish and record the High-Level Purpose in `OBJECTIVE.md`.
- **Step 0b**: Establish concrete specifications via section-by-section interviewing. Root `SPEC.md` ("System Bible") MUST exist before sub-specs (`<topic>-<action>-spec.md`) can be created.

### 2. Section-by-Section `SPEC.md` Interview Protocol
- **Never Assume Spec Sections**: Do NOT populate any section of `SPEC.md` based on assumptions.
- **Dedicated Sequential Interview Questions**:
  - **Question A (Section 2: Description of Specifications)**: First present `OBJECTIVE.md` to ground the context, then interview the user explicitly on the concrete specifications desired to achieve that objective.
  - **Question B (Section 3: Utilities to Use)**: Interview the user explicitly on assigned agents, tech stack, file formats, frameworks, and external tools.
  - **Question C (Section 4: Scope Boundaries)**: Interview the user explicitly on explicit boundary controls (Do's & Don'ts).
- **Immediate Section Writing**: As each section of a spec is approved, write it immediately to the file before moving to interview the next section.

### 3. User Input Analysis, Section Routing & Downstream Tagging
- **Cross-Section Routing**: Analyze non-concise user input and route negative constraints to **Section 4: Scope Boundaries (Don'ts)**.
- **Downstream Tagging**: If user input references future execution details (planning, coding, testing), record it and tag it explicitly (e.g. `[Tag: Step 1 Plan]`) so downstream phases catch it.

### 4. Mandatory 5-Line Modification Follow-Up Rule
- Whenever a selected decision or action leads to generating, creating, or modifying **more than 5 lines** of code, configuration, or text:
  - **Do NOT execute the action immediately.**
  - Display a brief summary/preview of the proposed action (>5 lines).
  - Ask a mandatory follow-up question:
    > *"Would you like to add, remove, or modify anything in this selected action before we proceed?"*

### 5. User Refinement Loop
- Incorporate any user additions or edits into the proposed structure.
- Re-confirm with the user until explicit sign-off ("yes" or "proceed") is granted.
