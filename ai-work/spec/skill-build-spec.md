# 📋 Feature Specification: Build Skill (`ai-work/spec/skill-build-spec.md`)

---

## 🎯 1. Objective Alignment
- **Target Objective**: Define and implement the `build` skill (`skills/build/SKILL.md`) for task execution, enforcing the disciplined 4-phase loop (Implement → Verify → Commit → Check-off) across all project tasks.
- **Reference**: Grounded in [`OBJECTIVE.md`](../OBJECTIVE.md) and [`SPEC.md`](../SPEC.md).

---

## 📝 2. Description of Specifications

### Core Purpose & Execution Loop
The `build` skill executes planned tasks strictly within defined scope boundaries using a 4-phase execution loop per todo item:
1. **Implement**: Write the minimum amount of code needed to fulfill the task requirements. Touch only explicitly requested files.
2. **Verify**: Execute build scripts, linters, or test suites to empirically verify functionality before declaring completion.
3. **Commit**: Perform a clear, focused git commit summarizing the task completed.
4. **Check-off**: Update the corresponding `ai-work/todo/<topic>-<action>-todo.md` file, marking the item as completed (`[x]`).

### Execution Controls
- **Plan & Todo Dependency**: Must read `ai-work/plan/<topic>-<action>-plan.md` and `ai-work/todo/<topic>-<action>-todo.md` before initiating work.
- **5-Line Modification Preview**: Present a preview and obtain user confirmation for any code/file modification > 5 lines.
- **Empirical Verification Only**: Never declare success without concrete runtime/build verification logs.

---

## 🛠️ 3. Utilities to Use

### Core Technical & Agentic Utilities
- **Dynamic Skill & Agent Delegation**: Dynamically utilize the best skill, subagent, or tool for the task at hand (e.g., specialized domain skills like PHP, Node-TS, Python, `document`, Content Writer agents, or image generation tools).
- **Execution & Shell Utilities**: `run_command` to execute build scripts, test suites, linters, and verification commands directly.
- **Git Version Control**: Git CLI (`git status`, `git add`, `git commit -m`) to commit per completed todo task.
- **File Editing Tools**: `replace_file_content` / `write_to_file` adhering strictly to the 5-line modification preview rule.
- **Todo Progress Tracking**: Standard Markdown check-boxes (`[x]`) in `ai-work/todo/<topic>-<action>-todo.md`.

---

## 🛑 4. Scope Boundaries (Do's & Don'ts)

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
4. **No Direct Edits Without Preview**: Don't edit or create files > 5 lines without presenting a preview and obtaining user confirmation.


