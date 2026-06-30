---
name: codebase-mapper
description: >
  Maps the architecture of any codebase — local or open-source — and produces clean,
  publishable architecture documentation with diagrams, component breakdowns, data flow,
  and design-decision analysis. TRIGGER whenever the user says: "map this codebase",
  "architecture of this repo", "how is this project structured", "break down this codebase",
  "explain this repo's architecture", "I want to understand how X works internally",
  "document the architecture", "create an architecture deep dive", or any request to
  understand, analyze, or document the structure of a codebase or open-source project.
  Also triggers for: "reverse engineer this project", "what are the key modules",
  "how do the components connect", "draw me the architecture".
---

# Codebase Architecture Mapper

You are producing architecture documentation that is good enough to publish as a standalone
repo on GitHub. The output should demonstrate senior-level systems thinking — the kind that
impresses in system design interviews and shows recruiters the user understands how software
is built, not just how to write code.

## When to use this skill

- User wants to understand an unfamiliar codebase
- User wants to create architecture documentation for their own or an open-source project
- User wants a "deep dive" repo they can publish on GitHub
- User is preparing for system design interviews by studying real architectures

## Step 1: Identify the target

Ask one clarifying question if needed:
- Is it a local repo (path on disk)?
- Is it a GitHub URL to clone?
- Is it a well-known project the user named (e.g., "Lottie-web", "Fabric.js")?

If it's a GitHub URL and you have network access, clone it. If not, ask the user to
provide the code or key files.

## Step 2: Reconnaissance pass

Before diving deep, do a fast scan to understand the shape:

```
1. Read the top-level directory structure
2. Read package.json / setup.py / Cargo.toml / build files for dependencies
3. Read the existing README for stated architecture
4. Identify entry points (main, index, app, server files)
5. Count files by type to understand the codebase composition
6. Look for /docs, /architecture, or ADR directories
```

Produce a quick mental model: "This is a [type] project with [N] modules, built on [framework],
with [pattern] architecture."

## Step 3: Deep mapping

For each major module/component, identify:

- **Purpose**: What does it do? One sentence.
- **Public API**: What does it expose to other modules?
- **Dependencies**: What does it import/consume?
- **Key patterns**: State machine? Event-driven? Pipeline? Observer?
- **Data flow**: What comes in, what goes out, how is it transformed?

Build a dependency graph mentally. Identify:
- The core (what everything depends on)
- The periphery (what could be removed without breaking the core)
- The boundaries (where the system talks to the outside world)

## Step 4: Produce the architecture document

Create a Markdown document with this structure. Use Mermaid diagrams where they add clarity.

```markdown
# Architecture Deep Dive: [Project Name]

## Overview
[2-3 sentences: what this project is, what problem it solves, what architecture style it uses]

## High-Level Architecture
[Mermaid diagram showing major components and their relationships]

## Core Components

### [Component 1]
- **Responsibility**: [one sentence]
- **Key files**: [list]
- **Pattern**: [what design pattern it uses]
- **Depends on**: [other components]
- **Exposes**: [what API/interface it provides]

[Repeat for each major component]

## Data Flow
[Mermaid sequence diagram or flowchart showing how data moves through the system]
[Walk through 1-2 key user-facing flows end-to-end]

## Key Design Decisions
[For each major decision:]
- **Decision**: What was chosen
- **Context**: Why this matters
- **Tradeoffs**: What was gained and lost
- **Alternatives**: What else could have been done

## Dependency Map
[Mermaid diagram showing module dependencies]

## What I'd Change
[Your engineering opinion — what could be improved, simplified, or redesigned.
This section is what makes the doc more than just documentation — it shows critical thinking.]
```

## Step 5: Output format

- If the user wants a publishable repo, create the full Markdown file ready to push to GitHub
- If the user wants to understand the codebase for their own learning, keep it conversational but still structured
- Always include at least 2 Mermaid diagrams (high-level architecture + data flow)
- Keep each component description to 3-5 sentences max — density over length

## Quality checklist

Before delivering, verify:
- [ ] Someone unfamiliar with the codebase could understand the architecture from this doc alone
- [ ] Diagrams actually match the code, not just what the README claims
- [ ] Design decisions section has real engineering analysis, not surface observations
- [ ] "What I'd Change" section shows independent thinking
- [ ] The document would look strong as a standalone GitHub repo

## What makes this different from just reading code

You're not summarizing files. You're reconstructing the *mental model* the original architects
had, then presenting it clearly enough that someone else can hold that model. Focus on *why*
the code is structured this way, not just *what* each file does.
