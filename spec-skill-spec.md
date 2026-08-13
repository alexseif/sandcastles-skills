# 📋 Feature Specification: Spec Skill (`spec-skill-spec.md`)

---

## 🎯 1. Objective Alignment
- **Target Objective**: Build and refine the `spec` skill runbook as the technical software architecture authoring engine that generates complete, unambiguous specification documents (`ai-work/spec/<topic>-<action>-spec.md`) for AI coders, software engineers, and functional subagents.
- **Reference**: Grounded in `OBJECTIVE.md` and root `SPEC.md`.

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
- **Mandatory 5-Line Modification Preview**: Present a preview and ask confirmation before writing spec sections >5 lines.
- **Semantic Trigger Aliases**: Invoked naturally via "write spec", "create specification", "technical spec", "spec this feature".

---

## 🛠️ 3. Utilities to Use

### Core Technical Utilities
- **Diagramming & Visual Flow**: Mermaid visual flowcharts, DevOps/infrastructure deployment diagrams, and written step-by-step logic flows.
- **Data Structure Schemas**: Structured JSON or YAML schemas (enforcing exact data model contracts once field properties are detailed with the user).
- **Specification Formats**: Standard GitHub Flavored Markdown (`.md`), YAML frontmatter headers for `skills/spec/SKILL.md`.
- **Interactive Interview Modal**: `ask_question` tool for property-by-property field detailing.
- **Version Control & Hosting**: Git, GitHub CLI (`gh`), repository `git@github.com:alexseif/sandcastles-skills.git`.
- **Dedicated Directory**: Sub-specs stored strictly in `ai-work/spec/<topic>-<action>-spec.md`.
- **Global Discovery Symlinks**: `~/.agents` → `/home/alexseif/dev/sandcastles-skills`.

### Functional Agent Roles Assigned
- **Software Architect Agent**: Guides architectural design trees, subsystem component definitions, and boundary controls.
- **Technical Specification Agent**: Authors complete, unambiguous technical specs tailored for AI coders and software engineers.

## 📏 4. Scope Boundaries (Do’s & Don’ts)

### ✅ Do (s)

- **Align with Objective** – Every spec must reference `ai-work/OBJECTIVE.md` and the root `ai-work/SPEC.md`.
- **Interview First** – Before any database table, JSON/YAML schema, or data‑model is documented, the user must be interviewed **field‑by‑field**.
- **Domain Selection** – At the start of the spec interview, present a **Domain‑Aware Question Dispatcher** that asks the user to choose one of the supported domains:
  - **Software** – Uses the existing software‑architecture questionnaire.
  - **Finance** – Prompts for financial‑advisor specifics (e.g., KPIs, regulatory constraints, risk‑management policies).
  - **Marketing** – Prompts for market‑analysis, target‑audience, campaign goals, budget allocations, etc.
- **Visual Diagrams** – Only generate Mermaid flowcharts, DevOps diagrams, or structured JSON/YAML schemas **after the user approves** the domain‑specific questionnaire.
- **Preview > 5 Lines** – Show a preview and request explicit confirmation for any spec‑section change that exceeds five lines.
- **File Placement** – All sub‑spec files must live under `ai‑work/spec/<topic>-<action>-spec.md`.
- **No Premature Coding** – Do not start implementation code until the full spec is signed off.

### 🚫 Don’t (s)

- **Invent Schemas** – Never create database tables, JSON/YAML schemas, or data‑model properties without a prior user interview for each field.
- **Skip Root Spec Check** – Do not create a sub‑spec unless the root `ai-work/SPEC.md` (“System Bible”) already exists.
- **Add Unverified Assumptions** – Do not include speculative designs or undocumented requirements.
- **Edit >5 Lines Without Consent** – Never modify a file with more than five lines without the user’s explicit approval.
- **Use Religious or Non‑English Text** – Keep all content English‑only unless the user explicitly requests otherwise.
- **Hard‑code Future Domains** – Adding a new domain requires updating the dispatcher’s question‑set list, not ad‑hoc modifications in other sections.
