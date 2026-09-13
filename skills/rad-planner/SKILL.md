---
name: rad-planner
description: >-
  Preflight verification and planning engine for Rapid Application Development (RAD) in Symfony 6.4 LTS.
  Executes runtime and agent skill preflights, logs to ai-work/rad-development/preflight.log,
  ingests database schemas into an entities.json manifest, generates the sequential execution plan (plan.md),
  and creates a git commit ready for rad-developer execution.
  Aliases: rad plan, rad planner, plan rad, prepare rad.
---

# 📋 RAD Planner Skill (`rad-planner`)

The `rad-planner` skill serves as the **mandatory preparation gateway** for Rapid Application Development on **Symfony 6.4 LTS**. It verifies the development environment and ecosystem agent skills, logs audit traces, ingests the database schema into a structured `entities.json` catalog, creates a checklist-driven `plan.md`, and commits the initial state so `rad-developer` can execute safely.

---

## 🛑 Scope Boundaries (Do's & Don'ts)

### ✅ Do's
1. **Mandatory Preflight Checks**: Verify system binaries, runtime extensions, Composer packages, Node packages, and required agent skills before creating any plan.
2. **Audit Logging**: Write complete preflight stdout/stderr and timestamps to `ai-work/rad-development/preflight.log`.
3. **Structured Entity Manifest**: Generate `ai-work/rad-development/entities.json` cataloging all tables, columns, data types, and foreign key relations.
4. **Execution Checklist**: Produce `ai-work/rad-development/plan.md` ordering every task from layout setup to the final entity.
5. **Git Commit on Completion**: Create an atomic Git commit at the end of planning before handing off to `rad-developer`.

### ❌ Donts
1. **No Code Implementation**: Do NOT generate PHP, Twig, SCSS, or EasyAdmin code; all code generation is strictly delegated to `rad-developer`.
2. **No Unverified Planning**: Never generate a plan if preflight dependencies or the database schema are missing.
3. **No Destructive DB Operations**: Live database introspection must be strictly read-only.

---

## 📜 Execution Protocols

### Step 1: Directory Setup & Preflight Verification
Create the artifact directory:
```bash
mkdir -p ai-work/rad-development
```

Execute all checks and record output to `ai-work/rad-development/preflight.log`:

1. **Ecosystem Agent Skills Check**:
   Inspect `.skill-lock.json` and `skills/`. Install if missing:
   ```bash
   npx skills add dev-toolings/superpowers-symfony@symfony:doctrine-relations
   npx skills add kgslotwinski/skills@easy-admin-bundle
   npx skills add mindrally/skills@scss-best-practices
   npx skills add antfu/skills@vite
   ```
2. **Runtime & System Packages**:
   - PHP >= 8.2 (extensions: `pdo`, `intl`, `mbstring`).
   - Composer, Node >= 18, npm >= 9.
3. **Composer Application Packages (`composer.json`)**:
   - `symfony/orm-pack`, `symfony/maker-bundle`, `easycorp/easyadmin-bundle`, `pentatrion/vite-bundle`, `symfony/validator`, `symfony/form`, `symfony/twig-bundle`.
4. **Node Packages (`package.json`)**:
   - `vite`, `sass`.

*If any dependency is missing, halt execution immediately and output the exact command to install them.*

---

### Step 2: Schema Ingestion & Entity Catalog (`entities.json`)
Ingest schema from `schema.sql` (or output of `rad-interviewer`), a read-only live DB, or a spec file. Generate `ai-work/rad-development/entities.json`:

```json
{
  "project": "app_name",
  "planned_at": "2026-09-13T15:30:00Z",
  "preflight_passed": true,
  "entities": [
    {
      "name": "Customer",
      "table": "customers",
      "status": "pending",
      "relations": [
        { "property": "orders", "type": "OneToMany", "target": "Order" }
      ]
    },
    {
      "name": "Order",
      "table": "orders",
      "status": "pending",
      "relations": [
        { "property": "customer", "type": "ManyToOne", "target": "Customer" }
      ]
    }
  ]
}
```

---

### Step 3: Phased Execution Plan Generation (`plan.md`)
Generate `ai-work/rad-development/plan.md` with sequentially ordered tasks:

```markdown
# 📋 RAD Execution Plan: [Project Name]

- [x] Phase 0: Preflight verification logged (`ai-work/rad-development/preflight.log`)
- [x] Phase 1: Schema ingested and entity manifest created (`entities.json`)
- [ ] Phase 2: Setup EasyAdmin Dashboard & Base Layout
- [ ] Phase 3: Entity: Customer (Model, Repository, EasyAdmin CRUD, Frontend)
- [ ] Phase 4: Entity: Order (Model, Repository, EasyAdmin CRUD, Frontend)
- [ ] Phase 5: Final validation & schema integrity check
```

---

### Step 4: Finalization & Git Commit
Commit the planning artifacts to version control:
```bash
git add ai-work/rad-development/
git commit -m "docs(rad): complete preflight, entities manifest, and execution plan"
```
