# 📝 Todo Breakdown: RAD Skills Suite (`skills/rad-interviewer` & `skills/rad-developer`)

- [ ] Task 1: Environment Preparation
  - **Pre-requisites**: None
  - **Description**: Create directories `skills/rad-interviewer/` and `skills/rad-developer/`.
  - **Validation Steps**: Inspect filesystem with `ls -ld skills/rad-interviewer skills/rad-developer`.

- [ ] Task 2: Implement RAD Interviewer Skill (`skills/rad-interviewer/SKILL.md`)
  - **Pre-requisites**: Task 1 complete
  - **Description**: Create `skills/rad-interviewer/SKILL.md` defining zero-assumption entity inquiry, property and validation multiple-choice interviewing, relationship cardinality/cascade rules, and production SQL DDL generation.
  - **Validation Steps**: Inspect `skills/rad-interviewer/SKILL.md` to confirm YAML frontmatter, execution protocols, and scope boundaries.

- [ ] Task 3: Implement RAD Developer Skill (`skills/rad-developer/SKILL.md`)
  - **Pre-requisites**: Task 2 complete
  - **Description**: Create `skills/rad-developer/SKILL.md` defining preflight checks, read-only DB/SQL schema ingestion, Option B blueprint generation (Doctrine entities/repositories with eager joins, EasyAdmin 4 with autocomplete, and Twig + Vite + SCSS frontend), and ecosystem skills integration.
  - **Validation Steps**: Inspect `skills/rad-developer/SKILL.md` to confirm YAML frontmatter, execution protocols, and scope boundaries.

- [ ] Task 4: Verification & Alignment Audit
  - **Pre-requisites**: Task 3 complete
  - **Description**: Perform full audit of both skill runbooks against `ai-work/spec/skill-rad-interviewer-spec.md` and `ai-work/spec/skill-rad-developer-spec.md`.
  - **Validation Steps**: Verify all requirements across both specs are satisfied without omissions.
