# Specification

## Feature/Task Title

<!-- AI: Use a clear, descriptive title. e.g., "AI-Based Candidate Scoring Engine" not "Scoring Feature" -->

[Feature title]

## Parent Epic

<!-- AI: Link to the parent epic GitHub issue. If this spec is standalone (Standard/Light track), write "N/A — standalone feature". -->

[Link to epic issue or N/A]

## Overview

<!-- AI: 2-3 sentences covering what this feature does and why it's being built. Reference the problem statement from the workflow doc if one exists. -->

**What:** [What this feature does]
**Why:** [What problem it solves, what value it delivers]

## Functional Requirements

<!-- AI: Each requirement must be specific, testable, and unambiguous. Use "The system shall..." format. Number them for traceability. Ask the engineer about every requirement — do not invent requirements that weren't discussed. If a requirement is unclear, add it to Open Questions instead. -->

| ID | Requirement | Priority |
|----|------------|----------|
| FR-01 | The system shall [specific, testable behavior] | Must have |
| FR-02 | The system shall [specific, testable behavior] | Must have |
| FR-03 | The system shall [specific, testable behavior] | Should have |
| FR-04 | The system shall [specific, testable behavior] | Nice to have |

## Non-Functional Requirements

<!-- AI: Ask the engineer about each category. Do not skip categories — if a category doesn't apply, explicitly state "Not applicable for this feature" with a reason. -->

### Performance
| ID | Requirement |
|----|------------|
| NFR-01 | [e.g., API response time shall be < 200ms for 95th percentile] |
| NFR-02 | [e.g., System shall support 100 concurrent users] |

### Security
| ID | Requirement |
|----|------------|
| NFR-03 | [e.g., All API endpoints shall require authentication] |
| NFR-04 | [e.g., User data shall be encrypted at rest] |

### Scalability
| ID | Requirement |
|----|------------|
| NFR-05 | [e.g., System shall handle 10x current data volume without architecture changes] |

### Reliability
| ID | Requirement |
|----|------------|
| NFR-06 | [e.g., System shall have 99.9% uptime] |

### Accessibility
| ID | Requirement |
|----|------------|
| NFR-07 | [e.g., UI shall meet WCAG 2.1 AA standards] |

## User Stories

<!-- AI: Write user stories for each key interaction. Ask the engineer to validate each one. -->

1. **As a** [role], **I want to** [action], **so that** [outcome].
2. **As a** [role], **I want to** [action], **so that** [outcome].
3. **As a** [role], **I want to** [action], **so that** [outcome].

## Acceptance Criteria

<!-- AI: Write acceptance criteria in Given/When/Then format. Each functional requirement should have at least one acceptance criterion. Ask the engineer about edge cases for each. -->

### FR-01: [Requirement title]
- **Given** [precondition], **when** [action], **then** [expected result].
- **Given** [precondition], **when** [action], **then** [expected result].

### FR-02: [Requirement title]
- **Given** [precondition], **when** [action], **then** [expected result].

## UI/UX Requirements

<!-- AI: If this feature has a UI component, describe layouts, interactions, and states. If no UI, write "This feature has no user-facing interface." Ask the engineer: "Are there any mockups, wireframes, or design references?" -->

- **Layout:** [Description of page/component layout]
- **Key interactions:** [How the user interacts with UI elements]
- **States:** [Loading, empty, error, success states]
- **Responsive:** [Mobile/tablet/desktop requirements]

## Data Requirements

<!-- AI: Ask the engineer about data models, storage, and relationships. Reference existing schemas if applicable. -->

### New Data Models
| Model/Table | Fields | Storage |
|-------------|--------|---------|
| [Model name] | [Key fields] | [PostgreSQL / MongoDB] |

### Schema Changes to Existing Models
| Model/Table | Change | Reason |
|-------------|--------|--------|
| [Model name] | [Add/modify/remove field] | [Why] |

### Data Migration
<!-- AI: If existing data needs to be migrated, describe the migration strategy. If no migration needed, state "No data migration required." -->

[Migration strategy or "No data migration required"]

## API Requirements

<!-- AI: If this feature involves API endpoints, document each one. If no API, write "No new API endpoints required." Ask the engineer about authentication, rate limiting, and error responses for each endpoint. -->

### Endpoint 1: [Method] [Path]
- **Description:** [What it does]
- **Authentication:** [Required / Public]
- **Request body:**
```json
{
  "field": "type — description"
}
```
- **Response (200):**
```json
{
  "field": "type — description"
}
```
- **Error responses:** [List error codes and when they occur]

## Dependencies

<!-- AI: Ask the engineer: "Does this feature depend on any other tasks, features, or external services?" List both internal and external dependencies. -->

| Dependency | Type | Status |
|-----------|------|--------|
| [Feature/task/service] | [Internal / External] | [Available / In progress / Blocked] |

## Edge Cases & Error Handling

<!-- AI: For each functional requirement, ask: "What happens if the input is invalid? What if the external service is down? What if the user does something unexpected?" Document each edge case. -->

| # | Scenario | Expected Behavior |
|---|----------|------------------|
| 1 | [Edge case description] | [How the system should handle it] |
| 2 | [Edge case description] | [How the system should handle it] |

## Open Questions

<!-- AI: Track every unresolved question. Never assume an answer. -->

| # | Question | Who should answer | Status |
|---|----------|------------------|--------|
| 1 | [Question] | [Engineer / Business team] | Open |

## Approval Status

- [ ] Engineer reviewed
- [ ] Business team approved
- **Status:** Pending
- **Date:** [Date of last status change]
- **Approved by:** [Name, if approved]
