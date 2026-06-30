# Claude Skills for GitHub & Open Source Growth

A collection of 7 Claude skills designed to build a strong GitHub presence, produce high-quality open-source work, and develop engineering skills that recruiters notice. Each skill follows a phased methodology with concrete outputs — files, directories, and reports you can push to GitHub immediately.

Built for engineers who have real domain expertise from their day job but haven't yet made it visible on GitHub.

## Skills

### 1. [Codebase Mapper](./codebase-mapper/)

Map the architecture of any codebase and produce publishable documentation with Mermaid diagrams, component breakdowns, and design-decision analysis. Output is a directory of Markdown files ready to push as a standalone GitHub repo.

**Trigger:** "Map this codebase" · "Architecture of this repo" · "How is this project structured"

**Output:** `architecture-[project]/` directory with 5 Markdown files + Mermaid diagrams

---

### 2. [Project Scaffolder](./project-scaffolder/)

Create professional-grade project repositories where every file has real content, tests run, and CI passes. Supports TypeScript libraries, CLI tools, React apps, Python packages, and APIs.

**Trigger:** "Scaffold a project" · "Set up a new repo" · "Create a TypeScript library"

**Output:** Complete project directory ready to `git push`

---

### 3. [Codebase-to-Course](./codebase-to-course/)

Transform engineering knowledge into published educational content — Build-Your-Own tutorials, deep-dive articles, or learning paths. Turn what you know from building real systems into content other engineers bookmark and share.

**Trigger:** "Turn this into a tutorial" · "Write a deep dive about X" · "Build-Your-Own tutorial"

**Output:** Tutorial repo with progressive build steps, or a deep-dive article with diagrams and code

---

### 4. [Repo README Generator](./repo-readme-gen/)

Produce professional README.md files that pass the 10-second recruiter test. Adapts structure to the project type — library, CLI, web app, API, or educational repo.

**Trigger:** "Write a README" · "Improve my README" · "Make this repo presentable"

**Output:** Complete `README.md` file, immediately committable

---

### 5. [Code Quality Improver](./code-quality-improver/)

Analyze code for quality issues and produce actionable improvements — severity-ranked fixes with actual code, reliability patterns, and complete test suites. Every suggestion includes the implementation, not just the diagnosis.

**Trigger:** "Improve this code" · "Add tests" · "Make this production-ready" · "Code review this"

**Output:** `QUALITY_REPORT.md` with prioritized fixes + test files

---

### 6. [Open Source Contributor](./oss-contributor/)

Guide strategic open-source contributions — find the right projects, identify specific issues, prepare PRs with proper descriptions, and build a visible contribution history targeting recognized repos.

**Trigger:** "Help me contribute to open source" · "Find projects to contribute to" · "Prepare a PR"

**Output:** `CONTRIBUTION_PLAN.md` with specific repos, issues, and approach — or a PR-ready package

---

### 7. [Debug Navigator](./debug-navigator/)

Systematically debug issues and navigate unfamiliar codebases. Follows a reproducible methodology — reproduce, narrow, identify, fix, prevent — and teaches the debugging process as it solves the problem.

**Trigger:** "Debug this" · "Why is this broken" · "Help me understand this code" · "Trace this error"

**Output:** Root cause analysis + fix + preventive test — or a structured code trace

---

## Installation

Copy any skill folder into `~/.claude/skills/`:

```bash
# Install all skills
cp -r skills/* ~/.claude/skills/

# Or install one at a time
cp -r skills/codebase-mapper ~/.claude/skills/
```

## Structure

Each skill follows the same layout:

```
skill-name/
├── README.md              # What the skill does, how to trigger it
├── SKILL.md               # Main instructions Claude follows
└── references/            # Templates, patterns, and checklists
    └── [reference].md       loaded only during the relevant phase
```

Reference files use progressive disclosure — Claude reads them only when it reaches the relevant phase, not upfront. This keeps context lean and output quality high.

## Recommended Order

| Priority | Skill | Why |
|----------|-------|-----|
| 1 | **project-scaffolder** | Every repo you create starts here — proper structure from day one |
| 2 | **repo-readme-gen** | Apply to every project immediately — the first thing recruiters see |
| 3 | **codebase-to-course** | Turn your domain knowledge into published content — your strongest differentiator |
| 4 | **codebase-mapper** | Produce architecture deep-dives of open-source projects — shows systems thinking |
| 5 | **code-quality-improver** | Harden your projects with tests and reliability patterns |
| 6 | **oss-contributor** | Start contributing to recognized open-source projects |
| 7 | **debug-navigator** | Use during development — accelerates everything else |
