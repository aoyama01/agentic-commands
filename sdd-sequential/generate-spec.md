# Generate Specification

<!-- /generate-spec $ARGUMENTS [--output PATH] -->

## Purpose

Generate machine-readable Specification from reviewed PRD.
Spec defines WHAT the system should do (API contracts, data models, validation rules).

## Input Validation

If `$ARGUMENTS` is empty or not a valid file path:

- Display error: `❌ エラー: PRDのファイルパスが必要です。`
- Display usage: `例: /generate-spec docs/prd/feature.md --output docs/spec/feature-spec.md`
- **STOP execution**

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

### 3. Validate Against PRD

- All user stories covered
- All success criteria can be verified
- All constraints are specific and measurable

### 4. Output

Write Spec to specified path with:

- Source PRD reference
- Generated timestamp
- Review checklist
- Next step: `/generate-design`

## Notes

- Spec is the "contract" - Design and Implementation must conform to it
- Keep Spec focused on WHAT, not HOW
- Make it specific enough that two implementations would behave identically
