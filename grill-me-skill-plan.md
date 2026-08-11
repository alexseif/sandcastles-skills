# 📋 Implementation Plan: Grill-Me Skill (`grill-me-skill-plan.md`)

Grounded in [`OBJECTIVE.md`](./OBJECTIVE.md) and [`grill-me-skill-spec.md`](./grill-me-skill-spec.md).

---

## 🎯 Plan Summary
Decompose the implementation of the updated `grill-me` skill into small, isolated, independently testable tasks.

---

## 🛠️ Task Breakdown

### Task 1: Environment Awareness & Directory Scanner Setup
- **Goal**: Implement protocol logic to scan `ai-work/` for existing `OBJECTIVE.md` and root `SPEC.md`.
- **Logic**:
  - If `ai-work/OBJECTIVE.md` or `ai-work/SPEC.md` missing $\rightarrow$ initiate Step 0a & Step 0b interview.
  - If `ai-work/OBJECTIVE.md` & `ai-work/SPEC.md` exist $\rightarrow$ present context and ask for new feature/action.
- **Verification**: Check directory scanning flow against empty and populated project folders.

### Task 2: Section-by-Section Spec Interviewer & Immediate File Writer
- **Goal**: Implement the 4-part `SPEC.md` sequential interview engine (Section 2 $\rightarrow$ Section 3 $\rightarrow$ Section 4).
- **Logic**:
  - Present `OBJECTIVE.md` before Section 2.
  - Apply Non-Concise Input Routing (route constraints to Section 4 Don'ts).
  - Apply Downstream Phase Tagging (`[Tag: Step 1 Plan]`).
  - **Immediate Section Writing**: Write approved sections directly to `ai-work/spec/<topic>-<action>-spec.md` before proceeding.
- **Verification**: Verify sequential question flow and section file writing.

### Task 3: 5-Line Modification Preview & Follow-up Confirmation Engine
- **Goal**: Enforce mandatory preview & follow-up question for any action modifying $> 5$ lines.
- **Logic**:
  - Show preview snippet (> 5 lines).
  - Ask mandatory question: *"Would you like to add, remove, or modify anything in this selected action before we proceed?"*
- **Verification**: Verify follow-up prompt triggers on actions $> 5$ lines.

### Task 4: Skill Runbook File (`skills/grill-me/SKILL.md`) Update & Testing
- **Goal**: Update `skills/grill-me/SKILL.md` with complete, verified runbook instructions.
- **Verification**: Test `grill-me` skill execution end-to-end and commit to GitHub.
