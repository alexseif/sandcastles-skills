# 📋 Feature Specification: Document Skill (`document-skill-spec.md`)

---

## 🎯 1. Objective Alignment
- **Target Objective**: Build and refine the `document` skill runbook to manage project documentation, Architecture Decision Records (ADRs), API docs, README updates, and humanization guidelines saved inside `ai-work/docs/` and project root files.
- **Reference**: Grounded in [`OBJECTIVE.md`](./OBJECTIVE.md) and root [`SPEC.md`](./SPEC.md).

---

## 📝 2. Description of Specifications

### Feature Overview & Primary Goal
The `document` skill systematically manages technical and domain documentation across all AI providers:
1. **Architecture Decision Records (ADRs)**: Standardized logging of structural decisions (`ai-work/docs/adr-<number>-<title>.md`).
2. **Project Documentation & READMEs**: In-place updates to repository `README.md`, developer guides, and API documentation.
3. **Writing & Humanization Guidelines (`humanize` skill integration)**: Enforces clear tone, logical flow, anti-AI writing rules (stripping em dashes `—` and fluff), short paragraphs, bullet points, and target audience alignment.
4. **Egyptian Adab al-Hadith (أدب الحديث)**: Enforces respectful, warm conversational etiquette for READMEs and collaboration files — starting with proper greetings and signing off with courteous thank yous and farewells.
5. **Reproducible Technical Installation Notes**: Technical setup and installation steps must be simple, concise, and 100% reproducible without conversational padding.
6. **Persistent Project Knowledge**: Records complex problem solutions and post-mortems for persistent team learning (`ai-work/docs/solutions/`).

### Key Protocol Specifications
- **Dedicated Subdirectory & Root Edits**: ADRs and runbooks stored in `ai-work/docs/`; repository `README.md` and `CONTRIBUTING.md` updated directly in place.
- **Root Spec Alignment**: All architectural decisions must align with root `ai-work/SPEC.md` ("System Bible").
- **Mandatory 5-Line Modification Preview**: Present a preview and ask confirmation before executing doc updates $> 5$ lines.
- **Semantic Trigger Aliases**: Invoked naturally via *"document this"*, *"write docs"*, *"generate adr"*, *"create documentation"*.

---

## 🛠️ 3. Utilities to Use

### Core Technical Utilities
- **Documentation Formats**: Standard GitHub Flavored Markdown (`.md`), Mermaid architecture/flow diagrams.
- **Skill Definition**: `skills/document/SKILL.md` with YAML frontmatter headers.
- **Version Control & Hosting**: Git, GitHub CLI (`gh`), repository `git@github.com:alexseif/sandcastles-skills.git`.
- **Dedicated Directory**: `ai-work/docs/` for ADRs (`adr-*.md`), solutions (`solutions/`), and technical runbooks.
- **Global Discovery Symlinks**: `~/.agents` $\rightarrow$ `/home/alexseif/dev/sandcastles-skills`.

### Humanization & Anti-AI Writing Protocols (`humanize` skill)
- **Eliminate AI Fingerprints**: Strip AI tropes and tell-tale formatting (e.g., em dashes `—`, fluff phrases, repetitive buzzwords).
- **Natural Reading Flow**: Prioritize effortless, engaging reading flow over rigid academic structures.
- **Formatting Constraints**: Short paragraphs, clear headings, bulleted lists for scannability.
- **Tone & Collaboration**: Precise, clear, and friendly. Include invitations to collaborate and open support channels.
- **Egyptian Adab al-Hadith (أدب الحديث)**: Enforce respectful, warm conversational etiquette — starting with proper greetings and signing off with courteous thank yous and farewells.

### Functional Agent Roles Assigned
- **Technical Writer / Documentation Agent**: Authors ADRs, API docs, system architecture diagrams, and repository READMEs.
- **Humanize / Content Writer Agent**: Applies humanization rules and Egyptian *Adab al-Hadith* communication standards across READMEs and documentation.

---

## 🛑 4. Scope Boundaries (Do's & Don'ts)

### ✅ Do's
1. **Target Directory Boundaries**:
   - Store general project docs, ADRs (`adr-*.md`), and solution runbooks (`solutions/`) inside `ai-work/docs/`.
   - Edit project root files (`README.md`, `CONTRIBUTING.md`) directly in place.
2. **Project-Scoped Content**: Limit all generated documentation strictly to items within the defined scope of the current project.
3. **Differentiated Style Application**:
   - Apply `humanize` skill (warmth, Egyptian *Adab al-Hadith*, invitations to collaborate) to READMEs, introductions, and community/support files.
   - Keep technical installation notes, build commands, and setup instructions **simple, concise, and 100% reproducible steps**.
4. **5-Line Modification Preview**: Present a preview and request follow-up confirmation for any action generating or modifying $> 5$ lines.
5. **Version Control**: Commit all validated documentation updates to GitHub.

### ❌ Don'ts
1. **No Out-of-Scope Bloat**: Don't discuss or document features/technologies outside the current project scope.
2. **No Fluff in Technical Steps**: Don't add conversational fluff or wordy explanations to technical installation, setup, or execution steps.
3. **No AI Tropes**: Don't use tell-tale AI formatting or punctuation (e.g., em dashes `—`, fluff buzzwords, rigid academic phrasing).
4. **No Spec Violation**: Don't document architectural decisions that violate root `ai-work/SPEC.md` ("System Bible").
5. **Immutability of Established Specs**: Don't update established objectives or root specs without explicit user approval.
6. **No Guessing Ambiguity**: Don't make unverified assumptions — stop and present $\ge 2$ trade-off options for user decision.
