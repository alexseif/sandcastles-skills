# 📋 Feature Specification: Grill-Me Skill (`grill-me-skill-spec.md`)

---

## 🎯 1. Objective Alignment
- **Target Objective**: Build and refine the `grill-me` skill runbook as the universal entry point to all chats, systematically interviewing users to output `OBJECTIVE.md` (high-level goal), root `SPEC.md` ("System Bible"), and `<topic>-<action>-spec.md` (feature specifications) before any work begins.
- **Reference**: Grounded in [`OBJECTIVE.md`](./OBJECTIVE.md) and root [`SPEC.md`](./SPEC.md).

---

## 📝 2. Description of Specifications

### Feature Overview & Primary Goal
The `grill-me` skill serves as the **Universal Entry Point to All Chats**. Its primary workflow systematically guides the user through generating:
1. **`OBJECTIVE.md`**: High-level purpose and goals of the session/project.
2. **Root `SPEC.md` ("System Bible")**: System-wide specifications, architecture, and scope rules. MUST be generated first if it does not already exist.
3. **Feature Sub-Spec (`<topic>-<action>-spec.md`)**: Concrete feature-level specifications branched from the root `SPEC.md`.

### Key Protocol Specifications
- **Universal Entry Point**: Every new chat or feature request defaults to `grill-me` protocol initialization.
- **Root Spec Prerequisite Enforcement**: If root `SPEC.md` is missing, `grill-me` interviews and writes root `SPEC.md` before proceeding to `<topic>-<action>-spec.md`.
- **Section-by-Section Interviewing**: Ask dedicated sequential questions for Section 2, Section 3, and Section 4.
- **Immediate Section Writing**: Write approved sections immediately to the file before interviewing the next section.
- **Input Routing & Downstream Tagging**: Route negative constraints to Section 4 (Don'ts) and tag future execution ideas (e.g. `[Tag: Step 1 Plan]`).
- **Mandatory 5-Line Modification Preview**: Present a preview and ask confirmation for any action generating or modifying $> 5$ lines.

---

## 🛠️ 3. Utilities to Use

### Core Technical Utilities
- **Directory Scanning & Environment Awareness**: File discovery tools (`list_dir`, `view_file`) to scan the working folder for existing `OBJECTIVE.md` and root `SPEC.md`.
- **Interview Modal Tool**: `ask_question` tool (rendering interactive multi-choice & write-in questions).
- **File Formats**: Standard GitHub Markdown (`.md`), YAML frontmatter headers for `skills/grill-me/SKILL.md`.
- **Version Control & Hosting**: Git, GitHub CLI (`gh`), repository `git@github.com:alexseif/sandcastles-skills.git`.
- **Global Discovery Symlinks**: `~/.agents` $\rightarrow$ `/home/alexseif/dev/sandcastles-skills`.
- **Naming Schema**: `<topic>-<action>-spec.md`, `<topic>-<action>-plan.md`, `<topic>-<action>-todo.md`, `<topic>-<action>-test.md`.

### Environment-Aware Decision Workflow
- **If `OBJECTIVE.md` / `SPEC.md` Missing**: Commences step-by-step interview to generate `OBJECTIVE.md` and root `SPEC.md`.
- **If `OBJECTIVE.md` & `SPEC.md` Exist**: Presents established context and asks: *"What feature or task are you trying to achieve for this objective?"* to initiate `<topic>-<action>-spec.md`.

### Functional Agent Roles Assigned
- **Software Architect Agent**: Guides systemic decision trees, root spec enforcement, and section routing.
- **Technical Writer / Documentation Agent**: Formats and writes approved spec sections immediately into markdown files.
