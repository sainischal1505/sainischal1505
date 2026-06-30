---
name: code-quality-improver
description: >
  Analyze codebases for quality issues and produce actionable improvements — prioritized
  fixes, reliability patterns, test suites, and refactored code. The output is a structured
  quality report with actual code changes, not vague advice. Use this skill whenever someone
  wants code reviewed, improved, tested, or hardened. Also trigger when users mention
  'improve this code,' 'review my code,' 'add tests,' 'improve test coverage,' 'make this
  reliable,' 'refactor this,' 'find bugs,' 'improve error handling,' 'make this production-
  ready,' 'harden this code,' 'code review,' 'what is wrong with this code,' 'this needs
  better tests,' 'improve reliability.' This skill produces a prioritized analysis with
  working code — every suggestion includes the implementation, not just the diagnosis.
---

# Code Quality Improver

Review code the way a senior engineer reviews a PR — focused on correctness, reliability,
and maintainability, not style preferences. Every suggestion comes with the actual fix.
"Consider adding error handling" is worthless. Showing the error handling code is useful.

## Output Format

Every quality review produces a structured report. The report can be delivered as conversation
text or as a Markdown file — depending on scope.

**Small scope** (single file, one function): Answer inline in conversation.
**Medium scope** (a module, a feature): Produce a `QUALITY_REPORT.md` file.
**Large scope** (full codebase): Produce `QUALITY_REPORT.md` + improved files.

---

## The Process

### Phase 1: Triage

Read the code and categorize every issue you find into exactly one of these levels:

| Level | Meaning | Action |
|-------|---------|--------|
| **Critical** | Will break in production. Data loss, crashes, security holes. | Fix immediately. Show the fix. |
| **Important** | Will cause problems under load, edge cases, or maintenance. | Fix soon. Show the fix. |
| **Improvement** | Makes the code better but isn't urgent. | Suggest with rationale. Show the fix. |

**Do NOT dump a laundry list.** Identify the top 5-7 issues ranked by severity. A focused
report with 5 real fixes is worth more than 20 superficial observations.

### Phase 2: Analyze Each Issue

For each issue, produce this exact structure:

```markdown
### [Issue #N]: [Descriptive Title]

**Severity:** Critical / Important / Improvement
**Location:** `[file]:[line]` or `[file]:[function name]`
**Problem:** [One sentence — what is wrong]
**Impact:** [One sentence — what breaks or degrades because of this]

**Current code:**
```[language]
[the problematic code, minimal context]
```

**Fixed code:**
```[language]
[the fixed code, same scope]
```

**Why this fix is correct:** [1-2 sentences explaining the reasoning]
```

### Phase 3: Testing

When the user asks for tests or you identify testing gaps, produce complete test files.

Read `references/testing-patterns.md` for test structure and patterns.

**What to test (priority order):**
1. **Critical paths** — the main thing the code does
2. **Edge cases** — empty inputs, null, boundary values, max size
3. **Error paths** — what happens when dependencies fail
4. **State transitions** — if there's a state machine, test every valid transition

**Every test file must:**
- Actually run without modification
- Use the project's existing test framework (or recommend one if none exists)
- Follow Arrange-Act-Assert pattern
- Have descriptive test names that read as sentences
- Test behavior, not implementation

### Phase 4: Reliability Patterns

When improving reliability, apply these patterns with actual implementations:

**Retry with exponential backoff** — for network calls, external APIs. Show the code with
configurable max retries, backoff multiplier, and timeout.

**Circuit breaker** — for external service calls. Show the state machine: closed → open →
half-open with thresholds.

**Input validation at boundaries** — validate at the entry point (API endpoint, function
entry), not deep in the logic. Show the validation code.

**Graceful degradation** — when non-critical features fail, core still works. Identify
what's critical vs. optional and show the fallback paths.

**Timeout handling** — every external call gets a timeout. Show `Promise.race` with timeout
or equivalent pattern.

Don't apply patterns the code doesn't need. A utility function processing local data does
not need a circuit breaker. Match patterns to actual reliability risks.

### Phase 5: Deliver

- **Small scope**: Issues + fixes inline in conversation
- **Medium scope**: `QUALITY_REPORT.md` with all issues, fixes, and test suggestions
- **Large scope**: `QUALITY_REPORT.md` + modified source files + new test files

---

## Anti-Patterns in Code Review

| Bad review habit | Why it's bad | Do this instead |
|-----------------|-------------|----------------|
| "This is messy" | Not actionable | Name the specific smell and show the refactoring |
| "Consider adding tests" | Vague | Write the specific tests |
| Style nitpicks on working code | Low value, high friction | Focus on correctness and reliability |
| Rewriting code to your preference | Disrespectful, often unnecessary | Only refactor if there's a concrete quality benefit |
| "This could be a one-liner" | Clever ≠ better | Prioritize readability |

---

## Reference Files

- **`references/testing-patterns.md`** — Test structure templates, assertion patterns,
  and examples for TypeScript and Python. Read during Phase 3.
