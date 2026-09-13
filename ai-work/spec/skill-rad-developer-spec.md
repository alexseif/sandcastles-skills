# 📋 Feature Specification: RAD Developer Skill (`skills/rad-developer/SKILL.md`)

---

## 🎯 1. Objective Alignment
- **Target Objective**: Create a deterministic Rapid Application Development generator (`rad-developer`) based on Option B (Blueprint-Driven Generation Engine). It ingests a database schema (SQL file, live DB with read-only safety, or schema spec) and builds a high-performance Symfony 6.4 LTS application featuring EasyAdmin 4 CRUD, Twig + Vite + SCSS frontend, and Doctrine ORM with N+1 query prevention.
- **Reference**: Grounded in [`OBJECTIVE.md`](../../OBJECTIVE.md) and [`SPEC.md`](../../SPEC.md).

---

## 📝 2. Description of Specifications

### 1. Preflight Check Protocol
Before generating any code, verify and report the existence of:
- **System Binaries**: PHP >= 8.2 (extensions: `pdo`, `pdo_mysql`/`pgsql`, `intl`, `mbstring`), Composer, Node >= 18, npm.
- **Composer Bundles**: `symfony/orm-pack`, `symfony/maker-bundle`, `easycorp/easyadmin-bundle`, `pentatrion/vite-bundle`, `symfony/validator`, `symfony/form`, `symfony/twig-bundle`.
- **Node Packages**: `vite`, `sass`.
- **Halt on Missing Dependencies**: If any dependency is absent, halt and output the exact `composer require` / `npm install` command.

### 2. Multi-Source Schema Ingestion & Safety
- **Live Database Connection**: Strictly read-only reflection via DBAL SchemaManager. Prohibited from executing DDL/migrations without explicit user confirmation.
- **SQL DDL File**: Parses tables, columns, indexes, and foreign keys directly from `.sql` files.

### 3. Blueprint-Driven Code Generation (Option B)
- **Doctrine Persistence Layer**:
  - PHP 8.2+ Attributes (`#[ORM\Entity]`, `#[ORM\Column]`, `#[ORM\ManyToOne]`, etc.).
  - Strict PHP typing and Symfony Validator constraints (`#[Assert\NotBlank]`, `#[Assert\Length]`).
  - Custom Repositories with eager-joining DQL (`LEFT JOIN e.relation addSelect('r')`) to eliminate N+1 queries.
  - Doctrine pagination support (`Doctrine\ORM\Tools\Pagination\Paginator`).
- **EasyAdmin 4 Backend Layer**:
  - `DashboardController` configuring navigation, icons, and entity links.
  - `AbstractCrudController` per entity with automated field deduction.
  - Mandatory `AssociationField::autocomplete()` on all relations to eliminate memory exhaustion.
  - Search fields and filters for primary attributes.
- **Frontend Presentation Layer**:
  - Symfony Controllers with paginated index and show actions.
  - Twig templates with `{{ vite_entry_link_tags('app') }}` and `{{ vite_entry_script_tags('app') }}`.
  - BEM-structured SCSS architecture compiled through Vite (`pentatrion/vite-bundle`).

### 4. Ecosystem Skill Integration
Integrates established patterns from:
- `dev-toolings/superpowers-symfony`: `@symfony:doctrine-relations`, `@symfony:doctrine-migrations`.
- `kgslotwinski/skills@easy-admin-bundle`: EasyAdmin 4 CRUD design.
- `mindrally/skills@scss-best-practices`: Clean BEM SCSS architecture.
- `antfu/skills@vite`: Optimized Vite asset bundling.

---

## 🛑 3. Scope Boundaries (Do's & Don'ts)

### ✅ Do's
1. **Preflight Enforcement**: Verify all system and bundle prerequisites before generating code.
2. **Eager Join Repositories**: Always generate repository query methods with eager joins for listings.
3. **Autocomplete on Relations**: Always generate `AssociationField::autocomplete()` in EasyAdmin CRUD controllers.
4. **Read-Only Live DB**: Keep live DB introspection strictly read-only.

### ❌ Don'ts
1. **No Naive `findAll()`**: Never generate unpaginated or non-joined `findAll()` queries for entities with relationships.
2. **No Unconfirmed Migrations**: Never execute `doctrine:migrations:migrate` or destructive DDL on existing databases without explicit user sign-off.
3. **No Code Without Verification**: Run `php -l` (syntax check) or `bin/console lint:twig` on generated artifacts.
