# Codebase Mapper

A Claude skill that maps the architecture of any codebase and produces publishable architecture documentation with Mermaid diagrams, component breakdowns, data-flow traces, and design-decision analysis.

## What It Does

Point it at a codebase — local, uploaded, or open-source — and it produces a directory of interconnected Markdown files that document the architecture. Push it to GitHub as a standalone repo or add it to `/docs`.

## Output

```
architecture-[project-name]/
  README.md              ← overview + how to read this repo
  01-high-level.md       ← system overview with architecture diagram
  02-components.md       ← each component's responsibility, API, patterns
  03-data-flow.md        ← end-to-end traces of key user flows
  04-design-decisions.md ← why the code is shaped this way, tradeoffs
  05-what-id-change.md   ← engineering opinion on improvements
  diagrams/
    architecture.mmd
    data-flow.mmd
    dependencies.mmd
```

## How to Trigger

- "Map this codebase"
- "Architecture of this repo"
- "How is this project structured"
- "Create an architecture deep dive of [project]"

## Files

```
codebase-mapper/
├── SKILL.md                          # Main skill instructions
├── README.md                         # This file
└── references/
    ├── output-templates.md           # Markdown templates for each output file
    └── diagram-patterns.md           # Mermaid syntax, diagram type selection
```

## Installation

Copy the `codebase-mapper` folder into `~/.claude/skills/`.
