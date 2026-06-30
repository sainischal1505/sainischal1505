---
name: codebase-to-course
description: >
  Transform any codebase or technical domain into structured educational content — 
  Build-Your-Own tutorials, deep-dive articles, or learning paths — published as GitHub
  repos or Markdown articles. The output is a directory of well-structured Markdown files
  with code examples, Mermaid diagrams, and progressive build steps that teach how
  something works by building a simpler version of it. Use this skill whenever someone
  wants to create educational content from code, a domain, or their professional experience.
  Also trigger when users mention 'turn this into a tutorial,' 'create a learning guide,'
  'write a walkthrough,' 'explain this as a course,' 'make educational content,' 'I want
  to teach people how X works,' 'create a technical blog post,' 'break this down for
  beginners,' 'build a learning path,' 'write a deep dive article,' 'turn my knowledge
  into content,' 'Build-Your-Own tutorial.' This skill produces publishable content that
  positions the author as someone who deeply understands a domain.
---

# Codebase-to-Course

Turn engineering knowledge into published educational content. The output is either a
**Build-Your-Own tutorial repo** (strongest for GitHub) or a **deep-dive article**
(strongest for blogs/sharing) — each with code examples, diagrams, and progressive
complexity.

The content should be specific enough to be useful and opinionated enough to be interesting.
Generic "what is X" content is worthless. "How X actually works under the hood, and what I
learned building one" is what gets bookmarked, starred, and shared.

## Who Writes This

The user is likely a working engineer with domain knowledge from their job — animation
runtimes, media pipelines, creative tools, distributed systems, etc. They haven't published
this knowledge yet. Your job is to extract it and shape it into content that other engineers
would find genuinely valuable.

**The content must reflect the author's actual expertise.** If they built animation engines
at Adobe, the tutorial should contain insights that only come from building — not textbook
explanations anyone can Google. The value is in what they learned by doing.

## Who Reads This

Engineers who:
- Use a technology but don't understand its internals
- Want to learn a domain by building, not by reading documentation
- Are searching for "how does X actually work" and want more than a surface explanation
- Are preparing for system design interviews and want to study real architectures

## Content Types

### Type 1: Build-Your-Own Tutorial (strongest for GitHub)

**Format:** A repo where the reader builds a simplified version of a real system step by step.

**Example titles:**
- "Build a Mini Animation Engine from Scratch"
- "Build Your Own Media Upload Pipeline"
- "Build a Tiny Presentation Runtime in 500 Lines"

**Output structure:**
```
build-your-own-[thing]/
  README.md                  ← Full tutorial text (the reader reads this)
  src/
    step-01-foundation/      ← Minimal working version
      [code files]
      README.md              ← What this step teaches
    step-02-[feature]/       ← Add first feature
      [code files]
      README.md
    step-03-[feature]/       ← Add second feature
      [code files]
      README.md
    final/                   ← Complete implementation
      [code files]
  diagrams/                  ← Mermaid source files
  LICENSE
```

**Each step must:**
- Introduce exactly one concept
- Result in code that compiles and runs
- Include a "what we just learned" summary
- Include a diagram if the concept has structure (data flow, state transitions, architecture)

### Type 2: Deep-Dive Article (strongest for blogs/sharing)

**Format:** A single Markdown file, 2000-4000 words, publishable on dev.to, Medium, or as
a GitHub repo README.

**Example titles:**
- "How Animation Engines Actually Work (And What I Learned Building One)"
- "The Anatomy of a Media Pipeline: From Upload to Render"
- "Inside Presentation Runtimes: Choreography, Sequencing, and State"

**Output structure:**
```
deep-dive-[topic]/
  README.md                  ← The article
  diagrams/                  ← Mermaid source files
  code/                      ← Runnable code examples referenced in the article
  LICENSE
```

### Type 3: Learning Path

**Format:** A roadmap document for engineers entering a new domain.

**Output:** Single comprehensive Markdown file with: prerequisites → foundational concepts →
intermediate patterns → advanced topics → projects to build → resources.

---

## The Process

### Phase 1: Extract Knowledge

If the user is drawing from their own experience, ask:
- What's the domain? (animation engines, media pipelines, etc.)
- What's the one thing you wish you knew before starting?
- What's the most common misconception about this domain?

If they point at a codebase, analyze it using the codebase-mapper methodology first (trace
entry points, identify components, map data flows), then identify the teachable concepts.

**Decide the content type** based on context:
- User says "tutorial" or "teach how to build" → Build-Your-Own
- User says "article" or "explain" or "deep dive" → Deep-Dive Article
- User says "learning path" or "roadmap" → Learning Path
- Ambiguous → default to Build-Your-Own (strongest for GitHub)

### Phase 2: Design the Arc

**Build-Your-Own tutorials** follow this arc:
1. **The simplest thing that works** — demonstrate the core concept in < 50 lines
2. **The first complication** — what happens when you add a real-world requirement
3. **The clever part** — the non-obvious technique that makes it work well
4. **The complete version** — a working mini-implementation with tests

**Deep-dive articles** follow this arc:
1. **The hook** — a concrete scenario the reader recognizes ("You click play and the animation
   starts. But what actually happens between the click and the first frame?")
2. **The mental model** — the key abstraction the reader needs
3. **The mechanism** — how it works, with code and diagrams
4. **The hard part** — what makes this problem non-trivial
5. **The insight** — what you learned that isn't obvious from the outside

**Do NOT present the outline for approval. Build it.**

### Phase 3: Write

Read `references/content-rules.md` for writing standards.

**Writing principles:**
- **Code examples must actually work.** If they can't be run, label them as pseudocode.
- **Every diagram earns its place.** A diagram that restates the preceding paragraph is waste.
  A diagram that shows a relationship the text can't convey is essential.
- **The hard parts are why people are reading.** Don't skip them or hand-wave them. If
  keyframe interpolation is complicated, show why it's complicated and how to handle it.
- **One insight per section.** Each section should leave the reader knowing one thing they
  didn't know before. If a section doesn't do this, cut it.
- **No filler.** "In this section, we will learn about..." is filler. Start with the content.

**Mandatory elements (every piece of educational content includes ALL of these):**

1. **At least 2 Mermaid diagrams** — architecture, data flow, or state diagrams
2. **At least 3 code examples** — real, runnable, commented
3. **At least 1 "what I wish I knew" insight** — something from experience, not textbooks
4. **A "further reading" section** — links to related projects, papers, or implementations

### Phase 4: Quality Check

Before delivering:
- [ ] The title would make someone click on Hacker News or dev.to
- [ ] The first paragraph hooks the reader with a concrete scenario
- [ ] Code examples actually work if copy-pasted
- [ ] Every section teaches something that isn't on the first page of Google results
- [ ] Diagrams show relationships the text alone can't convey
- [ ] The content reflects domain expertise, not just documentation rewriting
- [ ] Someone could follow this end-to-end without getting lost

---

## Reference Files

- **`references/content-rules.md`** — Writing standards, code example formatting, diagram
  guidelines, anti-patterns. Read during Phase 3.
