# Contribution Playbook

## Strategic Timeline

### Month 1: Establish Presence (2-3 PRs)

**Goal:** Get PRs merged. Build confidence. Learn the workflow.

**Target contributions:**
- Fix documentation that doesn't match actual behavior (Tier 1)
- Fix a bug with an existing failing test or clear reproduction (Tier 2)
- Add a missing test for untested functionality (Tier 3)

**Process for each:**
1. Fork the repo
2. Create a branch named after the issue: `fix/issue-123-description`
3. Make the change. Keep it minimal.
4. Run all tests. They must pass.
5. Write a clear PR description (use the template from SKILL.md)
6. Submit and respond to feedback within 24 hours

### Month 2-3: Build Depth (2-3 PRs)

**Goal:** Show you understand the codebase. Tackle harder issues.

**Target contributions:**
- Small feature from the project's roadmap or feature requests (Tier 4)
- Improvement to error handling, validation, or reliability (Tier 3)
- Performance improvement with benchmarks (Tier 3-4)

### Month 4-6: Establish Authority (1-2 significant PRs)

**Goal:** Show you can own a subsystem. Build relationship with maintainers.

**Target contributions:**
- Significant feature discussed and agreed upon with maintainers (Tier 5)
- Refactoring of a subsystem with maintainer buy-in (Tier 5)
- Comprehensive documentation overhaul (Tier 4-5)

---

## Target Projects by Domain

### Creative Tools / Animation (for Nischal's profile)

| Project | Stars | Language | Why relevant | Contribution-friendly? |
|---------|-------|----------|-------------|----------------------|
| **Lottie-web** | 30k+ | JS | Animation rendering — directly maps to Adobe animation work | Medium — active, but large codebase |
| **Fabric.js** | 27k+ | JS/TS | Canvas editing — creative tools domain | Good — active, labeled issues |
| **PixiJS** | 43k+ | TS | 2D rendering engine — creative tools | Good — active community |
| **Remotion** | 20k+ | TS/React | React video creation — media + React | Excellent — very active, welcoming |
| **Motion** | 23k+ | TS | Animation library (ex-framer-motion) | Good — active, TS-native |
| **Sharp** | 29k+ | JS/C++ | Image processing — media pipelines | Medium — C++ core is complex |

### Frontend / React

| Project | Stars | Why relevant |
|---------|-------|-------------|
| **Radix UI** | 16k+ | Accessible component primitives |
| **TanStack Query** | 41k+ | Data fetching patterns |
| **Zustand** | 46k+ | State management |

### Developer Tools

| Project | Stars | Why relevant |
|---------|-------|-------------|
| **Vitest** | 13k+ | Testing framework — contribution shows testing depth |
| **Biome** | 14k+ | Linting/formatting — tooling knowledge |

---

## Communication Templates

### Claiming an Issue

```
Hi! I'd like to work on this. I've read the codebase and here's my planned approach:

[2-3 sentences describing what you'll change and why]

I can have a PR ready by [reasonable date — usually 1-2 weeks].

Let me know if this approach sounds right or if you'd suggest a different direction.
```

### Opening an Issue for a Contribution

```
## Problem

[One sentence: what's wrong or missing]

## Proposed Solution

[2-3 sentences: what you'd like to do]

## Alternatives Considered

[1-2 sentences: what else you thought about and why the proposed solution is better]

I'm happy to implement this if the approach sounds good. Let me know!
```

### Responding to Review Feedback

```
Thanks for the review! [Address each comment specifically]

- [Comment 1]: Done — changed X to Y as suggested.
- [Comment 2]: Good point. I've refactored this to [approach].
- [Comment 3]: Could you clarify what you mean? I interpreted it as [interpretation]
  but want to make sure I understand correctly.

Updated the PR with the changes.
```

---

## What NOT to Do

- **Don't submit a PR without reading CONTRIBUTING.md** — you'll get rejected on process.
- **Don't combine multiple unrelated changes** — one PR = one issue = one review.
- **Don't go silent after feedback** — respond within 24-48 hours or maintainers move on.
- **Don't argue with maintainers about style** — it's their project, follow their conventions.
- **Don't fork without contributing** — forks without PRs clutter your profile with no signal.
