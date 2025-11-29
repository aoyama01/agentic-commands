# Review PRD

<!-- /review-prd $ARGUMENTS -->

## Purpose

Validate PRD completeness and ask clarifying questions before moving to Spec generation.
Catch ambiguities early to prevent issues in downstream phases.

## Input Validation

If `$ARGUMENTS` is empty or not a valid file path:

- Display error: `❌ エラー: PRDのファイルパスが必要です。`
- Display usage: `例: /review-prd docs/prd/feature.md`
- **STOP execution**

## Execution Steps

### 1. Read PRD and Related Context

- Read the PRD file
- Search for related design/implementation files mentioned in PRD
- Gather context from existing codebase

### 2. Check Completeness

Verify PRD contains:

- [ ] Background & Purpose (Why?)
- [ ] User Stories (Who wants what?)
- [ ] Success Criteria (How to measure?)
- [ ] Scope (In/Out of scope)
- [ ] Non-functional requirements (Performance, Security, Scalability)
- [ ] Related file paths (for Spec/Design/Implementation outputs)
- [ ] Dependencies (on other systems/features)

### 3. Generate Targeted Questions

For any missing or ambiguous sections, ask specific questions:

- Business: "What's the priority? Expected user volume?"
- Technical: "Performance requirement? Consistency model?"
- Scope: "How to handle [error case]? What about [edge case]?"
- Dependencies: "Does this depend on [system X]? Fallback behavior?"

### 4. Output Results

Present findings as:

- ✅ Complete sections
- ⚠️ Missing or ambiguous sections
- ❓ Questions to clarify

## Notes

- PRD must be solid before Spec generation - ambiguities multiply downstream
- Ask questions with specific choices to help user decide
- Re-run this command after updating PRD until all items are ✅
