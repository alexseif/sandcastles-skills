# 📋 Feature Specification: RAD Interviewer Skill (`skills/rad-interviewer/SKILL.md`)

---

## 🎯 1. Objective Alignment
- **Target Objective**: Create an interactive architectural interview skill (`rad-interviewer`) that systematically guides the user through designing a relational database schema entity-by-entity, property-by-property, and relation-by-relation without making assumptions or silent additions, outputting a complete, production-ready SQL schema file (`schema.sql`).
- **Reference**: Grounded in [`OBJECTIVE.md`](../../OBJECTIVE.md) and [`SPEC.md`](../../SPEC.md).

---

## 📝 2. Description of Specifications

### Core Interview Protocols
1. **Zero-Assumption Entity Discovery**:
   - Ask the user to define domain entities one by one. Never infer or invent entities.
2. **Property & Validation Interview**:
   - For every column/property, explicitly present multiple-choice options for:
     - SQL Data Type (`INT`, `BIGINT`, `VARCHAR(n)`, `TEXT`, `BOOLEAN`, `DECIMAL(p,s)`, `DATETIME`, `JSON`).
     - Nullability (`NOT NULL` vs. `NULL`).
     - Uniqueness & Primary Key designation.
     - Default values.
     - Validation rules (e.g. email, positive number, length boundaries).
3. **Relationship & Constraint Disambiguation**:
   - For each relationship, explicitly present options:
     - Cardinality: `ManyToOne`, `OneToMany`, `ManyToMany`, `OneToOne`.
     - Foreign Key Actions: `ON DELETE CASCADE`, `ON DELETE SET NULL`, `ON DELETE RESTRICT`.
     - Join table specification for `ManyToMany`.
4. **SQL Schema Output**:
   - Write the finalized schema to a clean SQL file (e.g. `ai-work/schema/<project>-schema.sql` or `schema.sql`) with valid DDL, primary keys, foreign key constraints, and performance indexes.

---

## 🛠️ 3. Utilities to Use
- **Interactive Question Tool**: `ask_question` for multi-choice field types, constraints, and relationships.
- **File Utilities**: `write_to_file` to produce the validated `.sql` DDL schema.

---

## 🛑 4. Scope Boundaries (Do's & Don'ts)

### ✅ Do's
1. **Explicit Options**: Always provide options when asking about data types, constraints, or relations.
2. **Normalized DDL**: Generate standard SQL with explicit foreign key constraints, column lengths, and table engines.
3. **Save Complete Artifact**: Ensure the final SQL file is completely valid and ready for consumption by `rad-developer`.

### ❌ Don'ts
1. **No Assumptions**: Never guess field types, nullability, or relationships.
2. **No Code Implementation**: Do NOT generate PHP, Twig, or Symfony files during this interview skill.
