# 📋 Feature Specification: Document Skill (`document-skill-spec.md`)

---

## 🎯 1. Objective Alignment
- **Target Objective**: Build and refine the `document` skill runbook to manage project documentation, Architecture Decision Records (ADRs), API docs, README updates, and humanization guidelines saved inside `ai-work/docs/`.
- **Reference**: Grounded in [`OBJECTIVE.md`](./OBJECTIVE.md) and root [`SPEC.md`](./SPEC.md).

---

## 📝 2. Description of Specifications

### Feature Overview & Primary Goal
The `document` skill systematically manages technical and domain documentation across all AI providers:
1. **Architecture Decision Records (ADRs)**: Standardized logging of structural decisions (`ai-work/docs/adr-<number>-<title>.md`).
2. **Project Documentation & READMEs**: Automated updates to repository `README.md`, developer guides, and API documentation.
3. **Writing & Humanization Guidelines**: Enforces clear tone, logical flow, anti-fluff rules, and target audience alignment.
4. **Persistent Project Knowledge**: Records complex problem solutions and post-mortems for persistent team learning (`ai-work/docs/solutions/`).

### Key Protocol Specifications
- **Dedicated Subdirectory**: All generated docs stored separately in `ai-work/docs/`.
- **Root Spec Alignment**: All architectural decisions must align with root `ai-work/SPEC.md` ("System Bible").
- **Mandatory 5-Line Modification Preview**: Present a preview and ask confirmation before executing doc updates $> 5$ lines.
- **Semantic Trigger Aliases**: Invoked naturally via *"document this"*, *"write docs"*, *"generate adr"*, *"create documentation"*.
