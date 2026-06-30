# Output Templates

Use these templates exactly. Customize content, not structure.

## README.md

```markdown
# Architecture Deep Dive: [Project Name]

An architecture analysis of [[project-name](link)] — what it does, how the pieces
fit together, and the key design decisions that shape the codebase.

## What is [Project Name]?

[2-3 sentences: what the project does, who uses it, why it exists.]

## How to read this

| File | What you'll learn |
|------|------------------|
| [01-high-level.md](01-high-level.md) | The big picture — major components and how they connect |
| [02-components.md](02-components.md) | Each component's job, API, and internal patterns |
| [03-data-flow.md](03-data-flow.md) | What happens when you [key user action] — traced through the code |
| [04-design-decisions.md](04-design-decisions.md) | Why the code is shaped this way |
| [05-what-id-change.md](05-what-id-change.md) | What I'd do differently (and why) |

## Tech stack

[Table: technology → what it's used for in this project. Only list what's actually used.]

## Quick stats

- **Language**: [primary language]
- **Size**: ~[N] files, ~[N]k lines
- **Architecture**: [one-word pattern: monolith, microservices, event-driven, etc.]
- **Key dependency**: [the one library/framework this project couldn't exist without]
```

## 01-high-level.md

```markdown
# High-Level Architecture

## Overview

[One paragraph: the system's architecture in plain language. State the pattern name.]

## Architecture Diagram

[Mermaid flowchart: major components as boxes, arrows showing communication direction.
Label arrows with what flows between components (HTTP, events, function calls, etc.)]

## Components at a Glance

| Component | Responsibility | Key file(s) |
|-----------|---------------|-------------|
| [Name] | [One sentence] | `src/[path]` |

## How They Connect

[2-3 paragraphs explaining the communication patterns between components.
Which connections are synchronous vs async? What protocol/mechanism?
Where is the coupling tight vs loose?]
```

## 02-components.md

```markdown
# Component Breakdown

## [Component Name]

**Responsibility:** [One sentence]
**Key files:** `src/[path]`
**Pattern:** [Name the design pattern: state machine, pipeline, observer, etc.]
**Exposes:** [What other modules consume from this component]
**Depends on:** [What this component needs from others]

### How it works

[3-5 sentences. Focus on the mechanism, not the implementation details.
What data comes in? What happens to it? What comes out?]

### Notable implementation detail

[One specific thing about the implementation worth knowing — a clever
optimization, an unusual choice, a known limitation. Include the file:line.]

[Repeat for each major component]
```

## 03-data-flow.md

```markdown
# Data Flow

## Flow 1: [User Action → Result]

**Trigger:** [What the user does]
**Result:** [What happens]

### Sequence

[Mermaid sequence diagram showing the full flow]

### Step-by-step

1. **[Step name]** — `[file:function]` — [What happens and why]
2. **[Step name]** — `[file:function]` — [What happens and why]
...

### What could go wrong

[1-2 error cases in this flow. Where does it fail? How is the failure handled?]

[Repeat for 2-3 key flows]
```

## 04-design-decisions.md

```markdown
# Design Decisions

## Decision: [What was chosen]

**Context:** [What constraint or goal drove this]
**Tradeoff:** [What was gained] at the cost of [what was sacrificed]
**Alternative:** [What else could have been done]
**Evidence:** [Where in the code you can see this decision — file path, comment, pattern]

[Repeat for each major decision. Aim for 4-6 decisions.]
```

## 05-what-id-change.md

```markdown
# What I'd Change

These are engineering opinions based on analyzing the codebase. Reasonable
people might disagree — that's fine. The point is to demonstrate engineering
judgment, not to criticize the original authors.

## 1. [Change title]

**Current state:** [What exists now]
**Problem:** [Why it's suboptimal — not "it's messy", but a specific consequence]
**Proposed change:** [What you'd do instead]
**Why this is better:** [What improves — testability, performance, readability, etc.]
**Cost:** [What it would take to make this change — trivial, medium, major refactor]

[Repeat for 3-5 suggestions. Order by impact.]

## What I'd keep

[1-2 paragraphs on what the codebase does well. This shows balanced judgment,
not just criticism. Name specific patterns or decisions you admire.]
```
