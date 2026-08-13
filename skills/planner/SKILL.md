---
name: planner
description: >-
  Generates detailed, step-by-step implementation plans from objective and specification files, producing both a high-level plan and a detailed task breakdown.
  Aliases: plan this, create plan, make a plan, planning phase.
---

# 📝 Planner Skill (`planner`)

The `planner` skill handles the transition from specifications to actionable execution plans. It strictly consumes `OBJECTIVE.md` and `SPEC.md` (or sub-specs) to generate a structured `*plan.md` and a detailed `*todo.md`.

---

## 🛑 Scope Boundaries (Do's & Don'ts)
- **DO NOT** execute any code, run terminal commands, or attempt to implement features during the planning phase.
- **DO NOT** modify the existing `OBJECTIVE.md` or `SPEC.md` (or sub-specs) files; treat them as read-only inputs.
- **DO** strictly generate the planning files (`*plan.md` and `*todo.md`) according to the established specifications below.

---

## 📜 Execution Protocols

### 1. File Generation & Naming Convention
Whenever you generate a plan based on a specification, you MUST produce exactly two files. The file names must match the specification's naming convention:
- For the root `SPEC.md`, generate `PLAN.md` and `TODO.md`.
- For a sub-spec `ai-work/spec/<topic>-<action>-spec.md`, generate `ai-work/plan/<topic>-<action>-plan.md` and `ai-work/todo/<topic>-<action>-todo.md`.

### 2. Plan Document Structure (`*plan.md`)
The high-level plan file must be written in Standard Markdown and include:
- **YAML Frontmatter**: Must include:
  - Links to the relevant `OBJECTIVE.md` and spec file.
  - A `status` field (e.g., `under review`, `approved`, `in progress`, `complete`).
- **Description**: A high-level summary of the task.
- **Phased Plan**: The actual execution plan structured into phases (if needed), including clear acceptance criteria for each phase.
- **Cost Estimates**: A Markdown table estimating token usage and dollar cost for the execution.
- **Precedence Graph**: A diagram rendered exclusively using **Mermaid.js** establishing the sequence and dependencies for the tasks in `*todo.md`.

### 3. Todo Document Structure (`*todo.md`)
The detailed breakdown file must be written in Standard Markdown and include:
- A sequentially ordered list of Markdown tasks.
- **Clear Pre-requisites**: Explicitly stated for each task.
- **Validation Steps**: Clear validation criteria/steps for each task to verify success.
- **Complexity Limits**: Plans must not exceed a predefined complexity or ambiguity threshold. If tasks are too complex, they must be broken down further.

### 4. Utilities and Formatting
- Any capable model may execute this skill.
- Use strictly Standard Markdown for structure.
- Use YAML for all metadata frontmatter.
- Use **Mermaid.js** blocks for precedence graphs.
