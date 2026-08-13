# Planner Skill Specification

## 1. Objective Alignment
This specification aligns with the High-Level Purpose defined in the root `OBJECTIVE.md`. The goal is to create a planning skill that generates detailed, step-by-step plans from `objective.md`, `spec.md`, and optionally `<Topic>-<Action>-spec.md`, while strictly enforcing the defined rules.

## 2. Description of Specifications
- **Complexity Limits:** Plans must not exceed a predefined complexity or ambiguity threshold; they must be broken down if necessary.
- **File Generation & Naming:** Generating a plan must produce two files following the spec naming convention:
  - `*plan.md` (e.g., `PLAN.md` or `<Topic>-<Action>-plan.md`): A high-level description of the task.
  - `*todo.md` (e.g., `TODO.md` or `<Topic>-<Action>-todo.md`): A detailed, actionable breakdown of the plan.
- **Plan Document Structure (`*plan.md`):**
  - **YAML Frontmatter:** Must include links to the relevant `OBJECTIVE.md` and spec file, along with a `status` (e.g., under review, approved, in progress, complete).
  - **Description:** High-level summary of the task.
  - **Phased Plan:** The actual plan structured in phases (if needed), including clear acceptance criteria.
  - **Cost Estimates:** A table estimating token usage and dollar cost.
  - **Precedence Graph:** A graph/chart establishing dependencies for the `todo.md` tasks to function correctly.
- **Todo Document Structure (`*todo.md`):**
  - Must consist of sequentially ordered Markdown tasks with clear pre-requisites and validation steps for each.

## 3. Utilities to Use
- **File Formats:** Standard Markdown for document structure and YAML for frontmatter metadata.
- **Diagrams:** Mermaid.js must be used to render the precedence graph in the plan file.
- **Agents/Models:** Any capable model can execute this planning skill.

## 4. Scope Boundaries (Do's & Don'ts)
- **Do:** strictly generate the planning files (`*plan.md` and `*todo.md`) according to the established specifications.
- **Don't:** execute code, run commands, or implement features during the planning phase.
- **Don't:** modify the existing `OBJECTIVE.md` or `SPEC.md` files; treat them as read-only inputs during planning.
