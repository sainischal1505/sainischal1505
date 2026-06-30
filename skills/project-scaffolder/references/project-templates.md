# Project Templates

## TypeScript Library / Package

```
[project-name]/
├── src/
│   ├── index.ts              # Public API — re-exports everything consumers need
│   └── [core-module].ts      # Core implementation (name after what it does)
├── tests/
│   └── [core-module].test.ts # Tests the core module
├── .github/
│   └── workflows/
│       └── ci.yml            # See ci-templates.md
├── package.json
├── tsconfig.json
├── vitest.config.ts
├── .gitignore
├── LICENSE
└── README.md
```

### package.json essentials
```json
{
  "name": "[project-name]",
  "version": "0.1.0",
  "description": "[one sentence]",
  "main": "dist/index.js",
  "types": "dist/index.d.ts",
  "files": ["dist"],
  "scripts": {
    "build": "tsc",
    "test": "vitest run",
    "test:watch": "vitest",
    "typecheck": "tsc --noEmit"
  },
  "engines": { "node": ">=18" },
  "license": "MIT",
  "devDependencies": {
    "typescript": "^5.0.0",
    "vitest": "^1.0.0"
  }
}
```

### tsconfig.json
```json
{
  "compilerOptions": {
    "target": "ES2022",
    "module": "Node16",
    "moduleResolution": "Node16",
    "declaration": true,
    "outDir": "dist",
    "rootDir": "src",
    "strict": true,
    "esModuleInterop": true,
    "skipLibCheck": true,
    "forceConsistentCasingInFileNames": true
  },
  "include": ["src"],
  "exclude": ["node_modules", "dist", "tests"]
}
```

### vitest.config.ts
```typescript
import { defineConfig } from 'vitest/config';

export default defineConfig({
  test: {
    include: ['tests/**/*.test.ts'],
  },
});
```

### .gitignore (TypeScript)
```
node_modules/
dist/
*.tsbuildinfo
.env
.DS_Store
```

---

## TypeScript CLI Tool

```
[project-name]/
├── src/
│   ├── cli.ts                # Entry point — arg parsing only
│   ├── commands/
│   │   └── [command].ts      # One file per command
│   └── lib/
│       └── [core].ts         # Core logic (testable without CLI)
├── tests/
│   └── lib/
│       └── [core].test.ts
├── bin/
│   └── [project-name]        # #!/usr/bin/env node shebang
├── .github/
│   └── workflows/
│       └── ci.yml
├── package.json
├── tsconfig.json
├── vitest.config.ts
├── .gitignore
├── LICENSE
└── README.md
```

**Key principle:** Separate CLI concerns (argument parsing, output formatting) from core
logic. The `lib/` directory should be fully testable without invoking the CLI.

### bin/[project-name]
```bash
#!/usr/bin/env node
require('../dist/cli.js');
```

### package.json additions for CLI
```json
{
  "bin": { "[project-name]": "bin/[project-name]" },
  "scripts": {
    "build": "tsc",
    "test": "vitest run",
    "dev": "ts-node src/cli.ts"
  }
}
```

---

## React Web App

```
[project-name]/
├── src/
│   ├── App.tsx               # Root component
│   ├── main.tsx              # Entry point (ReactDOM.render)
│   ├── components/           # UI components
│   │   └── [Component].tsx
│   ├── hooks/                # Custom React hooks
│   │   └── use[Hook].ts
│   ├── lib/                  # Business logic (NO React imports)
│   │   └── [module].ts
│   └── types/                # Shared TypeScript types
│       └── index.ts
├── tests/
│   └── lib/
│       └── [module].test.ts  # Test business logic, not components
├── .github/
│   └── workflows/
│       └── ci.yml
├── index.html
├── package.json
├── tsconfig.json
├── vite.config.ts
├── .gitignore
├── LICENSE
└── README.md
```

**Key principle:** Keep business logic in `lib/` with zero React dependencies. This makes
it testable with simple unit tests — no component rendering required. Test the logic, not
the UI.

---

## Python Library / Tool

```
[project-name]/
├── src/
│   └── [project_name]/
│       ├── __init__.py       # Public API
│       ├── core.py           # Core implementation
│       └── utils.py          # Shared utilities
├── tests/
│   ├── conftest.py           # Shared fixtures
│   └── test_core.py
├── .github/
│   └── workflows/
│       └── ci.yml
├── pyproject.toml            # Modern Python packaging (PEP 621)
├── .gitignore
├── LICENSE
└── README.md
```

### pyproject.toml
```toml
[project]
name = "[project-name]"
version = "0.1.0"
description = "[one sentence]"
requires-python = ">=3.10"
license = { text = "MIT" }

[build-system]
requires = ["setuptools>=68.0"]
build-backend = "setuptools.build_meta"

[tool.pytest.ini_options]
testpaths = ["tests"]

[tool.setuptools.packages.find]
where = ["src"]
```

### .gitignore (Python)
```
__pycache__/
*.pyc
dist/
*.egg-info/
.env
.venv/
.DS_Store
```

---

## README Template (all project types)

```markdown
# [project-name]

[One sentence: what it does. Specific. Not "a tool for..." — state the action.]

## Installation

[Exact command. Nothing else.]

## Quick Start

[Minimal working example. Copy-paste-runnable. 5-15 lines of code.]

## API

[For libraries: document each public function/method.]
[For CLIs: document each command and its flags.]
[For apps: document how to configure and use.]

## Development

git clone [url]
cd [project-name]
[install command]
[test command]
[build command]

## License

MIT
```
