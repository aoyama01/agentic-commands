# Generate Specification

<!-- /generate-spec $PRD_PATH_OR_SUMMARY [--output PATH] -->

## Purpose

Generate machine-readable Specification from PRD or summary description.
Spec defines WHAT the system should do (API contracts, data models, validation rules).

## Input Validation

If `$PRD_PATH_OR_SUMMARY` is empty:

- Display error: `❌ エラー: PRDのファイルパスまたは概要説明が必要です。`
- Display usage:
  - `例: /generate-spec docs/prd/feature.md --output docs/spec/feature-spec.md`
  - `例: /generate-spec "ユーザーが予約履歴をCSVでエクスポートできる機能" --output docs/spec/export-spec.md`
- **STOP execution**

## Input Mode Detection

**If argument is a valid file path:**

- Read PRD file and proceed to Step 1

**If argument is NOT a file path (summary mode):**

- Treat argument as feature summary
- Before proceeding, ask clarifying questions:
  - Who are the target users?
  - What are the key success criteria?
  - Any constraints (performance, security, etc.)?
- Proceed to Step 2 after gathering sufficient context

## Execution Steps

### 1. Analyze PRD

- Extract user stories → API endpoints or commands
- Extract data entities → Database schema
- Extract success criteria → Validation rules
- Extract non-functional requirements → Constraints

### 2. Generate Spec Sections

**API Specification:**

- Endpoints/Commands with request/response formats
- Use OpenAPI for REST, Protobuf for gRPC, or plain markdown for CLI

**Data Model:**

- Database tables/collections with columns and constraints
- Include indexes for performance requirements

**Validation Rules:**

- Input validation (types, ranges, formats)
- Business rules (uniqueness, state transitions)

**Error Codes:**

- All possible error scenarios with codes and descriptions
- HTTP status codes or CLI exit codes

**Performance & Constraints:**

- Response time requirements
- Throughput limits
- Security requirements (auth, input sanitization)

### 3. Validate Against Source

- All user stories / requirements covered
- All success criteria can be verified
- All constraints are specific and measurable

### 4. Output

Write Spec to specified path with:

- Source reference: `PRD: <file path>` or `Summary: "<inline summary>"`
- Generated timestamp
- Review checklist
- Next step: `/generate-design`

## Notes

- Spec is the "contract" - Design and Implementation must conform to it
- Keep Spec focused on WHAT, not HOW
- Make it specific enough that two implementations would behave identically
