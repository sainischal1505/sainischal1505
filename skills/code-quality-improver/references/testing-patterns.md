# Testing Patterns

## Test File Structure (TypeScript / Vitest)

```typescript
import { describe, it, expect } from 'vitest';
import { functionUnderTest } from '../src/module';

describe('functionUnderTest', () => {
  describe('happy path', () => {
    it('returns correct result for standard input', () => {
      const result = functionUnderTest(validInput);
      expect(result).toEqual(expectedOutput);
    });

    it('handles multiple items correctly', () => {
      const result = functionUnderTest([item1, item2, item3]);
      expect(result).toHaveLength(3);
      expect(result[0]).toMatchObject({ key: 'expected' });
    });
  });

  describe('edge cases', () => {
    it('returns empty result for empty input', () => {
      expect(functionUnderTest([])).toEqual([]);
    });

    it('handles single item', () => {
      expect(functionUnderTest([oneItem])).toEqual([expectedSingle]);
    });

    it('handles maximum allowed input', () => {
      const largeInput = Array.from({ length: 10000 }, (_, i) => makeItem(i));
      const result = functionUnderTest(largeInput);
      expect(result).toHaveLength(10000);
    });
  });

  describe('error cases', () => {
    it('throws TypeError for null input', () => {
      expect(() => functionUnderTest(null)).toThrow(TypeError);
    });

    it('throws RangeError for negative values', () => {
      expect(() => functionUnderTest(-1)).toThrow(RangeError);
    });
  });
});
```

## Test File Structure (Python / pytest)

```python
import pytest
from project_name.module import function_under_test


class TestFunctionUnderTest:
    """Tests for function_under_test."""

    def test_standard_input(self):
        result = function_under_test(valid_input)
        assert result == expected_output

    def test_empty_input(self):
        assert function_under_test([]) == []

    def test_null_input_raises(self):
        with pytest.raises(TypeError):
            function_under_test(None)

    @pytest.fixture
    def large_dataset(self):
        return [make_item(i) for i in range(10000)]

    def test_large_input(self, large_dataset):
        result = function_under_test(large_dataset)
        assert len(result) == 10000
```

## Assertion Guide

| What you're checking | Assertion | NOT this |
|---------------------|-----------|----------|
| Exact value | `expect(x).toEqual(5)` | `expect(x).toBeTruthy()` |
| Object shape | `expect(x).toMatchObject({key: val})` | `expect(JSON.stringify(x)).toContain(...)` |
| Array contents | `expect(arr).toContain(item)` | `expect(arr.includes(item)).toBe(true)` |
| Thrown error | `expect(() => fn()).toThrow(Type)` | Try/catch with manual check |
| Async rejection | `await expect(fn()).rejects.toThrow()` | Try/catch |
| Called with args | `expect(spy).toHaveBeenCalledWith(x)` | Manual tracking |

## Test Naming Convention

Test names should be sentences that describe behavior:
- `it('returns empty array when input is empty')`
- `it('throws TypeError when called with null')`
- `it('retries failed request up to 3 times')`
- `it('applies discount when cart total exceeds threshold')`

NOT: `it('test1')`, `it('should work')`, `it('handles edge case')`

## What to mock

- External APIs and services → always mock
- Database calls → mock in unit tests, real DB in integration tests
- File system → mock unless testing file operations specifically
- Time/dates → mock when testing time-dependent logic
- Internal modules → do NOT mock. If you need to mock an internal module, the code
  probably needs refactoring, not more mocks.
