---
description: Generate concise commit messages from staged changes (English/Japanese)
allowed-tools: Bash(git diff:*), Bash(git status:*), Bash(git log:*)
---

# Commit Message Generator

## Purpose

Generate consistent, high-quality commit messages following Conventional Commits format.

This ensures:

- Consistency across the project's commit history
- Clear understanding of changes at a glance
- Compatibility with automated changelog generation
- Time saved on writing commit messages

## Input Validation

Check for the `--ja` flag in `$ARGUMENTS`:

- If `--ja` is present: Generate commit message in Japanese
- If `--ja` is absent or `$ARGUMENTS` is empty: Generate commit message in English (default)

## Pre-execution Check

**IMPORTANT: Check for staged changes first**

Run `git diff --staged --name-only` to verify there are staged changes.

If no staged changes exist:

- Display: `❌ No staged changes found. Please stage your changes with 'git add' first.`
- **STOP execution immediately - do not proceed with any subsequent steps**

Only proceed with the following steps if staged changes exist.

## Execution Steps

1. **Analyze staged changes**
   - Run `git diff --staged` to see the actual changes
   - Run `git diff --staged --name-only` to get the list of modified files
2. **Review commit history**
   - Run `git log --oneline -10` to understand the project's commit message style
   - Identify patterns in type usage, scope usage, and tone
3. **Determine commit type and scope**
   - Identify the primary change type (feat, fix, refactor, etc.)
   - If changes affect a specific module/component, determine the scope
   - If multiple unrelated changes exist, recommend splitting the commit
4. **Generate commit message**
   - Follow the format: `<type>[(scope)]: <summary>`
   - Match the project's existing commit style
   - Ensure the message is clear, concise, and follows the rules below

## Output Format

```
<type>[(scope)]: <summary>
```

### Types

- `feat`: A new feature
- `fix`: A bug fix
- `docs`: Documentation only changes
- `style`: Changes that don't affect code meaning (whitespace, formatting, etc.)
- `refactor`: Code change that neither fixes a bug nor adds a feature
- `perf`: Performance improvements
- `test`: Adding or modifying tests
- `chore`: Changes to build process or auxiliary tools

### Scope (optional)

The area of change (e.g., auth, api, db, ui)

- Use when changes are limited to a specific module or component
- Omit for project-wide changes

## Message Quality Checklist

Ensure the generated message meets these requirements:

- [ ] Within 50 characters
- [ ] No period at the end
- [ ] Uses imperative mood (English) or appropriate verb form (Japanese)
- [ ] Starts with lowercase (English)
- [ ] Clearly describes the change
- [ ] Matches the project's commit history style

## Rules

### English (default)

- Keep within 50 characters
- No period at the end
- Start with lowercase ("add" not "Add")
- Use imperative mood ("add" not "added", "fix" not "fixed")
- Match recent commit history tone and style

### Japanese (when `--ja` is specified)

- Keep within 50 characters
- No period at the end
- Use forms like "〜する" or "〜を追加"
- Match recent commit history tone and style

## Edge Cases

- **Multiple change types**: Focus on the primary change and suggest splitting if feat and fix are mixed
- **Large changes**: Recommend splitting into smaller, focused commits
- **No clear type**: Ask for clarification on the intent of the changes
