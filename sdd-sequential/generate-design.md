# Generate Design Document

<!-- /generate-design $PRD_PATH --spec $SPEC_PATH [--output PATH] -->

## Purpose

Generate lightweight Design defining HOW to build the system.
Focus on key architectural decisions and technology choices.

## Input Validation

If `$PRD_PATH` or `--spec $SPEC_PATH` is missing:

- Display error and usage example
- **STOP execution**

## Execution Steps

### 1. Read Context

- PRD: Business constraints
- Spec: Technical contracts
- Existing codebase: Current patterns
- `claude.md`: Project conventions

### 2. Generate Design Sections

**Architecture Overview:**

- High-level component diagram (ASCII art is fine)
- 3-5 key components with brief descriptions

**Technology Decisions (ADR format):**

- 2-4 critical choices (database, framework, async processing, etc.)
- Each ADR: Decision, Reason, Alternatives considered
- Keep each ADR to 5-10 lines

**Critical Data Flows:**

- 2-3 main flows (happy path + key error cases)
- Numbered step lists, no need for detailed sequence diagrams

**Implementation Notes (optional):**

- Layering approach (if not obvious)
- Key patterns to use
- Implementation phases (if complex)

**Non-Functional Approach:**

- How to meet Spec's performance/reliability requirements
- Brief notes on error handling, retries, monitoring

### 3. Validate Against Spec

- All API endpoints from Spec are covered
- Database schema from Spec is addressed
- Performance requirements from Spec have a solution

### 4. Output

Write Design to specified path with:

- Source PRD and Spec references
- Review checklist
- Next step: `/implement`

## Notes

- Keep Design concise (1-2 pages)
- Focus on decisions that are hard to change later
- Implementation details can emerge during coding
- Design is a guide, not a prescription
