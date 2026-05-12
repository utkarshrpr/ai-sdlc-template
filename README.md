# AI-SDLC Template

> AI-assisted spec-driven SDLC workflow template for engineering teams.

## Overview

This repo provides a complete set of Claude Code skills, agents, and templates that enforce a spec-driven development workflow. AI writes specifications and technical design documents, engineers review, and AI executes — with human approval at every gate.

**No assumptions by AI. Questions first, always.**

## Why Spec-Driven Development?

- Specs force clarity before code is written
- Business team gets visibility and approval power over product decisions
- Technical design docs catch architecture issues before implementation
- AI-generated docs are consistent, thorough, and follow templates
- Engineers focus on reviewing and deciding, not drafting boilerplate

## Workflow

```
Problem Statement (from business team)
        │
        ▼
┌─────────────────┐
│  /discover      │  AI generates Product Workflow Doc
│  (Full track)   │  Engineer reviews, business team approves
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  /breakdown     │  AI creates Epics + Micro-tasks
│                 │  as GitHub Issues
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  /spec          │  AI generates Spec per task
│                 │  Engineer reviews, business team approves
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  /design        │  AI generates Technical Design Doc per epic
│                 │  Engineer reviews
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  feature-builder│  AI implements code
│  qa-agent       │  AI writes tests
│  docs-agent     │  AI updates docs
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  security-agent │  Review only — suggest fixes
│  performance-   │  Review only — suggest fixes
│  agent          │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  Engineer       │  Reviews, applies fixes, creates PR
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  pr-reviewer    │  Reviews the PR — suggest fixes
└────────┬────────┘
         │
         ▼
    Final review + Merge
```

## Quick Start

See [guides/setup.md](guides/setup.md) for installation and configuration.

## Workflow Tracks

| Track | When to use | Steps |
|-------|------------|-------|
| **Full** | New products, major features | Problem → Workflow Doc → Approval → Epics → Specs → Approval → TDD → Implementation |
| **Standard** | Medium features, clear scope | Problem → Spec → Approval → TDD → Implementation |
| **Light** | Bug fixes, small changes | Problem → Spec → Implementation |

See [guides/track-selection.md](guides/track-selection.md) for detailed guidance.

## Skills

| Skill | Command | Description |
|-------|---------|-------------|
| Discover | `/discover` | Generates a Product Workflow Doc from a problem statement |
| Spec | `/spec` | Generates functional + non-functional requirements specification |
| Design | `/design` | Generates a Technical Design Document from approved specs |
| Breakdown | `/breakdown` | Breaks a Workflow Doc into epics and micro-tasks as GitHub Issues |
| Implement | `/implement` | Implements a feature from approved spec + TDD |
| Review Spec | `/review-spec` | Reviews a spec for completeness, gaps, and contradictions |

## Agents

| Agent | Purpose | Writes Code? |
|-------|---------|:---:|
| `spec-writer` | Orchestrates full spec-writing flow with interview | No |
| `technical-design-writer` | Orchestrates TDD creation from approved specs | No |
| `project-planner` | Creates epics + micro-tasks as GitHub Issues | No |
| `feature-builder` | Implements features from spec + TDD | Yes |
| `qa-agent` | Writes tests, reviews coverage | Yes |
| `docs-agent` | Updates API docs, changelogs, README | Yes |
| `pr-reviewer` | Reviews PRs for code quality | No |
| `security-agent` | Reviews for security vulnerabilities | No |
| `performance-agent` | Reviews for performance issues | No |

## Templates

| Template | Purpose |
|----------|---------|
| [Workflow Doc](templates/workflow-doc.md) | Product Workflow Document |
| [Spec](templates/spec.md) | Functional + Non-Functional Requirements |
| [Technical Design](templates/technical-design.md) | Epic-level Technical Design Document |
| [Epic Issue](templates/epic-issue.md) | GitHub Issue template for epics |
| [Task Issue](templates/task-issue.md) | GitHub Issue template for micro-tasks |

## Guides

- [Workflow Guide](guides/workflow-guide.md) — Step-by-step guide for each workflow track
- [Track Selection](guides/track-selection.md) — How to choose the right track
- [Setup](guides/setup.md) — Installation and configuration

## Contributing

To add or modify skills/agents:
1. Follow the existing format in `skills/` or `agents/`
2. Update the relevant tables in this README
3. Test the skill/agent on a sample feature before merging
