---
name: rad-developer
description: >-
  Rapid Application Development (RAD) generator for Symfony 6.4 LTS.
  Consumes a database schema (SQL file, read-only live DB, or spec), verifies agent skills and runtime prerequisites,
  scaffolds via Symfony Maker CLI, and deterministically upgrades the code to enterprise standards:
  EasyAdmin 4 with autocomplete, Twig + Vite + SCSS frontend, and Doctrine ORM with eager joins (N+1 query prevention).
  Aliases: rad build, rad dev, scaffold symfony, generate crud, easyadmin scaffold.
---

# ⚡ RAD Developer Skill (`rad-developer`)

The `rad-developer` skill rapidly constructs production-grade web applications on **Symfony 6.4 LTS** from a database schema. It utilizes Symfony Maker CLI commands (`make:entity`, `make:crud`, `make:admin:crud`) as scaffolding accelerators, then immediately refactors the generated code to eliminate naive boilerplate shortcomings, enforcing **EasyAdmin 4** management with autocomplete relations, a **Twig + Vite + SCSS** frontend, and an optimized **Doctrine ORM** persistence layer engineered against N+1 query degradation and memory exhaustion.

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

1. **Framework Core**: **Symfony 6.4 LTS** (supported through Nov 2027) with PHP 8.2+ attribute support.
2. **Admin Layer**: **EasyAdmin 4** (`easycorp/easyadmin-bundle`) for CRUD dashboards.
3. **Asset Pipeline**: **`pentatrion/vite-bundle`** + **`sass`** for Vite HMR and SCSS compilation.
4. **ORM**: **Doctrine ORM 3.x** using PHP 8.2+ Attributes (`#[ORM\Entity]`, `#[ORM\Table]`, `#[Assert\...]`).

---

## 🛑 2. Scope Boundaries (Do's & Don'ts)

### ✅ Do's
1. **Mandatory Preflight Checks**: Verify system binaries, Composer bundles, Node packages, and required agent skills before running any generation tasks.
2. **Read-Only Live DB Safety Lock**: When connecting to an active database, perform strictly read-only schema reflection. Never alter schemas or run migrations without explicit user approval.
3. **Scaffold Acceleration + Refinement**: Use `bin/console make:*` to quickly generate base files, then refactor them to enforce architectural standards.
4. **Eager-Loaded Repositories**: Replace default `findAll()` calls with custom repository query methods using `LEFT JOIN` and `addSelect` for entity relationships to eliminate N+1 queries.
5. **Autocomplete on Relations**: Always configure `AssociationField::new(...)->autocomplete()` in EasyAdmin CRUD controllers to prevent PHP memory exhaustion.
6. **Strict Typing & Validations**: Enforce PHP 8.2+ strict types, ORM attributes, and Symfony Validator constraints (`#[Assert\...]`).

### ❌ Don'ts
1. **No Naive `findAll()`**: Never leave unpaginated or non-joined `findAll()` queries in controllers for entities that have relations.
2. **No Unconfirmed Migrations**: Never execute `doctrine:migrations:migrate` or destructive DDL on existing databases without explicit human confirmation.
3. **No Unverified Syntax**: Run `php -l` (syntax check) and `bin/console lint:twig` on generated artifacts before declaring completion.

---

## ⚠️ 3. Critical Architectural Traps & Countermeasures

### ⚠️ Trap 1: The N+1 Query Disaster in Default CRUD
- **The Problem**: Default `make:crud` outputs `findAll()` in controllers. When rendering related entities in Twig (e.g. `{{ order.customer.name }}`), Doctrine executes 1 query for the list + 50 queries for 50 customers.
- **Countermeasure**: The generator must **never** use `findAll()` on entities with relations. It must generate custom repository methods using explicit `LEFT JOIN FETCH` (`createQueryBuilder('o')->leftJoin('o.customer', 'c')->addSelect('c')`) paired with `Doctrine\ORM\Tools\Pagination\Paginator`.

### ⚠️ Trap 2: EasyAdmin Memory Exhaustion on Foreign Keys
- **The Problem**: If table `orders` has a `user_id` relation, default EasyAdmin loads all 50,000 users into a `<select>` dropdown, exhausting PHP `memory_limit` and crashing the admin panel.
- **Countermeasure**: All `AssociationField` instances in EasyAdmin must be generated with `.autocomplete()`:
  ```php
  yield AssociationField::new('customer')->autocomplete();
  ```

### ⚠️ Trap 3: Schema Type Misalignment
- **The Problem**: Database columns allow loose data unless guarded at the entity level.
- **Countermeasure**: Field introspection must generate strict PHP 8 types and dual validations:
  - `VARCHAR(255) NOT NULL` ➔ `string` + `#[Assert\NotBlank]` + `#[Assert\Length(max: 255)]`
  - `INT UNSIGNED` ➔ `int` + `#[Assert\PositiveOrZero]`
  - `DATETIME` ➔ `\DateTimeImmutable` + `DateTimeField`

---

## 📜 4. Execution Protocols

### Step 1: Preflight Verification Protocol

#### 1.1 Ecosystem Agent Skills Check
Check `.skill-lock.json` and `skills/` for the following required skills. If any are missing, install them via `npx skills add`:
```bash
# Verify and install required domain skills
npx skills add dev-toolings/superpowers-symfony@symfony:doctrine-relations
npx skills add kgslotwinski/skills@easy-admin-bundle
npx skills add mindrally/skills@scss-best-practices
npx skills add antfu/skills@vite
```

#### 1.2 System & Package Preflight
Inspect the project environment:
```bash
# System Binaries
php -v                  # Must be >= 8.2 with pdo, intl, mbstring extensions
composer -V             # Must exist
node -v && npm -v       # Node >= 18, npm >= 9

# Required Composer Bundles (composer.json)
symfony/orm-pack
symfony/maker-bundle
easycorp/easyadmin-bundle
pentatrion/vite-bundle
symfony/validator
symfony/form
symfony/twig-bundle

# Required Node Packages (package.json)
vite
sass
```

If any application dependency is missing, halt execution and output the required installation command:
```bash
composer require symfony/orm-pack easycorp/easyadmin-bundle pentatrion/vite-bundle symfony/validator symfony/form symfony/twig-bundle
composer require --dev symfony/maker-bundle
npm install --save-dev vite sass
```

---

### Step 2: Schema Ingestion Protocol
The generator consumes schemas from three supported sources:
- **Source A (SQL DDL File)**: Parses `schema.sql` (or output from `rad-interviewer`), extracting tables, column types, foreign keys, and indexes.
- **Source B (Live Database)**: Reads live database metadata using Doctrine DBAL's `SchemaManager` in **strict read-only mode**.
- **Source C (Structured Schema Document)**: Consumes entity specification tables from `ai-work/schema/`.

---

### Step 3: Hybrid Scaffolding & Refinement Protocol

#### 3.1 Doctrine Entities & Repositories
1. Run `bin/console make:entity --regenerate App` (or generate entity classes).
2. Refactor entities with strict typing and validations (`#[Assert\NotBlank]`, `#[Assert\Length]`).
3. Refactor repositories: Add paginated eager-join queries:
   ```php
   public function findWithRelationsPaginated(int $page = 1, int $limit = 20): Paginator
   {
       $qb = $this->createQueryBuilder('e')
           ->leftJoin('e.relation', 'r')
           ->addSelect('r')
           ->orderBy('e.id', 'DESC')
           ->setFirstResult(($page - 1) * $limit)
           ->setMaxResults($limit);

       return new Paginator($qb);
   }
   ```

#### 3.2 EasyAdmin 4 Backend Administration
1. If not present, generate dashboard: `bin/console make:admin:dashboard`.
2. Generate CRUD controllers: `bin/console make:admin:crud`.
3. Refactor each CRUD controller:
   - Configure fields with explicit types (`DateTimeField`, `MoneyField`, `ChoiceField`).
   - Enforce autocomplete on all foreign key associations:
     ```php
     yield AssociationField::new('customer')->autocomplete();
     ```
   - Add search fields and entity filters (`EntityFilter`, `DateTimeFilter`).

#### 3.3 Frontend Presentation Layer (Twig + Vite + SCSS)
1. Generate CRUD frontend: `bin/console make:crud <Entity>`.
2. Refactor frontend controllers to use the repository's `findWithRelationsPaginated()` method instead of `findAll()`.
3. Update `templates/base.html.twig` to embed Vite tags:
   ```twig
   {{ vite_entry_link_tags('app') }}
   {{ vite_entry_script_tags('app') }}
   ```
4. Structure SCSS in `assets/styles/` using BEM modular patterns (`_variables.scss`, `_layout.scss`, `_components.scss`), compiled via `pentatrion/vite-bundle`.

---

### Step 4: Verification & Linting
Run syntax and template checks before declaring complete:
```bash
php -l src/Entity/*.php
php -l src/Controller/*.php
bin/console lint:twig templates/
bin/console doctrine:schema:validate --skip-sync
```
