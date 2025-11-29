---
description: Generate a conventional commit message from staged changes
argument-hint: [--ja]
allowed-tools: Bash
---

# Commit Message Generator

Generate a concise commit message following Conventional Commits format.

**Default**: English | **`--ja`**: Japanese

## Instructions

1. Check if there are staged changes (`git diff --staged --name-only`)
   - If none, inform the user and stop
2. Analyze the changes:
   - Review `git diff --staged` for content
   - Check `git log --oneline -10` for project style
3. Generate a message following this format:

```
   <type>[(scope)]: <summary>
```

## Types

- `feat` - New feature
- `fix` - Bug fix
- `docs` - Documentation only
- `style` - Formatting, whitespace
- `refactor` - Code restructuring
- `perf` - Performance improvement
- `test` - Adding/updating tests
- `chore` - Build process, tools

## Rules

**English** (default):

- Max 50 characters
- Lowercase start ("add" not "Add")
- Imperative mood ("add" not "added")
- No period at end

**Japanese** (with `--ja`):

- Max 50 characters
- Use "〜する" or "〜を追加" forms
- No period at end

**Scope** (optional): Add when changes are module-specific (e.g., `auth`, `api`, `db`)

**Multiple changes**: Recommend splitting if unrelated types are mixed (feat + fix)

Match the tone and style of recent commits in `git log`.
