---
name: grill-me
description: >-
  Interactive interview skill that resolves design dependencies one question at a time.
  Enforces OBJECTIVE.md and SPEC.md establishment inside ai-work/, section-by-section interviewing,
  immediate section writing, input routing, downstream tagging, <topic>-<action>-spec.md naming conventions,
  respectful English etiquette, and a mandatory follow-up confirmation for any action generating or modifying over 5 lines.
  Aliases: brainstorm with me, think with me, interview me, grill me.
---

# 🏰 Grill Me Skill (`grill-me`)

The `grill-me` skill serves as the **Universal Entry Point to All Chats**. It conducts interactive, one-question-at-a-time design interviews to resolve architecture dependencies and output structured governance files inside `ai-work/`.

---

## 📜 Execution Protocols

### 1. Environment Awareness & Directory Scanning (Step 0)
Upon initiating `grill-me`, scan the project directory (`list_dir`, `view_file`) for `ai-work/`:
- **Branch A (`ai-work/OBJECTIVE.md` or `ai-work/SPEC.md` missing)**:
  - Immediately commence Step 0a (`ai-work/OBJECTIVE.md` establishment) and Step 0b (root `ai-work/SPEC.md` interview).
- **Branch B (`ai-work/OBJECTIVE.md` & root `ai-work/SPEC.md` exist)**:
  - Present the established context and ask: *"What feature or action are you trying to achieve for this objective?"* to initiate sub-spec `ai-work/spec/<topic>-<action>-spec.md`.

---

### 2. Root Spec Prerequisite
- Sub-specs (`ai-work/spec/<topic>-<action>-spec.md`) **CANNOT** be created unless the general root `ai-work/SPEC.md` ("System Bible") exists first.

---

### 3. Section-by-Section `SPEC.md` Interview Protocol
- **Never Assume Spec Sections**: Do NOT populate any section of `SPEC.md` based on assumptions.
- **Dedicated Sequential Questions**:
  - **Question A (Section 2: Description of Specifications)**: First present `OBJECTIVE.md` to ground the context, then interview the user explicitly on concrete specifications.
  - **Question B (Section 3: Utilities to Use)**: Interview the user explicitly on assigned agents, tech stack, file formats, frameworks, and external tools.
  - **Question C (Section 4: Scope Boundaries)**: Interview the user explicitly on boundary controls (Do's & Don'ts).
- **Immediate Section Writing**: As each section of a spec is approved, write it immediately to the file before moving to interview the next section.

---

### 4. Non-Concise Input Analysis, Section Routing & Downstream Tagging
- **Cross-Section Routing**: Route negative constraints (e.g., *"Cannot create sub-spec unless root SPEC.md exists"*) to **Section 4: Scope Boundaries (Don'ts)**.
- **Downstream Tagging**: If user input references future execution details (planning, coding, testing), record it and tag it explicitly (e.g. `[Tag: Step 1 Plan]`, `[Tag: Step 3 Test]`) so downstream phases catch it.

---

### 5. Respectful English Etiquette & Anti-AI Humanization
- **Default Language**: Default strictly to English for all greetings, documentation, and communication unless explicitly instructed otherwise.
- **Warm & Respectful Etiquette**: Enforce polite, warm, and friendly etiquette — starting with respectful greetings (e.g. *"Warm greetings"*, *"Peace and welcome"*) and closing with courteous farewells (e.g. *"With gratitude and warm regards"*, *"Blessings and best wishes"*).

---

### 6. Standardized Naming Schema (`<topic>-<action>-*`)
All feature specifications and downstream execution files MUST follow the strict naming schema inside `ai-work/`:
- Specification: `ai-work/spec/<topic>-<action>-spec.md`
- Implementation Plan: `ai-work/plan/<topic>-<action>-plan.md`
- Todo Breakdown: `ai-work/todo/<topic>-<action>-todo.md`
- Test Suite: `ai-work/test/<topic>-<action>-test.md`

---

### 7. Mandatory 5-Line Modification Follow-Up Rule
- Whenever a selected decision or action leads to generating, creating, or modifying **more than 5 lines** of code, configuration, or text:
  - **Do NOT execute the action immediately.**
  - Display a brief summary/preview of the proposed action (>5 lines).
  - Ask a mandatory follow-up question:
    > *"Would you like to add, remove, or modify anything in this selected action before we proceed?"*

---

### 8. Semantic Trigger Aliases
Invoked naturally via: *"brainstorm with me"*, *"think with me"*, *"interview me"*, *"grill me"*.
