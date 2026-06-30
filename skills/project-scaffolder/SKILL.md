---
name: project-scaffolder
description: >
  Scaffold professional-grade project repositories with proper structure, configuration,
  testing, CI/CD, and documentation — ready to push to GitHub immediately. The output
  is a complete project directory where every file has real content, tests actually run,
  and CI actually passes. Use this skill whenever someone wants to create a new project,
  library, CLI tool, or application from scratch. Also trigger when users mention 'scaffold
  a project,' 'set up a new repo,' 'create a project structure,' 'init a new project,'
  'bootstrap a repo,' 'start a new TypeScript/Python/React project,' 'create a library,'
  'make this repo look professional,' 'add proper project structure,' 'set up CI/CD,' or
  'make this production-ready.' This skill produces a ready-to-push directory with working
  tests, real CI configuration, and a README that passes the 10-second recruiter test.
---

# Project Scaffolder

Create project structures that signal engineering maturity. Every file earns its place. Tests
run. CI passes. The README communicates clearly. A recruiter clicking into this repo should
think: "This person knows how to set up a real project."

The output is a **complete project directory** — not a plan, not a template, not a checklist.
Real files with real content that can be pushed to GitHub in the next 30 seconds.

## First-Run Interaction

When triggered without a clear project specification, ask exactly one question:

> What are you building? Give me: (1) what it does in one sentence, (2) the language, and
> (3) whether it's a library, CLI tool, web app, or API.

If the user has already provided this context, skip the question and build.

---

## The Process

### Phase 1: Classify the Project

Every project falls into one of these categories. Pick the right one — the entire scaffold
depends on it.

| Type | Signal | Key characteristic |
|------|--------|--------------------|
| **Library/Package** | "npm package", "pip install", "importable", "SDK" | Has a public API. Published to a registry. No UI. |
| **CLI Tool** | "command line", "terminal", "CLI", "script" | Has argument parsing. Runs from terminal. May be published. |
| **Web App** | "React app", "dashboard", "frontend", "SPA" | Has UI components. Runs in browser. May have a backend. |
| **API/Backend** | "REST API", "GraphQL", "server", "backend" | Has endpoints. Runs on a server. Serves data. |
| **Full Stack** | "app with frontend and backend" | Combination. Needs clear separation. |

**Scale matters too:**
- **Small** (< 500 lines expected): Flat structure. Minimal tooling.
- **Medium** (500-5000 lines): Module directories. Testing. CI.
- **Large** (5000+ lines): Deeper nesting. Multiple concerns. Linting. Docs.

Match tooling to scale. A 200-line utility does not need ESLint + Prettier + Husky +
lint-staged + commitlint + semantic-release.

### Phase 2: Generate the Scaffold

Read `references/project-templates.md` for the exact directory structure and file contents
for each project type. Read `references/ci-templates.md` for GitHub Actions workflows.

**For every file you create, follow these rules:**

1. **No placeholder content.** `// TODO: implement` is worse than not having the file. Every
   file has real, working content — even if minimal.
2. **No empty directories.** If there's nothing to put in `src/utils/` yet, don't create it.
   The directory appears when the first utility function is written.
3. **Tests that test something.** The scaffold includes at least one test file with at least
   one test that exercises real code. `test('placeholder', () => {})` is a failure.
4. **README that communicates.** Read `references/readme-rules.md` for the README structure.
   The first sentence describes what the project does — not what it is.
5. **CI that passes.** The GitHub Actions workflow references only tools and scripts that
   exist in the project. Test this mentally: would `npm ci && npm test` succeed?
6. **gitignore that fits.** Language-appropriate, project-specific. Not a 200-line dump from
   gitignore.io. 15-25 lines maximum.

### Phase 3: Verify

Before delivering, run through this checklist:

- [ ] Can you run the install command and it succeeds? (e.g., `npm install`)
- [ ] Can you run the test command and it passes? (e.g., `npm test`)
- [ ] Can you run the build command and it produces output? (e.g., `npm run build`)
- [ ] Does the CI workflow reference only scripts/tools defined in the project?
- [ ] Does the README have: what it does, how to install, how to use, how to develop?
- [ ] Is every file justified? Could you explain why each file exists?
- [ ] Is the `.gitignore` specific to this project?

If the tooling is available, actually run the install/test/build commands to verify.

### Phase 4: Deliver

Create all files in the output directory. Inform the user that the project is ready to push.
If appropriate, generate a push script.

---

## Anti-Patterns

These are the mistakes that make a repo look amateur:

| Anti-pattern | Why it's bad | What to do instead |
|-------------|-------------|-------------------|
| Config file sprawl | `.eslintrc` + `.prettierrc` + `.editorconfig` + `.huskyrc` for a small project | Pick the minimum config for the project scale |
| Badge wall | 15 shields.io badges at the top of README | 0-2 badges. Build status and version if published. |
| Emoji section headers | 🚀 Getting Started 📦 Installation | Plain text headers. This is an engineering repo. |
| Framework boilerplate | Default CRA/Next.js scaffold with nothing removed | Clean up the scaffold. Remove what you won't use. |
| README filler | "This project was created because I wanted to learn..." | State the problem the project solves. |
| Premature abstraction | `src/core/domain/services/interfaces/` for 3 files | Flat until you need nesting. Add structure when earned. |

---

## Reference Files

- **`references/project-templates.md`** — Exact directory structures and file contents for
  each project type. Read during Phase 2.
- **`references/ci-templates.md`** — GitHub Actions workflow templates for TypeScript, Python,
  and multi-language projects. Read during Phase 2.
