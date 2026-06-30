# Codebase-to-Course

A Claude skill that transforms engineering knowledge into published educational content — Build-Your-Own tutorials, deep-dive articles, and learning paths that position the author as a domain expert.

## What It Does

Turn what you know from building real systems into content other engineers will bookmark and share. It produces Build-Your-Own tutorial repos, deep-dive articles, or learning paths — each with real code examples, Mermaid diagrams, and progressive complexity.

## Output

### Build-Your-Own Tutorial (strongest for GitHub)
```
build-your-own-[thing]/
├── README.md                    # Full tutorial text
├── src/
│   ├── step-01-foundation/      # Minimal working version
│   ├── step-02-[feature]/       # Add first feature
│   ├── step-03-[feature]/       # Add second feature
│   └── final/                   # Complete implementation
├── diagrams/
└── LICENSE
```

### Deep-Dive Article (strongest for blogs)
```
deep-dive-[topic]/
├── README.md                    # The article (2000-4000 words)
├── diagrams/
├── code/                        # Runnable code examples
└── LICENSE
```

## How to Trigger

- "Turn this into a tutorial"
- "Write a Build-Your-Own animation engine tutorial"
- "Create a deep dive about how media pipelines work"
- "Help me write a technical blog post"

## Files

```
codebase-to-course/
├── SKILL.md                          # Main skill instructions
├── README.md                         # This file
└── references/
    └── content-rules.md              # Writing standards, code examples, anti-patterns
```

## Installation

Copy the `codebase-to-course` folder into `~/.claude/skills/`.
