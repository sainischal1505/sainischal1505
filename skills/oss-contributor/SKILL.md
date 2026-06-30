---
name: oss-contributor
description: >
  Guide strategic open-source contributions — find the right projects, identify specific
  contribution opportunities, prepare PRs with proper descriptions, and build a visible
  contribution history. This is not a generic "how to contribute to open source" guide —
  it produces actionable contribution plans targeting specific repos, issues, and PRs.
  Use this skill whenever someone wants to contribute to open source or build their OSS
  presence. Also trigger when users mention 'help me contribute to open source,' 'find
  projects to contribute to,' 'I want to make a PR,' 'find issues to work on,' 'contribute
  to [project],' 'get started with open source,' 'find good first issues,' 'build my open
  source presence,' 'prepare a PR for [project],' 'review my PR,' 'which open source
  projects should I target,' 'help me write a PR description.' This skill produces a
  concrete contribution plan with specific issues, repos, and PR preparation.
---

# Open Source Contributor

Help the user make strategic, meaningful open-source contributions that strengthen their
GitHub profile. Not drive-by typo fixes — real contributions that show engineering judgment
and codebase understanding.

The goal: a GitHub profile where a recruiter sees merged PRs in recognized projects,
demonstrating that the user can read unfamiliar code, identify real improvements, and
communicate effectively with maintainers.

## Two Modes

### Mode 1: "Help me find projects to contribute to"
The user wants contribution targets. Produce a **Contribution Plan** — specific projects,
specific issues, specific approach for each.

### Mode 2: "Help me contribute to [specific project]"
The user has a target. Produce a **PR Preparation** — issue identification, approach,
code changes, PR description.

---

## Mode 1: Contribution Plan

### Phase 1: Understand the User's Profile

Identify from conversation context or by asking:
- **Tech stack** — what languages and frameworks they work with daily
- **Domain** — what kind of software they build (creative tools, infra, frontend, etc.)
- **Experience level with OSS** — first contribution or experienced contributor
- **Goal** — build profile, learn, or contribute to something they use

### Phase 2: Select Target Projects

**Selection criteria (all must be true):**
- [ ] Relevant to the user's stack and domain
- [ ] Actively maintained (commits in the last 30 days)
- [ ] External PRs get merged (check recent merged PR authors — if they're all core team, avoid)
- [ ] Has labeled issues (`good-first-issue`, `help-wanted`, or equivalent)
- [ ] Maintainers respond to issues/PRs within a reasonable time (< 2 weeks)
- [ ] Would be recognized by a recruiter in the user's target industry

**Red flags (avoid):**
- No external PR merged in 6+ months
- Hundreds of stale open PRs
- Maintainer is hostile or dismissive in issues
- No license or highly restrictive license
- Massive codebase with no documentation (too hard for first contribution)

### Phase 3: Identify Specific Opportunities

For each target project, find 2-3 concrete contribution opportunities:

```markdown
### [Project Name] ([stars] stars)

**Why this project:** [One sentence relevance to user]
**Contribution readiness:** [good-first-issue count, recent external PRs merged]

**Opportunity 1:** [Issue #N — Title]
- **Type:** Bug fix / Documentation / Feature / Test
- **Difficulty:** Low / Medium
- **Approach:** [2-3 sentences on how to tackle it]
- **Estimated effort:** [hours]

**Opportunity 2:** [Description if no issue exists]
- **Type:** [what kind of contribution]
- **Why it's needed:** [what's missing or broken]
- **Approach:** [how to do it]
```

Read `references/contribution-playbook.md` for the strategic timeline.

### Phase 4: Deliver the Plan

Output a `CONTRIBUTION_PLAN.md` with:
1. Selected projects with rationale
2. Specific opportunities per project
3. Recommended order (start with highest-acceptance-probability contribution)
4. Timeline (Month 1: docs/bugs, Month 2-3: small features, Month 4+: significant PRs)

---

## Mode 2: PR Preparation

### Phase 1: Understand the Project

- Read CONTRIBUTING.md (code style, branch naming, commit format, review process)
- Read recent merged PRs (what does a good PR look like in this project?)
- Run the test suite locally (if possible) to verify environment works

### Phase 2: Identify or Validate the Contribution

If the user has a specific issue: validate it's still open, unassigned, and worth doing.
If they want to find something: scan issues for opportunity (see Mode 1, Phase 3).

### Phase 3: Plan the Changes

Before writing code:
- Comment on the issue: "I'd like to work on this. Here's my approach: [brief plan]."
- Wait for maintainer acknowledgment (advise user to wait 24-48 hours)
- If no issue exists, open one first and describe what you want to do

### Phase 4: Prepare the PR

**PR description template:**

```markdown
## What

[One sentence: what this PR does]

## Why

[One sentence: what problem it solves]
Closes #[issue number]

## How

[Brief description of the approach. 2-4 sentences.]
[If there were alternative approaches, briefly note why you chose this one.]

## Testing

- [What tests were added or modified]
- [How to verify the change manually]

## Checklist

- [ ] Tests pass locally
- [ ] Code follows project conventions
- [ ] Documentation updated (if applicable)
- [ ] Commits are clean (squashed if needed)
```

**Pre-submission checklist:**
- [ ] PR touches only the relevant files (no unrelated changes)
- [ ] Tests pass
- [ ] Code follows the project's existing style exactly
- [ ] Commit message follows project convention
- [ ] PR description clearly explains what and why
- [ ] Issue is referenced

---

## Contribution Tiers

| Tier | Type | Signal to recruiters | Acceptance rate |
|------|------|---------------------|----------------|
| 1 | Fix incorrect docs | "Reads code carefully" | Very high |
| 2 | Bug fix with test | "Debugs and tests" | High |
| 3 | Add missing tests | "Cares about quality" | High |
| 4 | Small feature from roadmap | "Understands codebase" | Medium |
| 5 | Significant feature | "Can own a subsystem" | Lower, but very high signal |

Start at Tier 1-2. Move to Tier 3-4 after building rapport. Tier 5 only after established
trust with maintainers.

---

## Reference Files

- **`references/contribution-playbook.md`** — Month-by-month timeline, target project
  database for different domains, and communication templates. Read during Phase 3/4.
