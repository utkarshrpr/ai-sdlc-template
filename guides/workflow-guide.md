# Workflow Guide

Step-by-step guide for engineers covering all three workflow tracks: Full, Standard, and Light.

For help choosing a track, see [Track Selection](track-selection.md).

---

## Full Track

Use for new products, major features, or work that spans multiple epics. This is the complete spec-driven workflow.

### Phase 1: Discovery

1. **Receive problem statement from business team.** This arrives as a brief description of the problem to solve, not a solution. It may come via Slack, email, or a GitHub issue.

2. **Generate a Workflow Doc.** Run `/discover` (skill) or use the `spec-writer` agent (agent). The AI will ask clarifying questions before generating anything. Answer them — the more context you provide, the better the output.

3. **Review the Workflow Doc.** Read it carefully. Check that the problem framing, user personas, proposed features, and success metrics match your understanding. Iterate with AI until it is solid.

4. **Get business team approval.** Create a GitHub issue with the Workflow Doc content. Tag the business team. They approve by commenting on the issue. Do not proceed until you have approval.

### Phase 2: Planning

5. **Break down into epics and tasks.** Run `/breakdown` (skill) or use the `project-planner` agent. This creates GitHub issues for each epic and micro-task, linked to the parent Workflow Doc issue.

6. **Generate specs for each task.** For each micro-task, run `/spec` (skill) or use the `spec-writer` agent. Each spec covers functional requirements, non-functional requirements, edge cases, and acceptance criteria.

7. **Get specs approved.** Create GitHub issues with spec content (or update the existing task issues). Share with business team for approval via comments.

### Phase 3: Design

8. **Generate Technical Design Documents.** Once specs are approved, run `/design` (skill) or use the `technical-design-writer` agent. This produces one TDD per epic covering architecture, data models, API contracts, and implementation approach.

9. **Review the TDD.** Check the architecture decisions, data model choices, and API design. Iterate with AI until the design is sound. TDDs do not require business team approval — this is an engineering decision.

### Phase 4: Implementation

10. **Implement code.** Use the `feature-builder` agent. It reads the approved spec and TDD, then writes the implementation. Review the generated code as it is produced.

11. **Write tests.** Use the `qa-agent`. It generates unit tests, integration tests, and edge case tests based on the spec's acceptance criteria.

12. **Security review.** Use the `security-agent`. It reviews the implementation for vulnerabilities and suggests fixes. It does NOT modify code — you decide which suggestions to apply.

13. **Performance review.** Use the `performance-agent`. It reviews for performance issues (N+1 queries, missing indexes, unnecessary allocations, etc.) and suggests fixes. It does NOT modify code.

14. **Update documentation.** Use the `docs-agent`. It updates API docs, changelogs, and README files based on what was implemented.

### Phase 5: Review and Merge

15. **Apply fixes.** Review all suggestions from the security and performance agents. Apply the ones that make sense. Use your judgment.

16. **Create a PR.** You create the PR manually. No agent or skill creates PRs.

17. **AI PR review.** Use the `pr-reviewer` agent. It reviews the PR for code quality, consistency, and potential issues. It suggests changes but does NOT modify code.

18. **Final review and merge.** Do your own final review. Address any remaining feedback. Merge when ready.

---

## Standard Track

Use for medium-sized features where the scope is already clear. You know what to build — you need to spec it out and design it properly.

Skip the Workflow Doc and epic breakdown. Start directly with spec writing.

1. **Start with a clear feature description.** Write a 2-3 sentence description of what you are building and why.

2. **Generate a spec.** Run `/spec` or use the `spec-writer` agent. The AI will interview you to fill in gaps.

3. **Review the spec.** Check requirements, edge cases, and acceptance criteria. Iterate until complete.

4. **Get business team approval.** Create a GitHub issue with the spec. Business team approves via comment.

5. **Generate a TDD.** Run `/design` or use the `technical-design-writer` agent. Review the design.

6. **Implement.** Use `feature-builder` agent. Then `qa-agent` for tests.

7. **Review.** Run `security-agent` and `performance-agent` for review suggestions. Use `docs-agent` for documentation.

8. **Create PR.** You create the PR manually. Use `pr-reviewer` agent for AI review.

9. **Final review and merge.**

---

## Light Track

Use for bug fixes, small enhancements, config changes, and anything where the scope is obvious and minimal.

1. **Write a brief spec.** A few sentences covering: what is the problem, what is the fix, how will you verify it. You can run `/spec` if you want structure, but it is not required.

2. **Implement the fix.** Use `feature-builder` agent or code it yourself.

3. **Write tests.** Use `qa-agent` or write tests yourself.

4. **Create PR.** Use `pr-reviewer` for AI review if you want a second pair of eyes.

5. **Merge.**

No TDD. No business team approval (unless the change affects product behavior). No epic breakdown.

---

## Skills vs Agents

**Skills** (slash commands like `/spec`, `/design`, `/discover`) are best for:
- Quick, one-off document generation
- When you want to run a single step and stay in control
- When you already have all the context and just need output

**Agents** (`spec-writer`, `feature-builder`, `qa-agent`, etc.) are best for:
- The full orchestrated flow with back-and-forth conversation
- When the AI needs to interview you or ask clarifying questions
- When the task involves multiple steps that the agent coordinates

In practice: use skills when you know exactly what you want, use agents when you want the AI to guide the process.

---

## Tips

- **Do not skip the review steps.** AI-generated specs and code are a starting point, not a finished product. Your review is the quality gate.
- **Iterate on specs before moving to implementation.** Fixing a spec is cheap. Fixing code is expensive. Fixing production is very expensive.
- **Use `/review-spec` to sanity-check specs.** Run it before sharing with the business team to catch gaps and contradictions early.
- **Business team approves by commenting on GitHub issues.** Keep specs in issues so they have visibility and a clear place to provide feedback.
- **All generated documents go in your project's `docs/` directory.** Specs, TDDs, and Workflow Docs are stored as markdown alongside your code.
- **Engineers create PRs manually.** This is intentional. The PR is your checkpoint to review everything before it goes to the team.
