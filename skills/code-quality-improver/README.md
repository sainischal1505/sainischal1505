# Code Quality Improver

A Claude skill that analyzes codebases for quality issues and produces actionable improvements — prioritized fixes with actual code, reliability patterns, and complete test suites. Every suggestion comes with the implementation, not just the diagnosis.

## What It Does

Reviews code like a senior engineer reviews a PR. Produces a structured quality report with severity-ranked issues, each containing the problematic code, the fix, and the reasoning. Writes complete test files when testing gaps are found.

## Output

- **Small scope** (single file): Issues + fixes inline
- **Medium scope** (a module): `QUALITY_REPORT.md` with all issues and fixes
- **Large scope** (full codebase): `QUALITY_REPORT.md` + modified source files + new test files

## How to Trigger

- "Improve this code"
- "Review my code quality"
- "Add tests for this module"
- "Make this production-ready"
- "Find bugs in this code"

## Files

```
code-quality-improver/
├── SKILL.md                          # Main skill instructions
├── README.md                         # This file
└── references/
    └── testing-patterns.md           # Test structure, assertion guide, mocking rules
```

## Installation

Copy the `code-quality-improver` folder into `~/.claude/skills/`.
