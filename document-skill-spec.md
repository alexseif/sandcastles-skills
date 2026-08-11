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
3. **Writing & Humanization Guidelines (`humanize` skill integration)**: Enforces clear tone, logical flow, anti-AI writing rules (stripping em dashes `—` and fluff), short paragraphs, bullet points, and target audience alignment.
4. **Egyptian Adab al-Hadith (أدب الحديث)**: Enforces respectful, warm conversational etiquette — starting with proper greetings and signing off with courteous thank yous and farewells.
5. **Persistent Project Knowledge**: Records complex problem solutions and post-mortems for persistent team learning (`ai-work/docs/solutions/`).

### Key Protocol Specifications
- **Dedicated Subdirectory**: All generated docs stored separately in `ai-work/docs/`.
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
