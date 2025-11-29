# Verify Alignment

<!-- /verify $SPEC_PATH --design $DESIGN_PATH --impl $IMPL_DIR [--prd $PRD_PATH] -->

## Purpose

Verify alignment between Spec, Design, and Implementation.
Optionally verify PRD coverage if provided.

## Input Validation

If `$SPEC_PATH`, `--design $DESIGN_PATH`, or `--impl $IMPL_DIR` is missing:

- Display error: `❌ エラー: Spec、Design、Implのパスが必要です。`
- Display usage: `例: /verify docs/spec/feature-spec.md --design docs/design/feature-design.md --impl ./internal/`
- **STOP execution**

## Execution Steps

### 1. PRD ↔ Spec Alignment (if `--prd` specified)

- All user stories have corresponding features in Spec
- All success criteria are verifiable through Spec
- Skip if PRD not provided

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
