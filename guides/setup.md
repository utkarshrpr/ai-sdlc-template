# Setup Guide

How to set up the AI-SDLC workflow in your project.

---

## Prerequisites

Before you start, make sure you have:

- **Claude Code CLI** installed and authenticated
- **GitHub CLI (`gh`)** installed and authenticated — run `gh auth status` to verify
- **A GitHub repository** for your project with a GitHub Project board set up (used for epic/task tracking)

---

## Step 1: Clone this repo

```bash
git clone <this-repo-url> ~/ai-sdlc-template
```

Pick a stable location. Your projects will reference this directory.

---

## Step 2: Add skills to your project

Skills are slash commands (like `/spec`, `/discover`, `/design`) that Claude Code picks up from your project's `.claude/skills/` directory.

**Option A: Symlink (recommended)**

Keeps your project in sync with the latest version of the skills automatically.

```bash
cd your-project
mkdir -p .claude/skills
ln -s ~/ai-sdlc-template/skills/*.md .claude/skills/
```

**Option B: Copy**

Use if you want to pin a specific version or customize skills per project.

```bash
cd your-project
mkdir -p .claude/skills
cp ~/ai-sdlc-template/skills/*.md .claude/skills/
```

---

## Step 3: Add agents to your project

Agents are long-running, multi-step workflows that Claude Code runs from your project's `.claude/agents/` directory.

**Option A: Symlink (recommended)**

```bash
cd your-project
mkdir -p .claude/agents
ln -s ~/ai-sdlc-template/agents/*.md .claude/agents/
```

**Option B: Copy**

```bash
cd your-project
mkdir -p .claude/agents
cp ~/ai-sdlc-template/agents/*.md .claude/agents/
```

---

## Step 4: Set up CLAUDE.md in your project

Your project needs a `CLAUDE.md` file that tells Claude Code about the SDLC workflow and where to find templates.

Add the following to your project's `CLAUDE.md` (create it if it does not exist):

```markdown
## SDLC Workflow

This project follows a spec-driven development workflow. See ~/ai-sdlc-template/guides/workflow-guide.md for the full process.

### Templates

When generating specs, TDDs, or workflow docs, use the templates from:
- Workflow Doc: ~/ai-sdlc-template/templates/workflow-doc.md
- Spec: ~/ai-sdlc-template/templates/spec.md
- Technical Design: ~/ai-sdlc-template/templates/technical-design.md
- Epic Issue: ~/ai-sdlc-template/templates/epic-issue.md
- Task Issue: ~/ai-sdlc-template/templates/task-issue.md

### Rules

- All specs and TDDs are stored in this project's `docs/` directory as markdown.
- Engineers create PRs manually. No agent or skill creates PRs.
- Business team approves specs by commenting on GitHub issues.
```

Adjust the path to `~/ai-sdlc-template` if you cloned the repo elsewhere.

---

## Step 5: Create the docs directory

Generated specs, TDDs, and workflow docs are stored in your project:

```bash
cd your-project
mkdir -p docs
```

---

## Step 6: Verify the setup

Run these checks to confirm everything is working:

**Check skills are available:**

```bash
ls -la your-project/.claude/skills/
# Should show: breakdown.md, design.md, discover.md, implement.md, review-spec.md, spec.md
```

**Check agents are available:**

```bash
ls -la your-project/.claude/agents/
# Should show: docs-agent.md, feature-builder.md, performance-agent.md,
#   pr-reviewer.md, project-planner.md, qa-agent.md, security-agent.md,
#   spec-writer.md, technical-design-writer.md
```

**Check `gh` CLI works:**

```bash
gh auth status
# Should show: Logged in to github.com
gh repo view --json name
# Should show your repo name
```

**Test a skill:**

Open Claude Code in your project directory and run `/spec`. It should prompt you for a feature description and start the spec-writing interview flow.

---

## Project Structure After Setup

```
your-project/
├── .claude/
│   ├── skills/          # Symlinked or copied from ai-sdlc-template/skills/
│   │   ├── breakdown.md
│   │   ├── design.md
│   │   ├── discover.md
│   │   ├── implement.md
│   │   ├── review-spec.md
│   │   └── spec.md
│   └── agents/          # Symlinked or copied from ai-sdlc-template/agents/
│       ├── docs-agent.md
│       ├── feature-builder.md
│       ├── performance-agent.md
│       ├── pr-reviewer.md
│       ├── project-planner.md
│       ├── qa-agent.md
│       ├── security-agent.md
│       ├── spec-writer.md
│       └── technical-design-writer.md
├── docs/                # Generated specs, TDDs, workflow docs
├── CLAUDE.md            # Project instructions referencing templates
└── ...                  # Your project code
```

---

## Updating

If you used symlinks, pulling the latest changes in `~/ai-sdlc-template` updates all your projects automatically.

If you copied the files, re-copy when you want to pick up changes:

```bash
cp ~/ai-sdlc-template/skills/*.md your-project/.claude/skills/
cp ~/ai-sdlc-template/agents/*.md your-project/.claude/agents/
```
