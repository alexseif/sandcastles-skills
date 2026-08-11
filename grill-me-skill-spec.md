# 📋 Feature Specification: Grill-Me Skill (`grill-me-skill-spec.md`)

---

## 🎯 1. Objective Alignment
- **Target Objective**: Build and refine the `grill-me` skill runbook as the universal entry point to all chats, systematically interviewing users to output `ai-work/OBJECTIVE.md` (high-level goal), root `ai-work/SPEC.md` ("System Bible"), and `ai-work/spec/<topic>-<action>-spec.md` (feature specifications) before any work begins.
- **Reference**: Grounded in [`OBJECTIVE.md`](./OBJECTIVE.md) and root [`SPEC.md`](./SPEC.md).

---

## 📝 2. Description of Specifications

### Feature Overview & Primary Goal
The `grill-me` skill serves as the **Universal Entry Point to All Chats**. Its primary workflow systematically guides the user through generating:
1. **`ai-work/OBJECTIVE.md`**: High-level purpose and goals of the session/project.
2. **Root `ai-work/SPEC.md` ("System Bible")**: System-wide specifications, architecture, and scope rules. MUST be generated first if it does not already exist.
3. **Feature Sub-Spec (`ai-work/spec/<topic>-<action>-spec.md`)**: Concrete feature-level specifications branched from the root `ai-work/SPEC.md`.

### Key Protocol Specifications
- **Universal Entry Point**: Every new chat or feature request defaults to `grill-me` protocol initialization.
- **Root Spec Prerequisite Enforcement**: If root `ai-work/SPEC.md` is missing, `grill-me` interviews and writes root `ai-work/SPEC.md` before proceeding to sub-specs.
- **Section-by-Section Interviewing**: Ask dedicated sequential questions for Section 2, Section 3, and Section 4.
- **Immediate Section Writing**: Write approved sections immediately to the file before interviewing the next section.
- **Input Routing & Downstream Tagging**: Route negative constraints to Section 4 (Don'ts) and tag future execution ideas (e.g. `[Tag: Step 1 Plan]`).
- **Mandatory 5-Line Modification Preview**: Present a preview and ask confirmation for any action generating or modifying $> 5$ lines.

---

## 🛠️ 3. Utilities to Use

### Core Technical Utilities
- **Directory Scanning & Environment Awareness**: File discovery tools (`list_dir`, `view_file`) to scan `ai-work/` for existing `OBJECTIVE.md` and root `SPEC.md`.
- **Interview Modal Tool**: `ask_question` tool (rendering interactive multi-choice & write-in questions).
- **File Formats**: Standard GitHub Markdown (`.md`), YAML frontmatter headers for `skills/grill-me/SKILL.md`.
- **Version Control & Hosting**: Git, GitHub CLI (`gh`), repository `git@github.com:alexseif/sandcastles-skills.git`.
- **Global Discovery Symlinks**: `~/.agents` $\rightarrow$ `/home/alexseif/dev/sandcastles-skills`.
- **Naming Schema**: `ai-work/spec/<topic>-<action>-spec.md`, `ai-work/plan/<topic>-<action>-plan.md`, `ai-work/todo/<topic>-<action>-todo.md`, `ai-work/test/<topic>-<action>-test.md`.

### Environment-Aware Decision Workflow
- **If `ai-work/OBJECTIVE.md` / `SPEC.md` Missing**: Commences step-by-step interview to generate `ai-work/OBJECTIVE.md` and root `ai-work/SPEC.md`.
- **If `ai-work/OBJECTIVE.md` & `SPEC.md` Exist**: Presents established context and asks: *"What feature or task are you trying to achieve for this objective?"* to initiate sub-spec.

### Functional Agent Roles Assigned
- **Software Architect Agent**: Guides systemic decision trees, root spec enforcement, and section routing.
- **Technical Writer / Documentation Agent**: Formats and writes approved spec sections immediately into markdown files.

---

## 🛑 4. Scope Boundaries (Do's & Don'ts)

### ✅ Do's
1. **Dedicated `ai-work/` Subdirectory**: Place all AI-generated workflow files separately inside the `ai-work/` working directory:
   - Root Objective: `ai-work/OBJECTIVE.md`
   - Root Spec ("System Bible"): `ai-work/SPEC.md`
   - Sub-Specs: `ai-work/spec/<topic>-<action>-spec.md`
2. **Directory Awareness**: Scan `ai-work/` upon initiating `grill-me` for existing `OBJECTIVE.md` and root `SPEC.md`.
3. **Context Presentation**: Present established `ai-work/OBJECTIVE.md` and root `ai-work/SPEC.md` if they exist before asking for new features.
4. **Immediate Section Writing**: Write approved spec sections immediately into markdown files before interviewing the next section.
5. **5-Line Modification Preview**: Present a preview and request follow-up confirmation for any action generating or modifying $> 5$ lines.
6. **Input Routing & Tagging**: Route negative constraints to Section 4 (Don'ts) and tag future execution ideas (e.g. `[Tag: Step 1 Plan]`).

### ❌ Don'ts
1. **No Root Pollution**: Don't dump AI workflow files outside the `ai-work/` directory hierarchy.
2. **No Work Without Purpose & Spec**: Don't proceed to chat execution or coding without first establishing `ai-work/OBJECTIVE.md` and spec interview.
3. **No Sub-Spec Without Root Spec**: Don't generate sub-specs (`ai-work/spec/<topic>-<action>-spec.md`) unless root `ai-work/SPEC.md` ("System Bible") exists first.
4. **No Bulk Un-Interviewed Generation**: Don't bulk-generate files or spec sections without dedicated, sequential user interviews.
5. **Immutability of Established Rules**: Don't update established objectives or specs without explicit user approval.
6. **No Guessing Ambiguity**: Don't make unverified assumptions — stop and present $\ge 2$ trade-off options for user decision.
