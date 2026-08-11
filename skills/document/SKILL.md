---
name: document
description: >-
  Documentation management and humanization skill. Manages ADRs in ai-work/docs/,
  in-place README updates, anti-AI writing rules (no em dashes —, short paragraphs, bullet points),
  reproducible technical installation steps, and respectful English conversational etiquette.
  Aliases: document this, write docs, generate adr, create documentation.
---

# 📚 Document Skill (`document`)

The `document` skill governs project documentation, Architecture Decision Records (ADRs), repository README updates, and anti-AI humanization protocols.

---

## 📜 Execution Protocols

### 1. Humanization & Anti-AI Writing Engine (`humanize` skill)
When generating READMEs, introductions, and community/collaboration docs:
- **Default Language**: Default strictly to English for all greetings, documentation, and communication unless explicitly instructed otherwise.
- **Warm & Respectful Etiquette**: Enforce polite, warm, and friendly etiquette — starting with respectful greetings (e.g. *"Warm greetings"*, *"Peace and welcome"*) and closing with courteous farewells (e.g. *"With gratitude and warm regards"*, *"Blessings and best wishes"*).
- **Eliminate AI Fingerprints**: Strip tell-tale AI formatting and punctuation (e.g. em dashes `—`, repetitive transitions like "delve", "realm", "testament").
- **Readability & Ease of Flow**: Prioritize natural, engaging reading flow over rigid academic structure.
- **Formatting Constraints**: Short, punchy paragraphs; clear section headers; bulleted lists for easy scanning.
- **Collaboration & Support**: Include warm, explicit invitations to collaborate and open support/community channels.

---

### 2. Differentiated Technical Installation & Setup Rules
When writing technical setup steps, build commands, or installation notes:
- **Concise & Reproducible**: Keep installation steps simple, concise, and 100% reproducible.
- **No Conversational Padding**: Omit conversational fluff, greetings, or wordy explanations from technical installation steps and code blocks.

---

### 3. Architecture Decision Records (ADRs) & Solutions (`ai-work/docs/`)
- **ADR Format**: Store structural decision logs in `ai-work/docs/adr-<number>-<title>.md` following standard ADR templates (Context, Decision, Consequences).
- **Persistent Problem Solutions**: Log complex bug post-mortems and solutions in `ai-work/docs/solutions/` for persistent team learning.

---

### 4. In-Place Repository README Updates
- Edit project root files (`README.md`, `CONTRIBUTING.md`) directly in place.
- Align all documented features strictly with the scope defined in `ai-work/OBJECTIVE.md` and root `ai-work/SPEC.md`.

---

### 5. Mandatory 5-Line Modification Follow-Up Rule
- Whenever generating or editing documentation exceeding **5 lines**:
  - Show a preview snippet.
  - Ask mandatory confirmation: *"Would you like to add, remove, or modify anything in this selected action before we proceed?"*

---

### 6. Semantic Trigger Aliases
Invoked naturally via: *"document this"*, *"write docs"*, *"generate adr"*, *"create documentation"*.
