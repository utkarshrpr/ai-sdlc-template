# AI-SDLC Template — Project Instructions

This repo contains the SDLC workflow templates, skills, and agents for AI-assisted spec-driven development.

## Core Principles

1. **Question-first approach** — AI must always ask clarifying questions before generating any document. No assumptions. If something is unclear, ask.
2. **Specs before code** — No implementation begins without an approved specification.
3. **Human review at every stage** — AI generates, engineers review, business team approves.
4. **Engineer autonomy** — Engineers choose the workflow track (Full/Standard/Light) based on their judgment.

## Workflow Tracks

- **Full Track** — New products, major features: Problem → Workflow Doc → Approval → Epics + Micro-tasks → Specs → Approval → TDD → Implementation
- **Standard Track** — Medium features: Problem → Spec → Approval → TDD → Implementation
- **Light Track** — Bug fixes, small changes: Problem → Spec → Implementation

## Personas

- **Specs and product documents** are written from the perspective of a **seasoned product engineer with 15+ years of experience**.
- **Technical design documents** are written from the perspective of a **seasoned staff engineer with 15+ years of experience**.

## Code-Writing Agents

Only these agents write code:
- `feature-builder` — implements features
- `qa-agent` — writes tests
- `docs-agent` — updates documentation

## Review-Only Agents

These agents present reviews and suggest fixes but do NOT modify code:
- `pr-reviewer`
- `security-agent`
- `performance-agent`

## Rules

- Engineers create PRs manually — no agent or skill creates PRs.
- All specs and TDDs are stored as markdown in the target project's `docs/` directory.
- GitHub issues are used for business team visibility and approval (via comments).
- Templates in `templates/` define the structure for all generated documents.

## Tech Stack

The team works across: TypeScript, Python/FastAPI, Node.js/Express, React, PostgreSQL, MongoDB, Google Cloud, Docker, GitHub Actions.
