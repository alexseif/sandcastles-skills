# 📋 Concrete Specifications (`SPEC.md`)

---

## 🎯 1. Objective Alignment
- **Target Objective**: Build, version, and continuously refine a modular, multi-domain AI agent workflow harness (`sandcastles-skills`) on GitHub that enforces disciplined execution across all coding, content, email, media, and research tasks.
- **Reference**: Documented in [`OBJECTIVE.md`](./OBJECTIVE.md).

---

## 📝 2. Description of Specifications
Detailed specifications for the `sandcastles-skills` repository ecosystem:
- Global system governance defined via `GEMINI.md`.
- Objective-First (`OBJECTIVE.md`) and Specification-First (`SPEC.md`) dual-harness.
- Custom workflow skills roster in `skills/<name>/SKILL.md`.
- Modular tech stack guidelines in `rules/<stack>.md`.
- Ambiguity gatekeeping (stop & present $\ge 2$ options with trade-offs).
- Mandatory 5-line modification follow-up confirmation.

---

## 🛠️ 3. Utilities to Use
- **Version Control & Hosting**: Git, GitHub CLI (`gh`), repository `git@github.com:alexseif/sandcastles-skills.git`.
- **Global Discovery**: Symlink `~/.agents` $\rightarrow$ `/home/alexseif/dev/sandcastles-skills`.
- **Target Subagents**: `planner`, `coder`, `reviewer`, `tester`, `reporter`.
- **File Formats**: Standard GitHub Markdown (`.md`), YAML Frontmatter (`SKILL.md`), Shell Scripts (`.sh`).

---

## 🛑 4. Scope Boundaries (Do's & Don'ts)

### ✅ Do's
- Do establish `OBJECTIVE.md` (high-level purpose) and `SPEC.md` (specifications) before executing work.
- Do present previews and ask confirmation for actions modifying $> 5$ lines.
- Do enforce isolated, testable single tasks.
- Do push all validated updates to GitHub repository `sandcastles-skills`.

### ❌ Don'ts
- Don't start coding, writing, or modifying files without an established objective and spec.
- Don't refactor adjacent systems or delete existing code without explicit user approval.
- Don't guess ambiguous requirements — stop and present 2 options with trade-offs.
