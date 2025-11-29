# Verify Alignment

<!-- /verify $PRD_PATH --spec $SPEC_PATH --design $DESIGN_PATH --impl $IMPL_DIR -->

## Purpose

Verify alignment between PRD, Spec, Design, and Implementation.
Catch drift and inconsistencies across artifacts.

## Input Validation

All arguments required. If any missing, display error and usage.

## Execution Steps

### 1. PRD ↔ Spec Alignment

- All user stories have corresponding features in Spec
- All success criteria are verifiable through Spec

### 2. Spec ↔ Design Alignment

- All Spec endpoints/schemas covered in Design
- All Spec error codes have handling strategy in Design

### 3. Design ↔ Implementation Alignment

- Implementation follows Design architecture
- All Design modules exist in Implementation

### 4. Spec ↔ Implementation Direct Check

- All Spec API contracts are implemented
- Error response formats match Spec exactly

### 5. Test Coverage Check

- All Spec validation rules have tests
- All critical flows have tests

## Output

Report:

- ✅ Aligned sections
- ⚠️ Warnings (minor issues)
- ❌ Failures (must fix)
- Recommended actions

## Notes

- Run before deployment
- Can be integrated into CI/CD
- Helps maintain consistency as project evolves
