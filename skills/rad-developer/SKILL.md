---
name: rad-developer
description: >-
  Rapid Application Development (RAD) generator for Symfony 6.4 LTS.
  Consumes a database schema (SQL file, read-only live DB, or spec), executes strict preflight verification,
  and deterministically scaffolds complete EasyAdmin 4 dashboards and Twig + Vite + SCSS frontend CRUD with Doctrine ORM (eager joins, N+1 query prevention).
  Aliases: rad build, rad dev, scaffold symfony, generate crud, easyadmin scaffold.
---

# ⚡ RAD Developer Skill (`rad-developer`)

The `rad-developer` skill deterministically generates a complete, production-grade application on **Symfony 6.4 LTS** from a relational database schema. It scaffolds an **EasyAdmin 4** management panel and a **Twig + Vite + SCSS** frontend, backed by an optimized **Doctrine ORM** persistence layer engineered to prevent N+1 query degradation and memory exhaustion.

---

## 🛑 Scope Boundaries (Do's & Don'ts)

### ✅ Do's
1. **Mandatory Preflight Checks**: Verify all system binaries, Composer bundles, and Node packages before generating any code. Halt with exact installation commands if dependencies are missing.
2. **Read-Only Live DB Safety Lock**: When connecting to an active database, perform strictly read-only schema reflection. Never alter schemas or run migrations without explicit user approval.
3. **Eager-Loaded Repositories**: Always generate custom repository query methods with `LEFT JOIN` and `addSelect` for entity relationships to eliminate N+1 queries.
4. **Autocomplete on Relations**: Always configure `AssociationField::new(...)->autocomplete()` in EasyAdmin CRUD controllers to prevent PHP memory exhaustion.
5. **Strict Typing & Validations**: Generate entities with PHP 8.2+ strict types, ORM attributes, and Symfony Validator constraints (`#[Assert\...]`).

### ❌ Don'ts
1. **No Naive `findAll()`**: Never generate unpaginated or non-joined `findAll()` queries for entities that have relations.
2. **No Unconfirmed Migrations**: Never execute `doctrine:migrations:migrate` or destructive DDL on existing databases without explicit human confirmation.
3. **No Unverified Syntax**: Verify generated PHP and Twig syntax via `php -l` or `bin/console lint:twig`.

---

## 📜 Execution Protocols

### 1. Preflight Verification Protocol
Before executing any generation step, inspect the project environment:

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

If any dependency is missing, halt execution immediately and output the exact command to install them:
```bash
composer require symfony/orm-pack easycorp/easyadmin-bundle pentatrion/vite-bundle symfony/validator symfony/form symfony/twig-bundle
composer require --dev symfony/maker-bundle
npm install --save-dev vite sass
```

---

### 2. Schema Ingestion Protocol
The generator consumes schemas from three supported sources:
- **Source A (SQL DDL File)**: Parses `schema.sql` (or output from `rad-interviewer`), extracting tables, column types, foreign keys, and indexes.
- **Source B (Live Database)**: Reads live database metadata using Doctrine DBAL's `SchemaManager` in **strict read-only mode**.
- **Source C (Structured Schema Document)**: Consumes entity specification tables from `ai-work/schema/`.

---

### 3. Blueprint-Driven Code Generation (Option B)

#### 3.1 Doctrine ORM Persistence Layer
- **Entities (`src/Entity/`)**:
  - PHP 8.2+ attributes (`#[ORM\Entity(repositoryClass: ...)]`, `#[ORM\Table]`, `#[ORM\Column]`).
  - Strict types on all properties, getters, and setters.
  - Symfony Validator attributes (`#[Assert\NotBlank]`, `#[Assert\Length]`, `#[Assert\Positive]`, `#[Assert\Email]`).
- **Repositories (`src/Repository/`)**:
  - Custom finders with eager joins:
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

#### 3.2 EasyAdmin 4 Backend Administration Layer
- **Dashboard (`src/Controller/Admin/DashboardController.php`)**:
  - Sets application title, locale, and main navigation links (`yield MenuItem::linkToCrud(...)`).
- **CRUD Controllers (`src/Controller/Admin/*CrudController.php`)**:
  - Dedicated controller per entity.
  - Mandatory autocomplete on all relations:
    ```php
    yield AssociationField::new('customer')->autocomplete();
    ```
  - Formatted fields (`DateTimeField`, `MoneyField`, `ChoiceField`, `TextareaField`).
  - Standard filters (`EntityFilter`, `DateTimeFilter`) and search fields.

#### 3.3 Frontend Presentation Layer (Twig + Vite + SCSS)
- **Controllers (`src/Controller/Frontend/*Controller.php`)**:
  - Public listing action with pagination and eager joins.
  - Detail show action with related entity rendering.
- **Twig Templates (`templates/frontend/`)**:
  - Root layout `templates/base.html.twig` utilizing:
    ```twig
    {{ vite_entry_link_tags('app') }}
    {{ vite_entry_script_tags('app') }}
    ```
  - Responsive index grid and detail templates.
- **SCSS Architecture (`assets/styles/`)**:
  - BEM-structured modular SCSS (`_variables.scss`, `_layout.scss`, `_components.scss`).
  - Compiled and hot-reloaded through `vite.config.js` and `pentatrion/vite-bundle`.

---

### 4. Ecosystem Skill Integration
During code generation, align with best practices from:
- `dev-toolings/superpowers-symfony`: Enforce clean relation mappings (`@symfony:doctrine-relations`) and migration safety (`@symfony:doctrine-migrations`).
- `kgslotwinski/skills@easy-admin-bundle`: EasyAdmin 4 controller configuration patterns.
- `mindrally/skills@scss-best-practices`: BEM modular SCSS structure.
- `antfu/skills@vite`: Optimized Vite asset bundle configurations.
