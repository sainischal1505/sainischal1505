# README Templates

## Library Template

```markdown
# [project-name]

[One sentence: what it does. Verb-first. Specific.]

## Installation

```bash
npm install [project-name]
```

## Quick Start

```typescript
import { [mainExport] } from '[project-name]';

// [Comment: what this example demonstrates]
const result = [mainExport]([minimal args]);
console.log(result); // → [expected output]
```

## API

### `[functionName](params)`

[One sentence: what it does.]

**Parameters:**
- `[param]` (`[type]`) — [what it is]

**Returns:** `[type]` — [what it contains]

**Example:**
```typescript
[runnable example]
```

[Repeat for each public function]

## Development

```bash
git clone [url]
cd [project-name]
npm install
npm test
npm run build
```

## License

MIT
```

## CLI Template

```markdown
# [project-name]

[One sentence: what it does when you run it.]

## Installation

```bash
npm install -g [project-name]
```

## Usage

```bash
[project-name] [most common usage]
```

## Commands

### `[project-name] [command]`

[What it does.]

```bash
[project-name] [command] [example flags]
```

**Flags:**
- `--[flag]` — [what it does] (default: [value])

[Repeat for each command]

## Development

```bash
git clone [url]
cd [project-name]
npm install
npm test
```

## License

MIT
```

## Web App Template

```markdown
# [project-name]

[One sentence: what it does and for whom.]

## Features

- **[Feature]** — [what it does, not how]
- **[Feature]** — [what it does, not how]
- **[Feature]** — [what it does, not how]

## Tech Stack

| Technology | Purpose |
|-----------|---------|
| [Tech] | [What it's used for in this project] |

## Getting Started

### Prerequisites

- Node.js >= 18
- [Any other requirements]

### Setup

```bash
git clone [url]
cd [project-name]
npm install
npm run dev
```

Open [http://localhost:3000](http://localhost:3000).

## Project Structure

```
src/
  components/   # UI components
  hooks/        # Custom React hooks
  lib/          # Business logic
  types/        # TypeScript types
```

## Development

```bash
npm run dev       # Start dev server
npm test          # Run tests
npm run build     # Production build
```

## License

MIT
```

## Educational Template

```markdown
# [Topic]: [Angle]

[What this repo teaches and who it's for. One sentence.]

## What You'll Learn

- [Specific thing 1 — not a topic, a skill or understanding]
- [Specific thing 2]
- [Specific thing 3]

## Prerequisites

[What the reader should already know — be honest, not aspirational.]

## Table of Contents

1. [Section 1 title](link)
2. [Section 2 title](link)
...

## [Sections]

## Further Reading

- [Resource] — [why it's worth reading]
```
