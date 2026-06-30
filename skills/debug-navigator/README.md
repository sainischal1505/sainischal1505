# Debug Navigator

A Claude skill that systematically debugs issues and navigates unfamiliar codebases. Follows a reproducible methodology — reproduce, narrow, identify, fix, prevent — and teaches the process as it solves the problem.

## What It Does

**Mode A — Debugging:** Traces execution paths, identifies root causes, produces fixes with preventive tests. Uses binary search, stack trace analysis, diff-based, and state inspection strategies.

**Mode B — Navigation:** Reads unfamiliar codebases systematically — discovers entry points, traces features through the code, maps data flows, and explains how components connect.

## Output

### Bug Analysis
```
Root Cause → Location → Fix (actual code) → Preventive Test
```

### Code Trace
```
Entry Point → Step-by-step flow → Key data structures → Non-obvious details
```

## How to Trigger

- "Debug this"
- "Why is this broken"
- "Trace this error"
- "Help me understand this code"
- "Where does X happen in the codebase"
- "I inherited this codebase"

## Files

```
debug-navigator/
├── SKILL.md                          # Main skill instructions
├── README.md                         # This file
└── references/
    └── debugging-checklist.md        # Quick-reference by error type, common patterns
```

## Installation

Copy the `debug-navigator` folder into `~/.claude/skills/`.
