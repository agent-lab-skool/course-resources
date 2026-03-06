---
name: review
description: Review staged code changes for security issues, type errors, performance problems, and style violations
command: /review
---

## What to Check

Security:
1. Look for exposed API keys, tokens, or secrets in the diff
2. Check for SQL injection vulnerabilities (raw string interpolation in queries)
3. Look for XSS risks (dangerouslySetInnerHTML, unescaped user input)
4. Verify that authentication checks exist on new API routes
5. Make sure .env files aren't being committed

Types:
1. Check for `as any` casts that could hide bugs
2. Look for missing null checks on optional values
3. Verify function return types match their signatures
4. Check for implicit any types in function parameters

Performance:
1. Flag unnecessary re-renders (missing useMemo, useCallback where it matters)
2. Check for N+1 query patterns in data fetching
3. Look for large objects being created inside render functions
4. Check for missing database indexes on frequently queried columns

## First Run Adaptation

1. Check for existing linting config (.eslintrc, biome.json) to avoid duplicating those checks
2. Read CLAUDE.md for project-specific code conventions
3. Look at recent PRs or git log for the team's review style

## Output Format

List each finding with the file path and line number.
Categorize as CRITICAL (must fix before merging), WARNING (should fix), or NOTE (consider fixing).
Don't auto-fix anything. Just report findings so the developer can decide.

## What NOT to Flag

Don't nitpick formatting. That's what Prettier is for.
Don't flag TODO comments. Those are intentional.
Don't suggest adding comments to obvious code.
Don't flag minor style preferences that aren't in the project's lint config.
