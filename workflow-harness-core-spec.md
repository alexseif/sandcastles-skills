# 📋 Feature Specification: Workflow Harness Core (`workflow-harness-core-spec.md`)

---

## 🎯 1. Objective Alignment
- **Target Objective**: Build, version, and continuously refine a multi-domain, multi-provider AI agent workflow harness (`sandcastles-skills`) on GitHub that enforces disciplined execution across all coding, content, email, media, and research tasks across major AI providers (Gemini, Claude, OpenAI, DeepSeek, Local LLMs).
- **Reference**: Documented in [`OBJECTIVE.md`](./OBJECTIVE.md).

---

## 📝 2. Description of Specifications

### Feature Overview
Build and structure the multi-provider, multi-domain workflow harness inside `sandcastles-skills`:

1. **Multi-Provider AI Compatibility**:
   - Support for Google Gemini, Anthropic Claude, OpenAI GPT-4, DeepSeek, and Local Models (Ollama/LM Studio).
   - Cross-compatible markdown governance (`GEMINI.md`, `AGENTS.md`, `CLAUDE.md`).

2. **Global Governance (`GEMINI.md` / `AGENTS.md`)**:
   - Universal Objective-First (`OBJECTIVE.md`) & Spec-First (`<topic>-<action>-spec.md`) dual-harness.
   - Ambiguity gatekeeping (stop & present $\ge 2$ trade-off options).
   - Mandatory 5-line modification follow-up confirmation.
   - Section-by-section spec interview protocol.

3. **Core Workflow Skills Roster (`skills/`)**:
   - Customizable skill runbooks for planning, implementation, code review, testing, and reporting.

4. **Modular Tech Stack Rules (`rules/`)**:
   - Stack-specific guidelines for Node/TypeScript (`node-ts.md`), PHP (`php.md`), Python (`python.md`), and Go (`go.md`).
