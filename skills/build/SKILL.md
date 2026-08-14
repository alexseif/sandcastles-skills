---
name: build
description: >-
  Executes planned tasks strictly within defined scope boundaries using a disciplined 4-phase loop (Implement → Verify → Commit → Check-off).
  Enforces minimal touch, 5-line confirmation previews for non-md files, empirical verification, per-task git commits, todo progress check-offs, and dynamic skill/agent delegation.
  Aliases: build this, execute task, run build, implement task, build loop.
---

# 🛠️ Build Skill (`build`)

The `build` skill serves as the core task execution engine of the Sandcastles Skills harness. It executes planned tasks strictly within defined scope boundaries using a disciplined 4-phase execution loop per todo item.

---

## 🛑 Scope Boundaries (Do's & Don'ts)

### ✅ Do's
1. **Sequential Execution**: Execute tasks strictly one by one in sequential order from `ai-work/todo/<topic>-<action>-todo.md`.
2. **Minimal Touch**: Write only the minimum amount of code required to complete the task item. Touch only explicitly requested files.
3. **Empirical Verification**: Run verification commands (build scripts, test suites, linters) before declaring any task complete.
4. **Per-Task Commit**: Create a clear git commit upon completion of each individual task item.
5. **Dynamic Skill Utilization**: Delegate tasks to specialized subagents or skills whenever appropriate.

### ❌ Don'ts
1. **No Scope Creep / Unrequested Refactoring**: Don't refactor adjacent systems, remove existing code, or alter unrequested files.
2. **No Superficial Symptom Patches**: Don't mask errors with try/except blocks, delete failing unit tests, or return dummy fallbacks.
3. **No Unverified Completion Claims**: Don't claim a task is resolved or working without runtime log proof.
4. **No Direct Code Edits Without Preview**: Don't edit or create non-`.md` files > 5 lines without presenting a preview and obtaining user confirmation.

---

## 📜 Execution Protocols

### 1. Plan & Todo Dependency Validation
Before initiating execution, verify that both the plan (`ai-work/plan/<topic>-<action>-plan.md`) and task breakdown (`ai-work/todo/<topic>-<action>-todo.md`) exist and are approved.

### 2. The 4-Phase Execution Loop
For every single task item in `ai-work/todo/<topic>-<action>-todo.md`, strictly follow this 4-phase cycle:
1. **Implement**: Write the minimum code necessary to satisfy task requirements. Touch only requested files.
2. **Verify**: Execute build scripts, linters, or test suites (`run_command`) to empirically verify functionality before declaring completion.
3. **Commit**: Perform a focused git commit (`git commit -m "..."`) summarizing the task completed.
4. **Check-off**: Update `ai-work/todo/<topic>-<action>-todo.md`, marking the task as completed (`[x]`).

### 3. 5-Line Modification Preview Rule
Whenever any code, configuration, or non-`.md` file generation/modification exceeds 5 lines:
- Do NOT write the changes directly.
- Present a clear preview of the proposed changes.
- Obtain explicit user approval ("yes" or "proceed") before writing the file.
- *Note*: Documentation and governance markdown files (`.md`) are exempt from the preview pause during active build execution.

### 4. Dynamic Agent & Skill Delegation
Dynamically leverage specialized subagents (`research`, `self`) or domain skills (e.g., PHP, Node-TS, Python, `document`, Content Writer, image generation) whenever complex sub-tasks arise during implementation.
