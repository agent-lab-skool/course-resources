---
name: migrate
description: Create and run database migrations with schema validation and rollback planning
command: /migrate
---

## First Run Adaptation

Before creating any migration:
1. Check package.json for the ORM (prisma, drizzle, knex, typeorm, sequelize)
2. Find the database config and connection details
3. Look at existing migrations to learn naming conventions and patterns
4. Check the current schema state
5. Identify the database type (PostgreSQL, MySQL, SQLite)

## Migration Process

1. Read the current schema to understand existing tables and relationships
2. Plan the migration based on what's being requested
3. Generate the migration file using the project's ORM tooling:
   - Prisma: update schema.prisma, then run `npx prisma migrate dev --name <name>`
   - Drizzle: create migration in drizzle/ directory, run `npx drizzle-kit push`
   - Knex: run `npx knex migrate:make <name>`, then write up/down functions
4. Verify the migration by checking the generated SQL
5. Run the migration in development
6. Verify the schema matches expectations

## Rules

Always create both up and down migrations (or the equivalent rollback).
Never drop columns or tables without explicit confirmation from the developer.
Always add indexes for foreign keys and commonly queried columns.
Use snake_case for column names unless the project has a different convention.
Add NOT NULL constraints where appropriate with sensible defaults.
Never store passwords in plain text. Use hashing.

## Common Patterns

Adding a new table: include id, created_at, updated_at columns by default.
Adding a foreign key: add an index and consider ON DELETE behavior.
Renaming a column: create new column, copy data, drop old column (safer than rename).
Adding an enum: check if the database supports native enums or use a string with validation.

## Post-migration

1. Run the test suite to verify nothing broke
2. Check that seed data still works
3. Report what changed and any manual steps needed
