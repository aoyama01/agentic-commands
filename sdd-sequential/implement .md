# Generate Implementation

<!-- /implement $PRD_PATH --spec $SPEC_PATH --design $DESIGN_PATH [--output-dir PATH] -->

## Purpose

Generate implementation code and tests based on PRD, Spec, and Design.
Code must conform to Spec contracts and follow Design architecture.

## Input Validation

If `$PRD_PATH`, `--spec $SPEC_PATH`, or `--design $DESIGN_PATH` is missing:

- Display error and usage example
- **STOP execution**

## Execution Steps

### 1. Load Context

- PRD: Business context and acceptance criteria
- Spec: Exact contracts (API, schemas, errors)
- Design: Architecture and technology choices
- `claude.md`: Coding standards

### 2. Generate Code Following Design Phases

For each phase in Design's implementation plan:

- Generate production code
- Generate corresponding tests (unit/integration)
- Follow Design's module structure and patterns

**Code Generation Principles:**

- Implement ALL Spec contracts exactly
- Follow Design's architecture (layers, patterns)
- Use Design's chosen technologies
- Match project coding style from `claude.md`

### 3. Generate Tests

**Unit Tests:**

- All domain logic and validation rules from Spec
- Mock external dependencies

**Integration Tests:**

- Database operations
- API endpoints
- Test against Spec contracts

**Test Coverage:**

- Aim for Design's coverage target
- Ensure all Spec validation rules are tested

### 4. Generate Supporting Files

- Database migrations (from Spec schema)
- Configuration files
- README with quickstart instructions

### 5. Verify Implementation

Run automatic checks:

- Code compiles/runs
- All tests pass
- Spec contracts are implemented
- Follows project standards

### 6. Output Summary

Report:

- Generated files list
- Test results
- Coverage metrics
- Next steps for manual review

## Notes

- Implementation MUST match Spec exactly
- Follow Design's architecture strictly
- Tests are generated alongside production code
- If Spec/Design conflicts found, stop and ask for clarification
