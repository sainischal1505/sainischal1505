# Debugging Checklist

## By Error Type

### TypeError / "Cannot read property X of undefined"

1. What variable is undefined? (Read the error message — it names the property, not the variable)
2. Trace backward: where was this variable supposed to get its value?
3. Check: Is it an async issue? (Variable not yet populated when accessed)
4. Check: Is it a conditional path? (Variable only set in one branch of an if/else)
5. Check: Is it a typo? (Property name misspelled)
6. Check: Is it a null propagation? (Something 3 calls back returned null)

### "Network Error" / Fetch failures

1. Is the server running? (Check the URL in a browser)
2. Is it CORS? (Check browser console for CORS errors specifically)
3. Is it auth? (Check if the token/cookie is being sent. Check 401 vs other errors.)
4. Is it the request format? (Compare working request with failing request — headers, body)
5. Is it intermittent? (Timeout? Rate limit? Network instability?)

### "State is wrong" / Unexpected behavior (no error)

1. Log the state at the entry point — is the input correct?
2. Log the state at the exit point — is the output correct?
3. Binary search: log at the midpoint of the flow
4. If React: check if the component is re-rendering when you expect it to
5. If React: check if state update is batched (async setState)
6. If global state: check if another component is mutating the same state

### "Works locally, fails in production"

1. Environment variables — are they set in production?
2. API URLs — hardcoded localhost somewhere?
3. Build differences — dev mode vs production build (tree shaking, minification)
4. CORS/CSP — production domain not in allowed origins?
5. Dependencies — version differences between environments?

### "Works sometimes, fails sometimes" (intermittent)

1. Race condition — two async operations finishing in different order
2. Cache — stale data from a previous request
3. Memory — growing memory usage causing GC pauses
4. External dependency — flaky API, rate limits, timeouts
5. Concurrency — multiple users/requests interacting

### Infinite loop / Hang

1. useEffect with missing or wrong dependency array → re-render loop
2. Recursive function without base case
3. Circular dependency between modules
4. Event listener triggering its own event
5. Promise that never resolves (missing resolve/reject call)

### Performance issue

1. Profile first — don't guess. Use browser DevTools Performance tab.
2. Is it rendering? (React DevTools → Highlight updates)
3. Is it data? (Large dataset being processed on every render)
4. Is it network? (Waterfall of sequential requests that could be parallel)
5. Is it a loop? (O(n²) algorithm that worked on small data, slow on large data)

## Quick Checks (do these first, every time)

- [ ] Read the FULL error message. Not just the first line.
- [ ] Check the stack trace. The answer is usually in there.
- [ ] What changed? (git diff, recent deployments, recent config changes)
- [ ] Can you reproduce it consistently?
- [ ] Does it happen in a fresh environment? (new browser tab, cleared cache)
