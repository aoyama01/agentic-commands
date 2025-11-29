# Dev Cycle

<!-- /dev $ARGUMENTS -->

## Purpose

Start the full design-implementation cycle based on the provided PRD (file path = $ARGUMENTS).
This command performs the orchestration internally:

- Generates a design (including test design) based on PRD and any existing implementation (for context only)
- Generates an implementation (including tests) based on PRD and any existing design (for context only)
- Reconciles design and implementation differences logically, guided by the PRD
- Updates claude.md rules to mitigate causes based on the differences
- Iterates until design and implementation are fully synchronized and all tests pass

### Why

Ensuring that the user only needs to review designs (never implementations) requires
guaranteeing that design and implementation are fully synchronized.
By embedding orchestration into this command, there is no dependency on a separate orchestrator agent.

---

## Input Validation

⚠️ IMPORTANT: Validate PRD file path argument ⚠️

If `$ARGUMENTS` is empty, undefined, or not a valid file path:

- Display error: `❌ エラー: PRDのファイルパスが必要です。引数を指定してください。 😊`
- Display usage example: `例: /dev path/to/prd-file.md`
- ⚠️STOP execution immediately - do not proceed with any subsequent steps⚠️

Only proceed with the following steps if a valid file path is provided.

---

## Execution Steps

### 1. Context Gathering

- Read the PRD (`$ARGUMENTS`) thoroughly to understand requirements.
- Extract any file paths to related design or implementation artifacts mentioned in the PRD.
- Search the repository for likely related files (naming, references, topical structure).
- Build a full context set:
  - PRD file path
  - Related design files (if any)
  - Related implementation files (if any)

### 2. Parallel Generation

- **Design Generation Task**:

  - Input: PRD + any existing implementation (context only)
  - Explicit Instruction:
    > "Use PRD as the primary source of truth.
    > Treat any existing implementation only as reference context.
    > Produce a clean design (including test design) that deterministically defines the implementation."

- **Implementation Generation Task**:

  - Input: PRD + any existing design (context only)
  - Explicit Instruction:
    > "Use PRD as the primary source of truth.
    > Treat any existing design only as reference context.
    > Generate implementation and tests directly from PRD, ensuring the new design being generated in parallel."

### 3. Reconciliation Phase (using reconciliation-agent)

- Invoke the **reconciliation-agent** with:
  - The original PRD
  - The newly generated/updated design documentation
  - The newly generated/updated implementation
- Analyze the reconciliation report for misalignments:
  - Compare design and implementation logically (API/function-level differences)
  - Generate implementation from design into a temporary directory and compare with the actual implementation
- If differences are found:
  - Use PRD as the ultimate truth to determine which artifact is incorrect
  - Adjust design or implementation accordingly
  - Update 'claude.md' if ambiguity or missing rules caused the difference

### 4. Iteration Phase

- **Repeat steps 1-3** until:
  - The reconciliation-agent confirms full alignment between design and implementation
  - All tests pass successfully
- This iterative loop ensures all artifacts converge to a consistent, PRD-aligned state.

### 5. Output Summary

- After the loop finishes, show:
  - Final design
  - Final implementation
  - Test results: `/tests/results`
  - Updated `claude.md` (if rules were changed)

---

## Notes

- The user only needs to provide the PRD file path; related files are automatically resolved.
- The cycle continues until **no differences remain** and **all tests pass**, ensuring the user only needs to review the design.
