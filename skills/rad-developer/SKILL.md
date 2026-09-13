---
name: rad-developer
description: >-
  Rapid Application Development (RAD) generator for Symfony 6.4 LTS with state-recovery and atomic git workflow.
  Logs preflight to ai-work/rad-development/preflight.log, generates an entities.json catalog and execution plan,
  supports resumption from failure, scaffolds via Symfony Maker CLI, and refactors to enterprise standards:
  EasyAdmin 4 with autocomplete, Twig + Vite + SCSS frontend, and Doctrine ORM with eager joins (N+1 query prevention).
  Aliases: rad build, rad dev, scaffold symfony, generate crud, easyadmin scaffold.
---

# ⚡ RAD Developer Skill (`rad-developer`)

The `rad-developer` skill rapidly constructs production-grade web applications on **Symfony 6.4 LTS** from a database schema. It operates with a **crash-resilient state machine**, logging execution audits, generating an entity catalog and todo checklist, committing incrementally after every task, and supporting resumption from where it left off in case of interruptions.

---

## 🏛️ 1. Core Architecture & Technology Stack

```
┌───────────────────────────────────────────────────────────────┐
│                       Presentation Layer                      │
├───────────────────────────────┬───────────────────────────────┤
│    Admin Panel (Backend)      │     Client App (Frontend)     │
│       EasyAdmin 4 CRUD        │     Twig + SCSS (BEM) + JS    │
│   (Auto-configured Fields)    │       Vite Bundle Pipeline    │
├───────────────────────────────┴───────────────────────────────┤
│                      Application / Domain                     │
│          Symfony 6.4 LTS (Controllers, Forms, Voters)         │
├───────────────────────────────────────────────────────────────┤
│                       Persistence Layer                       │
│    Doctrine ORM 3.x (Entities, Custom Repositories, DQL)     │
│            MySQL 8.0+ / PostgreSQL 15+ Database               │
└───────────────────────────────────────────────────────────────┘
```

1. **Framework Core**: **Symfony 6.4 LTS** (supported through Nov 2027) with PHP 8.2+ attributes.
2. **Admin Layer**: **EasyAdmin 4** (`easycorp/easyadmin-bundle`) for CRUD dashboards.
3. **Asset Pipeline**: **`pentatrion/vite-bundle`** + **`sass`** for Vite HMR and SCSS compilation.
4. **ORM**: **Doctrine ORM 3.x** using PHP 8.2+ Attributes (`#[ORM\Entity]`, `#[ORM\Table]`, `#[Assert\...]`).

---

## 🛑 2. Scope Boundaries (Do's & Don'ts)

### ✅ Do's
1. **State-First Resumption**: Always inspect `ai-work/rad-development/plan.md` and `entities.json` first. If an incomplete plan exists, resume directly from the first uncompleted task.
2. **Audit Logging**: Write all preflight execution results and timestamps to `ai-work/rad-development/preflight.log`.
3. **Atomic Git Commits**: Commit changes after every completed entity/task (`Implement → Verify → Commit → Check-off`).
4. **Read-Only Live DB Safety**: When inspecting an active database, perform strictly read-only schema reflection. Never execute migrations or DDL without explicit human confirmation.
5. **Eager Joins & Autocomplete**: Replace `findAll()` with joined DQL queries (`LEFT JOIN FETCH` + `Paginator`) to eliminate N+1 queries. Always configure `AssociationField::autocomplete()` in EasyAdmin.

### ❌ Don'ts
1. **No Silent Re-runs**: Do not overwrite already completed entities when resuming from a crash or breakdown.
2. **No Bulk Commits**: Do not bundle the entire application into a single massive commit; maintain a clean, incremental git history per entity.
3. **No Naive `findAll()`**: Never leave unpaginated or non-joined queries in controllers for entities with relations.
4. **No Unverified Syntax**: Verify every generated class via `php -l` and `bin/console lint:twig` before committing.

---

## ⚠️ 3. Critical Architectural Traps & Countermeasures

### ⚠️ Trap 1: The N+1 Query Disaster in Default CRUD
- **The Problem**: Default `make:crud` outputs `findAll()`. Rendering related entities in Twig (e.g. `{{ order.customer.name }}`) triggers 1 query for the list + 50 queries for 50 records.
- **Countermeasure**: Generate custom repository methods with explicit `LEFT JOIN FETCH` (`createQueryBuilder('o')->leftJoin('o.customer', 'c')->addSelect('c')`) and `Doctrine\ORM\Tools\Pagination\Paginator`.

### ⚠️ Trap 2: EasyAdmin Memory Exhaustion on Foreign Keys
- **The Problem**: Default EasyAdmin loads entire related tables into `<select>` dropdowns, crashing PHP `memory_limit`.
- **Countermeasure**: All `AssociationField` instances must use `.autocomplete()`:
  ```php
  yield AssociationField::new('customer')->autocomplete();
  ```

### ⚠️ Trap 3: Schema Type Misalignment
- **The Problem**: Database columns allow loose data unless guarded at the entity level.
- **Countermeasure**: Generate strict PHP 8 types and dual validations:
  - `VARCHAR(255) NOT NULL` ➔ `string` + `#[Assert\NotBlank]` + `#[Assert\Length(max: 255)]`
  - `INT UNSIGNED` ➔ `int` + `#[Assert\PositiveOrZero]`
  - `DATETIME` ➔ `\DateTimeImmutable` + `DateTimeField`

---

## 📜 4. Execution Protocols

### Phase 0: Resumption & Crash-Recovery Check
Before starting any work, check if `ai-work/rad-development/` exists:
1. If `ai-work/rad-development/plan.md` and `entities.json` exist:
   - Read the files.
   - Scan `plan.md` for the first unchecked item (`- [ ]`).
   - Resume execution directly at that task. Do not re-run preflight or re-generate completed entities.
2. If files do not exist:
   - Initialize directory `mkdir -p ai-work/rad-development`.
   - Proceed to Phase 1.

---

### Phase 1: Preflight Verification & Logging
Run system checks and log stdout/stderr with ISO timestamps to `ai-work/rad-development/preflight.log`:

1. **Ecosystem Skills Check**:
   Verify installed skills in `.skill-lock.json` / `skills/`. Install if missing:
   ```bash
   npx skills add dev-toolings/superpowers-symfony@symfony:doctrine-relations
   npx skills add kgslotwinski/skills@easy-admin-bundle
   npx skills add mindrally/skills@scss-best-practices
   npx skills add antfu/skills@vite
   ```
2. **Runtime & Packages Check**:
   - PHP >= 8.2 (extensions: `pdo`, `intl`, `mbstring`).
   - Composer, Node >= 18, npm >= 9.
   - Composer bundles: `symfony/orm-pack`, `maker-bundle`, `easycorp/easyadmin-bundle`, `pentatrion/vite-bundle`, `symfony/validator`, `symfony/form`, `symfony/twig-bundle`.
   - Node packages: `vite`, `sass`.
3. **Log Output**:
   Record all check outcomes to `ai-work/rad-development/preflight.log`. If any dependency is missing, halt and output the exact install command.
4. **Git Commit**:
   ```bash
   git add ai-work/rad-development/preflight.log && git commit -m "chore(rad): complete preflight verification checks"
   ```

---

### Phase 2: Schema Ingestion & Entity Catalog (`entities.json`)
Parse the schema source (SQL DDL file, read-only live DB, or specification) and generate `ai-work/rad-development/entities.json`:

```json
{
  "project": "app_name",
  "generated_at": "2026-09-13T14:00:00Z",
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

### Phase 3: Execution Plan Generation (`plan.md`)
Generate `ai-work/rad-development/plan.md` with sequentially ordered tasks:
- `[x] Preflight checks logged`
- `[x] Schema ingested and entities.json created`
- `[ ] Setup EasyAdmin Dashboard & Base Layout`
- `[ ] Entity: Customer (Model, Repository, EasyAdmin CRUD, Frontend)`
- `[ ] Entity: Order (Model, Repository, EasyAdmin CRUD, Frontend)`
- `[ ] Final validation & schema integrity check`

Commit the state files:
```bash
git add ai-work/rad-development/entities.json ai-work/rad-development/plan.md
git commit -m "docs(rad): initialize entity catalog and execution plan"
```

---

### Phase 4: Incremental Execution Loop (Per Entity)
For each entity in `entities.json` where `status == "pending"`:

1. **Scaffold & Accelerate**:
   - `bin/console make:entity --regenerate App` (or generate entity classes).
   - `bin/console make:admin:crud` for EasyAdmin.
   - `bin/console make:crud <Entity>` for frontend.
2. **Architectural Refactoring**:
   - Add strict typing and `#[Assert\...]` validation attributes.
   - Refactor repository: replace `findAll()` with eager-joined `findWithRelationsPaginated()`.
   - Refactor EasyAdmin CRUD controller: add `yield AssociationField::new(...)->autocomplete()`, filters, and search fields.
   - Refactor frontend controller: wire to paginated repository method; ensure `templates/base.html.twig` has Vite tags.
3. **Empirical Verification**:
   - `php -l src/Entity/<Entity>.php`
   - `php -l src/Controller/Admin/<Entity>CrudController.php`
   - `php -l src/Controller/Frontend/<Entity>Controller.php`
   - `bin/console lint:twig templates/frontend/<entity>/`
4. **State Update & Atomic Git Commit**:
   - Update entity in `entities.json`: `"status": "completed"`.
   - Mark task complete in `plan.md`: `- [x] Entity: <Entity>`.
   - Commit changes:
     ```bash
     git add src/ templates/ ai-work/rad-development/
     git commit -m "feat(rad): generate and optimize <Entity> CRUD (EasyAdmin & Frontend)"
     ```

---

### Phase 5: Final Verification & Audit
1. Run schema and twig validation:
   ```bash
   bin/console doctrine:schema:validate --skip-sync
   bin/console lint:twig templates/
   ```
2. Mark final task complete in `ai-work/rad-development/plan.md`.
3. Commit and present summary report:
   ```bash
   git add ai-work/rad-development/plan.md && git commit -m "chore(rad): finalize application scaffolding"
   ```
