# 🏰 Sandcastles Skills: Global Agent Rules (`GEMINI.md`)

This file defines the universal governance, behavioral protocols, and execution lifecycles for all agent tasks across all domains.

---

## 🎯 1. Universal Objective & Spec Harness

Regardless of domain (Software Engineering, Content Writing, Email Processing, Media Generation, Research, System Operations):

### A. High-Level Purpose (`OBJECTIVE.md`)
1. **Establish Purpose First**: No work begins without a clearly established **High-Level Purpose** documented in `OBJECTIVE.md`.
2. **Domain Agnostic**: Defines the primary goal across all AI providers (Gemini, Claude, OpenAI, DeepSeek, Local Models).

### B. Root System Specification (`SPEC.md` — "The System Bible")
1. **Root Specification**: The root `SPEC.md` acts as the foundational "System Bible" for the entire project. All branched sub-specs must align with it.
2. **Standard 4-Part `SPEC.md` Template**:
   - **Section 1: Objective Alignment** — Explicit reference to `OBJECTIVE.md`.
   - **Section 2: Description of Specifications** — Detailed specifications, technical constraints, quality targets.
   - **Section 3: Utilities to Use** — Agents assigned, tech stack, file formats, frameworks, external tools.
   - **Section 4: Scope (Do's & Don'ts)** — Explicit boundaries control (what is in scope vs out of scope).

### C. Section-by-Section `SPEC.md` Interview Protocol
1. **Never Assume Spec Sections**: Do NOT populate any section of `SPEC.md` based on assumptions.
2. **Dedicated Sequential Interview Questions**:
   - **Question A (Section 2: Description of Specifications)**: First present `OBJECTIVE.md` to ground the context, then interview the user explicitly on the concrete specifications desired to achieve that objective.
   - **Question B (Section 3: Utilities to Use)**: Interview the user explicitly on assigned agents, tech stack, file formats, frameworks, and external tools.
   - **Question C (Section 4: Scope Boundaries)**: Interview the user explicitly on explicit boundary controls (Do's & Don'ts).
3. **Mandatory 5-Line Modification Check**: After drafting each section, if the text exceeds 5 lines, show a preview and ask:
   > *"Would you like to add, remove, or modify anything in this selected action before we proceed?"*

### D. Feature Naming Convention & Multi-Spec Architecture
1. **Sub-Spec Scope**: An `OBJECTIVE.md` can encompass multiple features or sub-components. Each feature gets its own dedicated specification.
2. **Standardized Naming Schema**: All feature-level specs and downstream execution files MUST follow the strict naming format:
   - Specification: `<topic>-<action>-spec.md` (e.g., `admin-auth-spec.md`, `map-search-spec.md`)
   - Implementation Plan: `<topic>-<action>-plan.md`
   - Todo Breakdown: `<topic>-<action>-todo.md`
   - Test Suite: `<topic>-<action>-test.md`
3. **Collision Prevention**: If a conversation or new requirement collides with an existing `<topic>-<action>-spec.md`:
   - **Option A (Update)**: Update and expand the existing spec file with explicit user consent.
   - **Option B (New Spec)**: Create a new distinct spec with a refined topic/action name if it represents a separate issue.
4. **Objective Expansion on Ambiguity**: If a new sub-spec or feature is not explicitly covered in `OBJECTIVE.md`, present the user with the option to expand `OBJECTIVE.md` to detail it further before drafting the spec.

### E. Standardized Skill Names & Semantic Aliases Roster
All skills follow a unified structure and use short, consistent names with natural trigger aliases:
1. **`grill-me`** (Aliases: *"brainstorm with me"*, *"think with me"*, *"interview me"*, *"grill me"*)
2. **`plan`** (Aliases: *"let's plan"*, *"plan this feature"*, *"break down feature"*)
3. **`code`** (Aliases: *"build"*, *"implement task"*, *"write code"*)
4. **`review`** (Aliases: *"review work"*, *"review code"*, *"check quality"*)
5. **`test`** (Aliases: *"run tests"*, *"verify task"*, *"test code"*)
6. **`report`** (Aliases: *"generate report"*, *"summarize outcome"*, *"report outcome"*)

---

## 🛑 2. Ambiguity & Safety Protocols

1. **Never Guess Ambiguity**: If a requirement, specification, or path is ambiguous, **STOP**. Do NOT make unverified assumptions.
2. **Present 2 Options with Trade-offs**: Always present at least 2 clear options with pros/cons and trade-off values for user selection.
3. **5-Line Modification Confirmation**: Any proposal or edit generating/modifying **more than 5 lines** must present a preview and ask:
   > *"Would you like to add, remove, or modify anything in this selected action before we proceed?"*
4. **Scope Discipline**: Touch only what is explicitly requested. Never refactor adjacent code or delete files without approval.

---

## 🔄 3. Universal Execution Lifecycle

Every task follows a strict 6-stage lifecycle:
1. **Step 0a: Establish Objective** — Document high-level goal in `OBJECTIVE.md`.
2. **Step 0b: Define Specifications** — Document concrete standards in `<topic>-<action>-spec.md` via section-by-section interview.
3. **Step 1: Task Planning** — Decompose spec into isolated tasks in `<topic>-<action>-plan.md`.
4. **Step 2: Execution** — Implement strictly within scope boundaries.
5. **Step 3: Verification** — Run tests in `<topic>-<action>-test.md` to verify against spec.
6. **Step 4: Outcome Report** — Present concise outcome report and request user sign-off.
