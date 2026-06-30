---
name: codebase-mapper
description: >
  Map the architecture of any codebase — local, uploaded, or open-source — and produce a
  publishable architecture deep-dive as a standalone directory with Mermaid diagrams,
  component breakdowns, data-flow traces, and design-decision analysis. Use this skill
  whenever someone wants to understand, analyze, document, or reverse-engineer the structure
  of a codebase or project. Also trigger when users mention 'map this codebase,' 'architecture
  of this repo,' 'how is this project structured,' 'break down this codebase,' 'explain this
  repo internals,' 'reverse engineer this project,' 'document the architecture,' 'create an
  architecture deep dive,' 'what are the key modules,' 'how do the components connect,' or
  'draw me the architecture.' This skill produces a directory of Markdown files with Mermaid
  diagrams that can be pushed directly to GitHub as a standalone repository or added to an
  existing repo's /docs directory.
---

# Codebase Architecture Mapper

Produce architecture documentation good enough to publish as a standalone GitHub repo. The
output is a **directory** containing interconnected Markdown files with embedded Mermaid
diagrams — push it to GitHub and it renders beautifully with zero tooling.

The goal is not to summarize files. It's to reconstruct the **mental model** the original
architects had, then present it clearly enough that someone who has never seen the codebase
can hold that model and make decisions with it.

## Who This Is For

The reader of your output is an engineer who:
- Is joining a team and needs to onboard onto this codebase fast
- Is evaluating this open-source project before using or contributing to it
- Is preparing for system design interviews by studying real architectures
- Wants to publish architecture analysis as a GitHub repo to demonstrate senior-level thinking

**The author** (the user running this skill) is building their GitHub presence. A repo called
`architecture-deep-dive-lottie-web` with clean diagrams and opinionated analysis makes a
recruiter think "this person thinks in systems, not just code."

## Output Structure

Every architecture map produces this directory:

```
architecture-[project-name]/
  README.md              ← overview + how to read this repo
  01-high-level.md       ← system overview with architecture diagram
  02-components.md       ← each component's responsibility, API, patterns
  03-data-flow.md        ← end-to-end traces of key user flows
  04-design-decisions.md ← why the code is shaped this way, tradeoffs
  05-what-id-change.md   ← the author's engineering opinion
  diagrams/
    architecture.mmd     ← high-level Mermaid source
    data-flow.mmd        ← sequence/flow Mermaid source
    dependencies.mmd     ← module dependency graph
```

The `diagrams/` directory holds raw `.mmd` files so readers can modify them. The same
diagrams are embedded inline in the Markdown files using fenced Mermaid blocks.

---

## The Process

### Phase 1: Reconnaissance

Before going deep, build a fast mental model of the codebase's shape. Spend the first
pass understanding *what* this is, not *how* it works.

**Extract in this order:**
1. **Entry points** — `main`, `index`, `app`, `server`, `cli` files. What starts the system?
2. **Package manifest** — `package.json`, `pyproject.toml`, `Cargo.toml`, `go.mod`. What are
   the dependencies? What do the scripts/tasks do?
3. **Directory structure** — `ls` the top level and one level deep. How is the code organized?
4. **README** — What does the project claim its architecture is?
5. **Types/interfaces** — Read type definitions first. They reveal the data shapes faster
   than reading implementation.
6. **Test structure** — `tests/` or `__tests__/` layout mirrors the code architecture.

After this pass, write one sentence: "This is a [type] project using [architecture pattern]
with [N] major components, built on [framework/runtime]."

If you cannot write that sentence yet, you haven't understood enough. Read more before
proceeding.

### Phase 2: Deep Mapping

For each component/module identified in Phase 1, extract:

| Question | Why it matters |
|----------|---------------|
| What does it do? (one sentence) | Forces precision — if you can't say it in one sentence, you don't understand it yet |
| What does it expose to other modules? | Defines the contract — this is what other code depends on |
| What does it depend on? | Reveals coupling — tightly coupled modules are design decisions worth discussing |
| What pattern does it use? | Names the pattern (state machine, pipeline, observer, pub-sub, middleware chain) |
| What data comes in, transforms, goes out? | The data flow is the real architecture — code structure is just how it's organized |

**Build a dependency graph.** Identify:
- **The core** — what everything depends on. This is the most important code.
- **The boundary** — where the system talks to the outside world (APIs, databases, filesystem, network).
- **The periphery** — what could be removed without breaking the core. These are extensions.

### Phase 3: Trace Key Flows

Pick 2-3 flows that represent the most important things the system does. For each flow, trace
the exact path through the code:

```
User action → Entry point → [Module A: does X] → [Module B: does Y] → [Module C: does Z] → Result
```

These flows become the sequence diagrams in `03-data-flow.md`. They are the most valuable
part of the architecture doc because they answer the question every new developer asks:
"What happens when...?"

**Choose flows that cover the most code.** A good set of 2-3 flows should touch 80%+ of the
codebase. If a module isn't part of any traced flow, it's either peripheral or you missed
something important.

### Phase 4: Analyze Design Decisions

For each major architectural choice, identify:

- **The decision** — what was chosen (e.g., "event-driven architecture", "single-threaded
  rendering loop", "document model with version upgraders")
- **The context** — what constraints or goals drove this choice
- **The tradeoff** — what was gained and what was sacrificed
- **The alternative** — what else could have been done (this shows you understand the design
  space, not just the implementation)

Don't speculate. If the decision rationale is visible in the code (comments, ADRs, git
history, README), cite it. If not, state the most likely rationale based on the constraints
you can observe, and flag it as inference.

### Phase 5: Write the Architecture Doc

Read `references/output-templates.md` for the exact Markdown templates for each file.

**Writing rules:**
- **Diagrams first, prose second.** Every section opens with a diagram, then explains it.
  If you can't diagram it, it might not belong in an architecture doc.
- **One sentence per component.** The component description table uses exactly one sentence
  per component in the "Responsibility" column. If you need two sentences, you don't
  understand it well enough.
- **Name the patterns.** Don't describe a pub-sub system in five paragraphs. Say "pub-sub"
  and link to how this implementation differs from textbook pub-sub.
- **Real file paths.** Every component reference includes the actual file path. The reader
  should be able to `cmd+click` and find the code.
- **"What I'd Change" is mandatory.** The last file (`05-what-id-change.md`) contains the
  author's engineering opinion. This is what makes the doc more than documentation — it shows
  critical thinking. A recruiter reads this section to evaluate engineering judgment.

**Mandatory diagram types (every architecture map includes ALL of these):**

1. **High-level architecture diagram** (Mermaid flowchart) — boxes for major components,
   arrows for communication. Read `references/diagram-patterns.md` for Mermaid conventions.
2. **Data flow sequence diagram** (Mermaid sequence) — at least one key user flow traced
   end-to-end through the system.
3. **Dependency graph** (Mermaid flowchart) — which modules depend on which. Arrows point
   from dependent to dependency.

**Do NOT present the analysis for approval — just build it.** The user wants architecture
docs, not a planning document. Analyze internally, then go straight to writing the files.

### Phase 6: Review

After writing all files, do a self-check:

- [ ] Someone unfamiliar with the codebase can understand the architecture from these docs alone
- [ ] Every component is mentioned in at least one diagram AND one prose section
- [ ] All file paths referenced actually exist in the codebase
- [ ] The "What I'd Change" section has at least 3 concrete suggestions with reasoning
- [ ] Diagrams render correctly (valid Mermaid syntax)
- [ ] The README explains what this repo is and how to read it

---

## Reference Files

Read these during the indicated phases — not upfront.

- **`references/output-templates.md`** — Exact Markdown templates for every output file.
  Read during Phase 5.
- **`references/diagram-patterns.md`** — Mermaid syntax conventions, diagram type selection
  guide, styling rules. Read during Phase 5 when writing diagrams.
