# 📋 Feature Specification: Spec Skill (`spec-skill-spec.md`)

---

## 🎯 1. Objective Alignment
- **Target Objective**: Build and refine the `spec` skill runbook as the technical software architecture authoring engine that generates complete, unambiguous specification documents (`ai-work/spec/<topic>-<action>-spec.md`) for AI coders, software engineers, and functional subagents.
- **Reference**: Grounded in [`OBJECTIVE.md`](./OBJECTIVE.md) and root [`SPEC.md`](./SPEC.md).

---

## 📝 2. Description of Specifications

### Feature Overview & Primary Goal
The `spec` skill systematically authors technical software architecture specifications:
1. **Target Audience**: Written specifically for AI coders, software engineers, and automated agents to fully grasp feature purpose, objective alignment, architectural design, and desired end results.
2. **Mandatory 4-Part Structure**: Enforces Section 1 Objective Alignment, Section 2 Description, Section 3 Utilities, Section 4 Scope (Do's & Don'ts).
3. **No Un-Interviewed Schemas**: Strictly forbids generating database tables, data models, or JSON/Proto schemas without detailing exact properties, fields, and types with the user during section-by-section interviewing.
4. **Downstream Tagging**: Tags schema detailing and task execution constraints for downstream consumption (`[Tag: Step 1 Plan]`).

### Key Protocol Specifications
- **Dedicated Directory**: Outputs sub-specs strictly to `ai-work/spec/<topic>-<action>-spec.md`.
- **Root Spec Prerequisite**: Cannot create sub-specs unless root `ai-work/SPEC.md` ("System Bible") exists.
- **Mandatory 5-Line Modification Preview**: Present a preview and ask confirmation before writing spec sections $> 5$ lines.
- **Semantic Trigger Aliases**: Invoked naturally via *"write spec"*, *"create specification"*, *"technical spec"*, *"spec this feature"*.
