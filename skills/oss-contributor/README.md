# Open Source Contributor

A Claude skill that guides strategic open-source contributions — finding the right projects, identifying specific contribution opportunities, preparing PRs, and building a visible contribution history. Not a generic guide — it produces actionable plans targeting specific repos and issues.

## What It Does

**Mode 1 — Find Projects:** Evaluates open-source projects for contribution-friendliness, relevance to your profile, and recruiter visibility. Produces a `CONTRIBUTION_PLAN.md` with specific issues to target.

**Mode 2 — Prepare a PR:** For a specific project, helps identify the opportunity, plan the approach, write the code, and prepare the PR description with the proper template.

## How to Trigger

- "Help me contribute to open source"
- "Find projects to contribute to"
- "Help me contribute to Lottie-web"
- "Prepare a PR for [project]"
- "Review my PR before I submit"

## Files

```
oss-contributor/
├── SKILL.md                          # Main skill instructions
├── README.md                         # This file
└── references/
    └── contribution-playbook.md      # Timeline, target projects by domain, communication templates
```

## Installation

Copy the `oss-contributor` folder into `~/.claude/skills/`.
