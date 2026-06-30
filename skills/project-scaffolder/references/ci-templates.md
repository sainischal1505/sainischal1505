# CI Templates

## TypeScript (npm + Vitest)

```yaml
name: CI

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  build-and-test:
    runs-on: ubuntu-latest
    strategy:
      matrix:
        node-version: [18, 20]
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: ${{ matrix.node-version }}
          cache: 'npm'
      - run: npm ci
      - run: npm run typecheck
      - run: npm test
      - run: npm run build
```

## Python (pytest)

```yaml
name: CI

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest
    strategy:
      matrix:
        python-version: ['3.10', '3.11', '3.12']
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-python@v5
        with:
          python-version: ${{ matrix.python-version }}
      - run: pip install -e ".[dev]"
      - run: pytest
```

## Rules

- Only reference scripts that exist in `package.json` or `pyproject.toml`.
- Use `npm ci` not `npm install` — it's faster and deterministic.
- Cache dependencies (`cache: 'npm'` or pip cache).
- Test on 2 runtime versions minimum.
- Don't add deployment, publishing, or Docker steps unless the user asks.
- Don't add linting steps unless a linter is configured in the project.
