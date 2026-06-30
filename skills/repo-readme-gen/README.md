# Repo README Generator

A Claude skill that produces professional, recruiter-friendly README.md files for any project repository. The output passes the 10-second test — what the project does, how to use it, and why it exists — immediately clear.

## What It Does

Analyzes a project (codebase, description, or context), selects the right template for the project type, and produces a complete README.md with no placeholders. Immediately committable.

## How to Trigger

- "Write a README for this project"
- "Improve my README"
- "Make this repo presentable"
- "Document this project"

## Files

```
repo-readme-gen/
├── SKILL.md                          # Main skill instructions
├── README.md                         # This file
└── references/
    └── readme-templates.md           # Templates for library, CLI, app, API, educational
```

## Installation

Copy the `repo-readme-gen` folder into `~/.claude/skills/`.
