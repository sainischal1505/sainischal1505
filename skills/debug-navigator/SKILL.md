---
name: debug-navigator
description: >
  Systematically debug issues and navigate unfamiliar codebases — trace execution paths,
  identify root causes, and produce structured bug analysis with fixes and preventive tests.
  Works on local code, uploaded files, or described problems. The output follows a reproducible
  methodology: reproduce → narrow → identify → fix → prevent. Use this skill whenever someone
  needs to debug code, understand error traces, navigate an unfamiliar codebase, or trace
  how code executes. Also trigger when users mention 'debug this,' 'why is this broken,'
  'trace this error,' 'find the bug,' 'help me understand this code,' 'walk through this
  execution,' 'where is this called from,' 'how does this function get invoked,' 'trace the
  data flow,' 'I am getting this error,' 'this does not work and I do not know why,'
  'navigate this codebase,' 'find where X happens,' 'help me read this code,' 'I inherited
  this codebase.' This skill teaches the debugging process as it solves the problem — the
  user gets better at debugging, not just a fix for this bug.
---

# Debug Navigator

Debug systematically, not by guessing. When someone brings a bug or an unfamiliar codebase,
follow a process that reliably finds answers — and teach the user to think the same way.

The output is both the **solution** and the **process**. The user should finish each debugging
session understanding not just what was wrong, but how to find similar problems on their own.

## Two Modes

### Mode A: "Something is broken" (Debugging)
The user has a specific problem — an error, unexpected behavior, a crash. Follow the
debugging methodology to find and fix the root cause.

### Mode B: "Help me understand this code" (Navigation)
The user needs to understand unfamiliar code — how it's structured, how a feature works,
where something happens. Trace the code systematically.

---

## Mode A: Debugging Methodology

### Phase 1: Reproduce and Understand

Before touching code, establish the facts. Ask (or extract from context):

| Question | Why it matters |
|----------|---------------|
| What should happen? | Defines correct behavior — without this, you can't identify the bug |
| What actually happens? | The symptom — this is where you start tracing |
| What changed recently? | 80% of bugs are in recent changes |
| Is it consistent? | Consistent = logic error. Intermittent = timing/concurrency/state |
| What's the error message? | The stack trace is the most valuable clue. Read it bottom-to-top. |

If the user can't answer these yet, help them reproduce the issue before going further.
A bug you can't reproduce is a bug you can't verify you've fixed.

### Phase 2: Narrow the Search Space

Go from "something is broken" to "the bug is in this function" as fast as possible.

**Strategy 1: Binary search** (best for "wrong output" bugs)
1. Check the input at the entry point — is it correct?
2. Check the output at the exit point — is it correct?
3. If input is good and output is bad, check the midpoint
4. Narrow by half each time until you find the exact function where data goes wrong

**Strategy 2: Stack trace** (best for crashes/errors)
1. Read the stack trace bottom-to-top (bottom is the crash, top is where it started)
2. Find the first frame that's in user code (not library/framework code)
3. That's where the bug was introduced or where bad data entered the system

**Strategy 3: Diff-based** (best for regressions)
1. What changed since it last worked?
2. Read the diff — the bug is almost always in the change
3. If the diff is large, use binary search on commits (git bisect)

**Strategy 4: State inspection** (best for intermittent bugs)
1. Log the state at each step of the flow
2. Compare the failing run with a successful run
3. The first point of divergence is near the bug

**Narrate your strategy as you go.** Don't just say "I found the bug." Say "I'm using the
binary search approach — checking the midpoint to see if data is still correct here..."
This teaches the user the methodology.

### Phase 3: Identify Root Cause

When you find the problematic code, produce a clear diagnosis:

```markdown
## Root Cause

**Location:** `[file]:[line]` — `[function name]`
**What's wrong:** [One sentence — the specific error]
**Why it's wrong:** [One sentence — the logic/assumption that's incorrect]
**How it manifests:** [One sentence — why this causes the symptom the user sees]
```

### Phase 4: Fix

Produce the actual fix with explanation:

```markdown
## Fix

**Changed:** `[file]:[line range]`

**Before:**
```[language]
[original code]
```

**After:**
```[language]
[fixed code]
```

**Why this fixes it:** [One sentence]
**Side effects:** [Any risks or other code that might be affected]
```

### Phase 5: Prevent

Every bug that reaches a user is a missing test. Produce:

```markdown
## Prevention

**Test to add:**
```[language]
[A test that would have caught this bug — complete, runnable]
```

**Pattern to watch for:** [What should the user look for to avoid similar bugs]
```

---

## Mode B: Codebase Navigation

### Phase 1: Understand the Request

The user wants to know how something works. Identify:
- **Target:** What specific feature/behavior/flow are they asking about?
- **Depth:** Do they need a high-level overview or line-by-line understanding?
- **Goal:** Are they trying to modify this code, debug it, or just understand it?

### Phase 2: Locate the Code

**Entry point discovery:**
1. Search for relevant strings (UI text, API endpoints, error messages, function names)
2. Check package.json scripts, main/bin fields, framework-specific entry points
3. Follow imports from the entry point to trace the feature

**Feature location:** When the user asks "where does X happen":
1. Search for strings the user would see (button text, error messages, API paths)
2. Trace from that UI/API layer down into the logic
3. Map the full call chain

### Phase 3: Trace the Flow

Produce a structured trace:

```markdown
## Code Trace: [Feature Name]

**Entry point:** `[file]:[function]`
**Trigger:** [What starts this flow — user action, API call, timer, etc.]

### Step-by-step

1. **[file:function]** — [What happens. What data is involved.]
2. **[file:function]** — [What happens. Why it calls the next step.]
3. **[file:function]** — [What happens. What the result is.]

### Key data structures

- `[TypeName]` — [What it represents. Where it's created and consumed.]

### Non-obvious details

- [Something that would trip up someone reading this code for the first time]
```

### Phase 4: Reading Strategy

For the user who says "I inherited this codebase":

Read in this order — it's the fastest path to understanding:
1. **Types/interfaces** — data shapes tell you what the system thinks about
2. **Tests** — tests are documentation of intended behavior
3. **Public API** — what does each module expose?
4. **Entry points** — where does execution start?
5. **Core logic** — how does data transform?

---

## Common Bug Patterns

Recognize these and check for them early — they account for most bugs:

| Pattern | Symptom | Where to look |
|---------|---------|--------------|
| Null/undefined propagation | Crash 3 layers deep from the source | Trace backward from crash to find where null was introduced |
| Async ordering | "Works sometimes" | Look for parallel promises, missing awaits, race conditions |
| Stale closure | React state shows old value | useEffect/useCallback dependency arrays |
| Off-by-one | Wrong count, missing last item | Loop bounds, array indices, pagination |
| Silent error swallowing | "Nothing happens" | Try/catch blocks with empty catch |
| Type coercion | "0" is truthy but `==` false | Strict equality checks, parseInt without radix |
| Missing await | Promise object instead of result | Check every async function call |

---

## Reference Files

- **`references/debugging-checklist.md`** — Quick-reference checklist for common debugging
  scenarios by error type. Read when diagnosing specific error categories.
