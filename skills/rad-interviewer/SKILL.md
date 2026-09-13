---
name: rad-interviewer
description: >-
  Interactive architectural interview skill that designs relational database schemas entity-by-entity, property-by-property, and relation-by-relation without assumptions.
  Generates clean, production-ready SQL DDL schema files (schema.sql) for rapid application development.
  Aliases: interview schema, design database, rad interview, create schema, architectural interview.
---

# 📐 RAD Interviewer Skill (`rad-interviewer`)

The `rad-interviewer` skill conducts a disciplined, zero-assumption architectural interview to design a normalized relational database schema. It systematically explores entities, properties, constraints, and relationships with explicit multi-choice options, outputting a complete, production-ready SQL DDL file (`schema.sql`).

---

## 🛑 Scope Boundaries (Do's & Don'ts)

### ✅ Do's
1. **Zero-Assumption Inquiry**: Ask explicitly about every entity, field, type, and relation. Never guess or silently fill in schema details.
2. **Always Provide Options**: Present explicit options when interviewing on data types, nullability, unique keys, and relationship cardinalities.
3. **Foreign Key Integrity**: Enforce explicit foreign key definitions, target tables/columns, and `ON DELETE` actions (`CASCADE`, `SET NULL`, `RESTRICT`).
4. **Normalized SQL Output**: Produce clean, standard SQL DDL with proper primary keys, foreign keys, table comments, and indexing.

### ❌ Don'ts
1. **No Silent Additions**: Do not inject unrequested tables, columns, or relations without asking the user first.
2. **No Implementation Code**: Do NOT generate PHP, Symfony, Twig, or JS code during this interview phase; produce strictly the SQL schema artifact.
3. **No Unstructured Descriptions**: Do not leave requirements in ambiguous prose; resolve them into exact SQL definitions.

---

## 📜 Execution Protocols

### 1. Entity Discovery Protocol (Phase 1)
- Prompt the user to specify domain entities:
  > *"What are the core entities/tables for this application? (List them one by one or provide the domain overview)."*
- Catalog the confirmed entities before drilling into field-level details.

### 2. Field & Property Interview Protocol (Phase 2)
For each confirmed entity, interview the user field-by-field, asking:
- **Field Name**: In lowercase snake_case (e.g. `first_name`, `published_at`).
- **Data Type Options**: Present explicit options:
  - Numeric: `INT`, `BIGINT`, `DECIMAL(10,2)`, `FLOAT`
  - Textual: `VARCHAR(255)`, `VARCHAR(n)`, `TEXT`, `LONGTEXT`
  - Temporal: `DATETIME`, `DATE`, `TIMESTAMP`
  - Logical/Structural: `BOOLEAN`, `JSON`
- **Nullability**: `NOT NULL` (default) vs. `NULL`.
- **Key Constraints**: Primary Key (Auto-increment vs. UUID), Unique Constraint, or Index.
- **Validation Rules**: Minimum/maximum lengths, regex patterns, positive-only numbers.

### 3. Relationship & Cardinality Protocol (Phase 3)
For every connected pair of entities, ask explicit clarifying questions:
- **Cardinality Options**:
  - `ManyToOne` (e.g. Order belongs to User)
  - `OneToMany` (e.g. User has many Orders)
  - `ManyToMany` (e.g. Product belongs to many Categories, via join table)
  - `OneToOne` (e.g. User has one Profile)
- **Cascade & Deletion Behavior Options**:
  - `ON DELETE RESTRICT` (disallow deletion of parent if children exist)
  - `ON DELETE CASCADE` (delete children automatically when parent is deleted)
  - `ON DELETE SET NULL` (nullify foreign key in child records)

### 4. SQL Schema File Generation (Phase 4)
Compile all confirmed entities, attributes, and relationships into a standard SQL DDL file:
- Target File: `schema.sql` (or `ai-work/schema/<project>-schema.sql`).
- Syntax Standards:
  - Standard ANSI / MySQL 8.0+ syntax (`ENGINE=InnoDB DEFAULT CHARSET=utf8mb4`).
  - Explicit `PRIMARY KEY` and `FOREIGN KEY` constraint blocks.
  - Performance indexes on all foreign keys and frequently filtered columns.
