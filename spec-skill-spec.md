# 📋 Feature Specification: Spec Skill (`spec-skill-spec.md`)

---

## 🎯 1. Objective Alignment
- **Target Objective**: Build and refine the `spec` skill runbook as the technical software architecture authoring engine that generates complete, unambiguous specification documents (`ai-work/spec/<topic>-<action>-spec.md`) for AI coders, software engineers, and functional subagents.
- **Reference**: Grounded in [`OBJECTIVE.md`](./OBJECTIVE.md) and root [`SPEC.md`](./SPEC.md).

---

## 📝 2. Description of Specifications

### Feature Overview & Primary Goal
The `spec` skill systematically authors technical software architecture specifications:
1. **Target Audience**: Written specifically for AI coders, software engineers, and automated agents to fully grasp feature purpose, objective alignment, architectural design, visual flow, and desired end results.
2. **Mandatory 4-Part Structure**: Enforces Section 1 Objective Alignment, Section 2 Description, Section 3 Utilities, Section 4 Scope (Do's & Don'ts).
3. **No Un-Interviewed Schemas**: Strictly forbids generating database tables, data models, or JSON/YAML schemas without detailing exact properties, fields, and types with the user during section-by-section interviewing.
4. **Visual & Architectural Diagrams**: Incorporates Mermaid flowcharts, DevOps infrastructure diagrams, written visual flows, and structured JSON/YAML schemas to enforce data contracts.
5. **Downstream Tagging**: Tags schema detailing and task execution constraints for downstream consumption (`[Tag: Step 1 Plan]`).

### Key Protocol Specifications
- **Dedicated Directory**: Outputs sub-specs strictly to `ai-work/spec/<topic>-<action>-spec.md`.
- **Root Spec Prerequisite**: Cannot create sub-specs unless root `ai-work/SPEC.md` ("System Bible") exists.
- **Mandatory 5-Line Modification Preview**: Present a preview and ask confirmation before writing spec sections $> 5$ lines.
- **Semantic Trigger Aliases**: Invoked naturally via *"write spec"*, *"create specification"*, *"technical spec"*, *"spec this feature"*.

---

## 🛠️ 3. Utilities to Use

### Core Technical Utilities
- **Diagramming & Visual Flow**: Mermaid visual flowcharts, DevOps/infrastructure deployment diagrams, and written step-by-step logic flows.
- **Data Structure Schemas**: Structured JSON or YAML schemas (enforcing exact data model contracts once field properties are detailed with the user).
- **Specification Formats**: Standard GitHub Flavored Markdown (`.md`), YAML frontmatter headers for `skills/spec/SKILL.md`.
- **Interactive Interview Modal**: `ask_question` tool for property-by-property field detailing.
- **Version Control & Hosting**: Git, GitHub CLI (`gh`), repository `git@github.com:alexseif/sandcastles-skills.git`.
- **Dedicated Directory**: Sub-specs stored strictly in `ai-work/spec/<topic>-<action>-spec.md`.
- **Global Discovery Symlinks**: `~/.agents` $\rightarrow$ `/home/alexseif/dev/sandcastles-skills`.

### Functional Agent Roles Assigned
- **Software Architect Agent**: Guides architectural design trees, subsystem component definitions, and boundary controls.
- **Technical Specification Agent**: Authors complete, unambiguous technical specs tailored for AI coders and software engineers.
