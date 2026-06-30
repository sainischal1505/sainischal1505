# Content Rules

## Writing Standards

### The Hook (first 3 sentences)

Every piece opens with a concrete scenario, not a definition. The reader should recognize
something from their own experience.

**Good:** "You click play and the presentation animates. Each object fades, slides, and
transforms in sequence. But how does the runtime know what to do when?"

**Bad:** "Animation engines are software systems that manage the rendering of visual
transformations over time."

### Code Examples

- Every code block has a language tag for syntax highlighting
- Every code block has a comment explaining the non-obvious line
- Keep examples under 30 lines. If longer, split into steps with prose between them
- Use consistent naming: if you call a variable `timeline` in one example, don't rename it
  to `sequence` in the next
- Show the output. After a code block, show what it produces (console output, visual result,
  state change)

```typescript
// Good: focused, commented, shows result
function interpolate(start: number, end: number, t: number): number {
  // t is 0-1, representing progress through the animation
  return start + (end - start) * t;
}

interpolate(0, 100, 0.5); // → 50 (halfway between 0 and 100)
```

### Diagrams

Use Mermaid. Every diagram must:
- Have a title (comment above the diagram)
- Label every arrow
- Use consistent names (same component = same label everywhere)
- Show max 8 nodes. More → split into multiple diagrams.

**When to use which diagram:**
| What you're showing | Diagram type |
|---------------------|-------------|
| Components and connections | `graph TD` or `graph LR` |
| A request flowing through a system | `sequenceDiagram` |
| States and transitions | `stateDiagram-v2` |

### Section Length

- Max 4 paragraphs per section before a code block, diagram, or subheading breaks it up
- Max 3 sentences per paragraph in tutorial content
- If you're writing a fourth paragraph without a visual break, you need a code block or diagram

### Technical Terms

First use of any technical term gets a plain-English definition inline. Not as a glossary —
as part of the sentence.

**Good:** "The runtime uses a **timeline** — an ordered list of animation steps with
timestamps — to know when each effect should fire."

**Bad:** "The runtime uses a timeline to orchestrate effects. (See glossary for definition.)"

## Anti-Patterns

| Anti-pattern | Why it's bad | What to do |
|-------------|-------------|-----------|
| Opening with a definition | Boring, Google-able | Open with a scenario |
| "In this section we will learn..." | Filler | Start with the content |
| Pseudocode instead of real code | Untestable, vague | Use real code. If simplified, say so. |
| Covering everything | Diluted, unfocused | Cover 3-5 things deeply, not 10 shallowly |
| No opinion | Reads like documentation | State what you learned, what surprised you, what you'd do differently |
| Wall of text | Readers bounce | Break every 2-3 paragraphs with code, diagram, or subheading |

## The "Insight Test"

Before publishing, read each section and ask: "Could someone learn this from the official
documentation in 5 minutes?" If yes, the section doesn't add value. Either cut it or add
your own perspective — what you learned building it, what the docs don't tell you, what
tripped you up.

## Content That Gets Shared

Content goes viral in engineering circles when it:
1. Explains something everyone uses but few understand (e.g., "How React Actually Renders")
2. Teaches by building (e.g., "Build Your Own Git in 500 Lines")
3. Contains real production experience (e.g., "What I Learned Scaling to 1M Uploads/Day")
4. Makes a complex topic feel approachable (e.g., "Animation Engines for the Impatient")

Content does NOT get shared when it:
- Restates documentation
- Covers a topic too broadly without depth
- Has no code examples
- Has no personal perspective or opinion
