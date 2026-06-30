---
name: repo-readme-gen
description: >
  Generate professional, recruiter-friendly README.md files for any project repository.
  Produces READMEs that communicate clearly in 10 seconds — what the project does, how to
  use it, and why it exists. The output is a complete, immediately committable README.md
  with no TODOs or placeholders. Use this skill whenever someone wants to write, improve,
  or rewrite a README. Also trigger when users mention 'write a README,' 'improve my README,'
  'this repo needs documentation,' 'make my README better,' 'document this project,'
  'make this repo presentable,' 'help me write project documentation.' This skill adapts
  the README structure to the project type (library, app, CLI, educational) and produces
  a file ready to commit and push.
---

# Repo README Generator

A README is the front door. Most people decide whether to care in 10 seconds. Your job is
to write READMEs that pass that test — clear, specific, and professional without bloat.

The output is a **complete README.md file** — no placeholders, no TODOs, no "[insert here]."
Immediately committable.

## The 10-Second Test

In 10 seconds, the reader must know:
1. **What** this project does (one sentence)
2. **Why** it exists (one sentence — what problem or gap)
3. **Whether** it's relevant to them (implied by the above)

If the reader has to scroll to understand what the project is, the README fails.

---

## The Process

### Phase 1: Understand the Project

Read the codebase (or ask the user) and identify:
- **What it does** — the core functionality in one sentence
- **Who uses it** — library consumers, end users, developers, teams
- **Project type** — library, CLI, web app, API, educational repo
- **Maturity** — early prototype, working MVP, production-ready, published package

### Phase 2: Choose the Template

Read `references/readme-templates.md` for exact templates by project type.

| Project type | Template | Key sections |
|-------------|----------|-------------|
| Library/Package | `library` | Install → Quick Start → API → Development |
| CLI Tool | `cli` | Install → Usage → Commands → Development |
| Web App | `app` | Features → Getting Started → Project Structure → Development |
| API/Backend | `api` | Endpoints → Getting Started → Configuration → Development |
| Educational | `educational` | What You'll Learn → Prerequisites → Table of Contents |

### Phase 3: Write the README

**The first sentence is everything.** Spend more time on this than any other line.

"A lightweight TypeScript library for keyframe interpolation with configurable easing
functions" beats "This project is about animations."

**Rules:**
1. **First sentence = what it does.** Not what it is. Not why it exists. What it does.
2. **Quick Start = copy-pasteable.** The reader should be able to run the example without
   reading anything else.
3. **No badge walls.** 0-2 badges max. Build status and version if published. That's it.
4. **No emoji headers.** Engineering repos use plain text headers.
5. **No motivational filler.** "I built this to learn X" doesn't help the reader.
   If motivation matters, state the problem: "Existing tools don't support Y."
6. **Development section is mandatory.** Clone, install, test, build. Four commands.
   Even for personal projects. This signals engineering discipline.
7. **API docs are mandatory for libraries.** Document every public function.
   For each: what it does, parameters, return value, one example.
8. **Real code only.** If the Quick Start example doesn't work when pasted, it's worse
   than no example.

### Phase 4: Deliver

Output the complete README.md. If improving an existing README, briefly note what changed
and why (in the conversation, not in the file).

---

## Anti-Patterns

| What NOT to do | Do this instead |
|----------------|----------------|
| "A comprehensive framework for..." | "[Does specific thing] in [language]" |
| 15 shields.io badges | 0-2 badges or none |
| 🚀 📦 ✨ emoji headers | Plain text headers |
| "Table of Contents" for a 50-line README | TOC only for 200+ line READMEs |
| Installation instructions for 3 package managers | Primary package manager only |
| "Contributing: PRs welcome!" with no guidelines | Either write real guidelines or skip the section |
| Screenshots that are 6 months old | Current screenshots or none |

---

## Reference Files

- **`references/readme-templates.md`** — Exact templates for each project type. Read during Phase 2.
