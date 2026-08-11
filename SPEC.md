# 📋 Concrete Specifications (`SPEC.md`)

---

## 🎯 1. Objective Alignment
- **Target Objective**: Build, version, and continuously refine a multi-domain, multi-provider AI agent workflow harness (`sandcastles-skills`) on GitHub that enforces disciplined execution across all coding, content, email, media, and research tasks across major AI providers (Gemini, Claude, OpenAI, DeepSeek, Local Models), while strictly limiting AI eagerness to a defined scope of work.
- **Reference**: Documented in [`OBJECTIVE.md`](./OBJECTIVE.md).

---

## 📝 2. Description of Specifications

### System Specifications
Build and structure the multi-provider, multi-domain workflow harness inside `sandcastles-skills`:

1. **Global Governance (`GEMINI.md`)**:
   - Universal Objective-First (`OBJECTIVE.md`) & Spec-First (`SPEC.md` / `<topic>-<action>-spec.md`) dual-harness.
   - **Root Spec Prerequisite**: Sub-specs (`<topic>-<action>-spec.md`) CANNOT be created unless the general root `SPEC.md` ("System Bible") exists first.
   - **Immediate Section Writing**: As each section of a spec is approved, write it immediately to the file before moving to interview the next section.
   - **Input Routing & Downstream Tagging**: Route constraints to appropriate sections and tag future execution ideas (`[Tag: Step 1 Plan]`).
   - Anti-eagerness protocols restricting AI execution to defined scope boundaries.
   - Ambiguity gatekeeping (stop & present $\ge 2$ trade-off options).
   - Mandatory 5-line modification follow-up confirmation.

2. **Multi-Provider AI Support**:
   - Cross-provider markdown configurations (`GEMINI.md`, `AGENTS.md`, `CLAUDE.md`).
   - Compatibility across Google Gemini, Anthropic Claude, OpenAI GPT-4, DeepSeek, and Local LLMs (Ollama / LM Studio).

3. **Modular Skills & Rules Roster**:
   - `skills/` folder containing custom workflow skill runbooks.
   - `rules/` folder containing modular tech-stack guidelines (`node-ts.md`, `php.md`, `python.md`, `go.md`).

---

## 🛠️ 3. Utilities to Use

### Core Technical Utilities
- **Version Control & Hosting**: Git, GitHub CLI (`gh`), repository `git@github.com:alexseif/sandcastles-skills.git`.
- **Global Discovery Symlinks**: `~/.agents` $\rightarrow$ `/home/alexseif/dev/sandcastles-skills`.
- **Cross-Model Governance Symlinks**: `AGENTS.md` and `CLAUDE.md` $\rightarrow$ `GEMINI.md`.
- **File Formats & Structure**: Standard GitHub Markdown (`.md`), YAML frontmatter headers.
- **Naming Schemas**: `<topic>-<action>-spec.md`, `<topic>-<action>-plan.md`, `<topic>-<action>-todo.md`, `<topic>-<action>-test.md`.
- **Supported AI Models & Tools**: Google Gemini, Anthropic Claude, OpenAI GPT-4, DeepSeek, Local LLMs (Ollama / LM Studio).

### Functional Agent Roles Assigned
- **Software Architect Agent**: Defines root system architecture, specification structures, and governance rules.
- **Technical Writer / Documentation Agent**: Maintains clear technical specifications, runbooks, and ADRs.
- **Content Writer Agent**: Generates domain content, workflow guidelines, and user-facing documentation.

---

## 🛑 4. Scope Boundaries (Do's & Don'ts)

### ✅ Do's
1. **Workspace Boundary**: Restrict all file operations to the workspace project directory and the `~/.agents` / `~/.gemini` discovery symlinks.
2. **Context Inquiry**: Ask the user where content is hosted, end result expectations, and align them explicitly with `OBJECTIVE.md`.
3. **5-Line Modification Preview**: Present a preview and request follow-up confirmation for any action generating or modifying $> 5$ lines.
4. **Version Control**: Push all validated changes to the GitHub repository `sandcastles-skills`.

### ❌ Don'ts
1. **No Spec Without Objective**: Don't generate `SPEC.md` or any sub-spec without an established `OBJECTIVE.md`.
2. **No Sub-Spec Without Root Spec**: Don't generate sub-specs (`<topic>-<action>-spec.md`) unless the general root `SPEC.md` ("The System Bible") exists first.
3. **Separation of Concerns**: Don't pollute specs with out-of-scope items. If an item is out of scope, advise the user to place it in its respective workflow or separate sub-spec.
4. **Immutability of Established Rules**: Don't update `OBJECTIVE.md`, root `SPEC.md`, or created sub-specs without explicit user approval. Treat them as established rules to strictly obey.
5. **No Guessing Ambiguity**: Don't make unverified assumptions — stop and present $\ge 2$ trade-off options for user decision.
