# Track Selection Guide

How to choose the right workflow track for your task.

---

## The Three Tracks

### Full Track

**"I need to think through the whole product/feature space."**

Use when there are multiple features to consider, a new product area to explore, or cross-cutting concerns that affect several parts of the system.

**Examples:**
- Building a new billing system with subscription management, invoicing, and payment processing
- Adding a multi-tenant architecture to an existing single-tenant application
- Creating a new customer-facing dashboard that pulls data from multiple backend services

**What you get:** Workflow Doc, business team approval, epic breakdown, specs per task, TDDs per epic, full implementation pipeline.

---

### Standard Track

**"I know what to build, I need to spec it out."**

Use when you have a single, well-scoped feature. The problem is clear, the solution space is narrow, and you just need to formalize the requirements and design before building.

**Examples:**
- Adding CSV export to an existing reports page
- Implementing a webhook notification system for a specific event type
- Building a new API endpoint for a mobile app feature that mirrors existing web functionality

**What you get:** Spec, business team approval, TDD, implementation pipeline. No Workflow Doc or epic breakdown.

---

### Light Track

**"I know exactly what to change."**

Use when the scope is obvious, the change is small, and adding process would slow things down without adding value. Bug fixes, config changes, small enhancements.

**Examples:**
- Fixing a date formatting bug in the invoice PDF generator
- Adding a missing index to a PostgreSQL table to fix a slow query
- Updating an environment variable and its associated Docker config

**What you get:** Brief spec, implementation, PR. No TDD, no business team approval (unless product behavior changes).

---

## Decision Flowchart

```
Start here
  │
  ▼
Does this involve multiple features
or a new product area?
  │
  ├── Yes ──▶ FULL TRACK
  │
  ▼
  No
  │
  ▼
Is the scope a single, well-defined feature
that needs requirements and design?
  │
  ├── Yes ──▶ STANDARD TRACK
  │
  ▼
  No
  │
  ▼
Is this a bug fix, small enhancement,
or config change with obvious scope?
  │
  ├── Yes ──▶ LIGHT TRACK
  │
  ▼
  No
  │
  ▼
When in doubt, start with STANDARD.
You can always upgrade to Full if
scope grows, or downgrade to Light
if it turns out to be simpler than expected.
```

---

## When to Switch Tracks

- **Upgrade from Standard to Full** if you start speccing a feature and realize it touches multiple systems or needs product-level thinking about user flows and trade-offs.
- **Downgrade from Standard to Light** if the spec turns out to be 3 sentences and the implementation is a one-file change.
- **Upgrade from Light to Standard** if what you thought was a simple bug fix reveals a deeper design issue that needs a proper spec and TDD.

Use your judgment. The tracks are guidelines, not bureaucracy.
