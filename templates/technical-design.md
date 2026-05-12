# Technical Design Document

## Epic Title & Link

<!-- AI: Reference the epic GitHub issue and title. -->

**Epic:** [Epic title]
**Issue:** [Link to GitHub issue]

## Overview

<!-- AI: 2-3 sentences describing what this design covers. State the scope clearly — which features/tasks from the epic are addressed. -->

[What this design covers and its scope]

## Approved Spec Reference

<!-- AI: Link to the approved spec(s) that this design is based on. If multiple specs feed into this epic, list all of them. -->

- [Link to spec file or GitHub issue]

## Architecture

<!-- AI: Explain how this feature fits into the existing system. Ask the engineer: "Can you walk me through the current architecture that this feature will interact with?" Draw connections to existing services, databases, and infrastructure. -->

### Current Architecture
[Describe the relevant parts of the existing system]

### How This Feature Fits In
[Describe where the new feature sits in the architecture — new service, new module in existing service, frontend component, etc.]

### Architecture Diagram
```
[Text-based architecture diagram showing components and data flow]
```

## System Design

<!-- AI: Detail the components, their responsibilities, and how they interact. Ask the engineer about existing patterns and conventions in the codebase. -->

### Components

| Component | Responsibility | Location |
|-----------|---------------|----------|
| [Component name] | [What it does] | [File path or service] |

### Data Flow
```
[Step-by-step data flow through the system]
1. User triggers [action]
2. [Component A] receives request
3. [Component A] calls [Component B]
4. [Component B] queries [Database]
5. Response flows back through [path]
```

### Key Interactions
[Describe critical interactions between components, including sync vs async, error propagation, retry logic]

## Data Model

<!-- AI: Ask the engineer about existing database schemas and conventions. Check the codebase for existing models/migrations before proposing new ones. -->

### New Tables/Collections

#### [Table/Collection Name]
```sql
-- PostgreSQL example
CREATE TABLE table_name (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    field_name TYPE CONSTRAINTS,
    created_at TIMESTAMP DEFAULT NOW(),
    updated_at TIMESTAMP DEFAULT NOW()
);

-- Indexes
CREATE INDEX idx_table_field ON table_name(field_name);
```

```javascript
// MongoDB example
{
  field_name: { type: String, required: true },
  created_at: { type: Date, default: Date.now }
}
```

### Schema Changes to Existing Tables
| Table | Change | Migration strategy |
|-------|--------|-------------------|
| [Table name] | [Add/modify/remove column] | [How to migrate safely] |

### Relationships
[Describe relationships between new and existing data models]

## API Design

<!-- AI: Follow existing API conventions in the codebase. Ask the engineer about authentication middleware, validation patterns, and error response formats already in use. -->

### Endpoint 1: [METHOD] [/api/path]

**Description:** [What it does]
**Authentication:** [JWT / API key / Public]
**Rate limiting:** [If applicable]

**Request:**
```json
{
  "field": "type — validation rules"
}
```

**Response (200):**
```json
{
  "field": "type"
}
```

**Error Responses:**
| Status | Code | Description |
|--------|------|-------------|
| 400 | VALIDATION_ERROR | [When this occurs] |
| 401 | UNAUTHORIZED | [When this occurs] |
| 404 | NOT_FOUND | [When this occurs] |

## Third-Party Integrations

<!-- AI: Ask the engineer about each integration: "Have we used this service before? Is there an existing client/SDK in the codebase?" Document rate limits, authentication, and failure handling for each. -->

### Integration 1: [Service Name]
- **Purpose:** [Why we're integrating]
- **API/SDK:** [Which API or SDK to use]
- **Authentication:** [How we authenticate]
- **Rate limits:** [Known limits]
- **Failure handling:** [What happens when this service is down]
- **Cost implications:** [If any]

## Infrastructure

<!-- AI: Ask the engineer about existing GCP setup, Docker configuration, and CI/CD pipelines. -->

### GCP Services
| Service | Purpose | Configuration |
|---------|---------|--------------|
| [e.g., Cloud Run] | [What it hosts] | [Key config: memory, CPU, scaling] |

### Docker Changes
[New Dockerfiles, changes to existing ones, new services in docker-compose]

### CI/CD Changes
[New GitHub Actions workflows, changes to existing pipelines, new deployment stages]

### Environment Variables
| Variable | Purpose | Where to set |
|----------|---------|-------------|
| [VAR_NAME] | [What it's for] | [GCP Secret Manager / .env / CI] |

## Security Considerations

<!-- AI: Think through authentication, authorization, data protection, and input validation for every component. Ask the engineer about existing security patterns. -->

- **Authentication:** [How users/services authenticate]
- **Authorization:** [Who can access what — RBAC, ownership checks, etc.]
- **Data protection:** [Encryption at rest/in transit, PII handling]
- **Input validation:** [What inputs need validation, sanitization approach]
- **Secrets management:** [How secrets are stored and accessed]

## Performance Considerations

<!-- AI: Consider query patterns, caching, indexing, and scalability. Ask the engineer about expected load and current bottlenecks. -->

- **Expected load:** [Requests per second, data volume]
- **Database queries:** [Key queries, expected performance, indexing strategy]
- **Caching strategy:** [What to cache, TTL, invalidation]
- **Async processing:** [What can be done asynchronously — queues, background jobs]
- **Bundle size impact:** [For frontend changes — new dependencies, code splitting]

## Testing Strategy

<!-- AI: Define what types of tests are needed. Reference existing test patterns in the codebase. -->

| Test Type | What to Cover | Framework |
|-----------|--------------|-----------|
| Unit tests | [Key logic, utilities, transformations] | [Jest / Pytest / etc.] |
| Integration tests | [API endpoints, database operations] | [Supertest / etc.] |
| E2E tests | [Critical user flows] | [Playwright / Cypress / etc.] |

## Migration Strategy

<!-- AI: If this changes existing functionality, describe how to migrate safely. If greenfield, write "Greenfield feature — no migration required." -->

### Migration Steps
1. [Step 1 — e.g., deploy database migration]
2. [Step 2 — e.g., deploy new API with feature flag]
3. [Step 3 — e.g., enable feature flag for internal users]
4. [Step 4 — e.g., enable for all users]

### Data Migration
[How existing data will be migrated, if applicable]

## Rollback Plan

<!-- AI: Always define how to undo this change if something goes wrong. -->

1. [Step 1 — e.g., disable feature flag]
2. [Step 2 — e.g., revert database migration]
3. [Step 3 — e.g., redeploy previous version]

**Estimated rollback time:** [e.g., < 5 minutes]

## Task-Level Design Notes

<!-- AI: Only include this section for micro-tasks that are complex enough to warrant their own design thinking. Simple CRUD tasks or UI components following existing patterns do NOT need entries here. Flag tasks as complex if they involve: new integrations, algorithm/logic decisions, data model changes, or performance-sensitive work. -->

### [Task Title] (Complex)
**Why this needs design notes:** [What makes this task non-trivial]
**Approach:** [How to implement it]
**Key decisions:** [Technical choices and why]

## Open Questions

<!-- AI: Track every unresolved technical question. Never assume an answer. -->

| # | Question | Who should answer | Status |
|---|----------|------------------|--------|
| 1 | [Question] | [Engineer] | Open |

## Alternatives Considered

<!-- AI: Document what approaches were considered and rejected. This is valuable for future engineers who might ask "why didn't we just do X?" -->

### Alternative 1: [Approach name]
- **Description:** [What this approach would look like]
- **Pros:** [Advantages]
- **Cons:** [Disadvantages]
- **Why rejected:** [Specific reason this wasn't chosen]

### Alternative 2: [Approach name]
- **Description:**
- **Pros:**
- **Cons:**
- **Why rejected:**
