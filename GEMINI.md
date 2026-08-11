# 🏰 Sandcastles Skills: Global Agent Rules (`GEMINI.md`)

This file defines the universal governance, behavioral protocols, and execution lifecycles for all agent tasks across all domains.

---

## 🎯 1. Universal Objective & Spec Harness

Regardless of domain (Software Engineering, Content Writing, Email Processing, Media Generation, Research, System Operations):

### A. High-Level Purpose (`OBJECTIVE.md`)
1. **Establish Purpose First**: No work begins without a clearly established **High-Level Purpose** documented in `OBJECTIVE.md`.
2. **Domain Agnostic**: Defines the primary goal (e.g. *"Build an app in Cairo"*, *"Write an article on AI"*).

### B. Concrete Specifications (`SPEC.md`)
1. **Define Specifications Second**: Following `OBJECTIVE.md`, create `SPEC.md` outlining all concrete constraints, requirements, and quality standards.
2. **Standard 4-Part `SPEC.md` Template**:
   - **Section 1: Objective Alignment** — Explicit reference to `OBJECTIVE.md`.
   - **Section 2: Description of Specifications** — Detailed specifications, technical constraints, quality targets.
   - **Section 3: Utilities to Use** — Agents assigned, tech stack, file formats, frameworks, external tools.
   - **Section 4: Scope (Do's & Don'ts)** — Explicit boundaries control (what is in scope vs out of scope).
3. **Traceability**: All subsequent tool calls, code, writing, and sub-tasks MUST align with both `OBJECTIVE.md` and `SPEC.md`.
4. **Conflict Management**:
   - If a new requirement conflicts with `OBJECTIVE.md` or `SPEC.md`:
     - **Option A (Update)**: Update `OBJECTIVE.md` / `SPEC.md` with explicit user consent.
     - **Option B (Fork)**: Fork a sub-objective/sub-spec into a separate isolated branch.

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
2. **Step 0b: Define Specifications** — Document concrete standards, tech stack, and formats in `SPEC.md` (4-part template).
3. **Step 1: Task Planning** — Decompose `SPEC.md` into isolated, testable tasks.
4. **Step 2: Execution** — Implement strictly within scope boundaries.
5. **Step 3: Verification** — Run tests, builds, or quality checks to verify against `SPEC.md`.
6. **Step 4: Outcome Report** — Present concise outcome report and request user sign-off.
