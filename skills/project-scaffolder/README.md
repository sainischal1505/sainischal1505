# Project Scaffolder

A Claude skill that creates professional-grade project repositories — complete with working tests, CI/CD, and documentation — ready to push to GitHub immediately.

## What It Does

Tell it what you're building and it produces a complete project directory where every file has real content, tests actually run, and CI actually passes. No placeholders, no TODOs.

## Output

A complete project directory matching the project type:

```
[project-name]/
├── src/                  # Source code with real implementation
├── tests/                # Tests that actually test something
├── .github/workflows/    # CI that actually passes
├── package.json          # (or pyproject.toml) with correct config
├── tsconfig.json         # (if TypeScript)
├── .gitignore            # Project-specific, not a 200-line dump
├── LICENSE
└── README.md             # Passes the 10-second recruiter test
```

## How to Trigger

- "Scaffold a new TypeScript library"
- "Set up a new repo for [project]"
- "Create a project structure for a CLI tool"
- "Make this repo production-ready"

## Files

```
project-scaffolder/
├── SKILL.md                          # Main skill instructions
├── README.md                         # This file
└── references/
    ├── project-templates.md          # Directory structures for each project type
    └── ci-templates.md               # GitHub Actions workflow templates
```

## Installation

Copy the `project-scaffolder` folder into `~/.claude/skills/`.
