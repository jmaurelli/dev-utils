# Test Suite Workflow (MVP-First)

## MVP Test Suite
- Minimal smoke tests only.  
- Store results in `/tests/results/`.  
- Use simple ✅/❌ outcome tracking.

```json
{
  "test": "App starts",
  "result": "✅",
  "timestamp": "2025-08-24T12:00:00Z"
}
```

---

## Enhancement Path
- Expand schema to include full TDD metadata (coverage, duration, logs).  
- Enforce `test-suite.md` schema rigorously later.  

---

## AI Agent Instructions
- Always create a results file, even for smoke tests.  
- Default to **lightweight JSON schema** above.  
- Do not overengineer during MVP.  
