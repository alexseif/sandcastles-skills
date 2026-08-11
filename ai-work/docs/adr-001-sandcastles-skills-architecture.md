# ADR-001: Multi-Provider Governance & Skill Harness Architecture

## Status
Accepted

## Date
2026-08-11

## Context
We need a robust, version-controlled custom skills, rules, and subagent workflow harness (`sandcastles-skills`) on GitHub that enforces disciplined, anti-eager execution across all coding, content writing, email processing, media generation, and research tasks across major AI providers (Gemini, Claude, OpenAI, DeepSeek, Local Models).

Key requirements identified:
- Domain-agnostic purpose establishment before execution.
- Concrete technical specifications grounding all work.
- Ambiguity gatekeeping (stop and present $\ge 2$ trade-off options).
- Mandatory 5-line modification preview & follow-up confirmation.
- Dedicated directory structure for all AI workflow artifacts to prevent root pollution.
- Non-concise user input routing and downstream phase tagging (`[Tag: Step 1 Plan]`).
- Egyptian *Adab al-Hadith* etiquette and humanization rules for documentation.

## Decision
Establish the `sandcastles-skills` repository with the following foundational architecture:

1. **Dedicated `ai-work/` Subdirectory**:
   - `ai-work/OBJECTIVE.md` — High-Level Purpose.
   - `ai-work/SPEC.md` — Root System Specification ("The System Bible").
   - `ai-work/spec/<topic>-<action>-spec.md` — Feature-level sub-specs.
   - `ai-work/plan/<topic>-<action>-plan.md` — Task implementation plans.
   - `ai-work/test/<topic>-<action>-test.md` — Test & verification suites.
   - `ai-work/docs/` — Architecture Decision Records (ADRs) and problem solution runbooks.

2. **Dual Governance Harness (`OBJECTIVE.md` + `SPEC.md`)**:
   - Root `SPEC.md` is mandatory before any feature sub-spec (`<topic>-<action>-spec.md`) can be created.
   - 4-Part `SPEC.md` template: Section 1 Objective Alignment, Section 2 Description, Section 3 Utilities, Section 4 Scope (Do's & Don'ts).

3. **Core Skills Roster Status**:
   - **`grill-me` (Accepted & Built)**: Universal entry point to all chats, handling environment awareness, objective/spec alignment, and 5-line previews.
   - **`document` (Accepted & Built)**: Documentation, ADR logging, README updates, anti-AI humanization, and Egyptian *Adab al-Hadith*.
   - **`plan`, `code`, `review`, `test`, `report` (WIP - Pending Sequential Interview)**: Core lifecycle skills reserved for section-by-section interviewing before file creation.

4. **Multi-Provider Symlinks**:
   - `~/.agents` $\rightarrow$ `/home/alexseif/dev/sandcastles-skills`
   - `AGENTS.md` & `CLAUDE.md` $\rightarrow$ `GEMINI.md`

## Alternatives Considered

### Un-Versioned Loose Skills
- **Pros**: Quick to modify locally.
- **Cons**: No git history, no backup, hard to share across machines.
- **Rejected**: Failed requirement for version control and GitHub tracking.

### Monolithic Single Spec
- **Pros**: Easy to write initially.
- **Cons**: Becomes bloated, causes file collisions as features expand.
- **Rejected**: Sub-specs with `<topic>-<action>-spec.md` naming schema provide clean modularity and collision prevention.

### In-Root Workflow Files
- **Pros**: Direct visibility in project root.
- **Cons**: Pollutes repository root with temporary or execution files.
- **Rejected**: Isolating all AI workflow artifacts in `ai-work/` keeps repositories clean.

## Consequences
- Every AI model (Gemini, Claude, OpenAI, DeepSeek) reading `GEMINI.md`, `AGENTS.md`, or `CLAUDE.md` obeys identical governance.
- ADRs stored in `ai-work/docs/` capture architectural intent permanently for future team members and AI agents.
