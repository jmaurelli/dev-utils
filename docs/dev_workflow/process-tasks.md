# 🔹 Consolidated Hierarchical Instructions for LLM Priming

This document unifies **Task List Management**, **TDD with Design**, and **Test Suite Standards** into a single hierarchical framework optimized for LLM execution and priming.

---

## 0. Meta Protocol (Global)

* Always operate hierarchically:

  1. **Plan**: Start with a short conceptual checklist (3–7 bullets).
  2. **Act**: Perform one sub-task at a time.
  3. **Validate**: After each step, provide a 1–2 line confirmation or self-correction.
  4. **Pause**: Wait for explicit user approval before advancing.
* Never skip validation or checkpoints.
* Keep reasoning concise, avoid verbosity.
* Before tool calls, announce purpose and minimal inputs.
* After file/code changes, validate correctness briefly.

---

## 1. Task List Management Protocol

**Purpose:** Maintain PRD-linked task lists, enforce task flow, and ensure traceability.

### Rules

* Work on **one sub-task at a time**.
* **Completion Protocol:**

  1. Mark sub-task `[x]`.
  2. Identify changed files with `git diff --name-only` (base: `main`).
  3. Run **targeted tests** for changed files → log results to `/test/` JSON files.
  4. Remove all temp files.
  5. Commit with **conventional commit message** (`feat:`, `fix:`, etc.) including summary, major changes, PRD reference.
  6. Mark parent task `[x]` once all children are done.
  7. Update `/tasks/tasks-[prd-file-name].md` changelog with date + summary.
* Maintain **Relevant Files** list continuously.

---

## 2. TDD with Design Protocol

**Purpose:** Fuse TDD with low-complexity design principles.

### Phases

1. **Pre-Implementation Planning**

   * Define requirements and acceptance criteria.
   * Propose 2+ design approaches, select lowest complexity.
   * Map data flows, dependencies, API contracts.

2. **RED Phase: Write Failing Tests**

   * Cover requirements with unit/integration/E2E.
   * Include edge cases and error scenarios.
   * Use contract-based mocks only.

3. **GREEN Phase: Minimal Implementation**

   * Start with defensive/error handling code.
   * Write minimal code to pass each test.
   * Iterate test-by-test until green.

4. **REFACTOR Phase: Improve Quality**

   * Remove duplication, simplify logic, enhance naming.
   * Validate deep modules, information hiding, error prevention.

5. **Integration & Validation**

   * Run end-to-end workflows across environments.
   * Ensure performance, accessibility, stability.

### Success Metrics

* All tests pass.
* 100% requirement coverage.
* Zero runtime errors.
* Deep modules, simple interfaces.
* Complexity hidden from consumers.

### Pitfalls to Avoid

* Writing tests after code.
* Modifying tests to fit code.
* Skipping refactor.
* Shallow modules or information leakage.

---

## 3. Test Suite Protocol

**Purpose:** Ensure test results are **machine-validated JSON** for agent consumption.

### Rules

* **Terminal output must never be read for validation.**
* All test results must be written to `/test/<test_name>.json`. The LLM/AI agent must **open and read these files directly**.
* After validation, **delete JSON files if all tests pass**. During MVP, no historical logs are maintained.
* Only if tests fail, retain the file until issues are resolved.

### Framework-Specific Commands

#### Command Selection Table

| Framework        | Command                                                                 |
| ---------------- | ----------------------------------------------------------------------- |
| **Jest**         | `jest --runInBand --json --outputFile=test/<test_name>.json <files>`    |
| **Mocha**        | `mocha --reporter json <files> > test/<test_name>.json`                 |
| **Pytest**       | `pytest <files> --json-report --json-report-file=test/<test_name>.json` |
| **Java (JUnit)** | `mvn test -DjsonReportOutput=test/<test_name>.json`                     |
| **Next.js**      | Same as Jest above                                                      |

The LLM/AI agent must auto-select the correct non-interactive JSON output command for the active framework:

* **Jest:**

  ```bash
  jest --runInBand --json --outputFile=test/<test_name>.json <files>
  ```

* **Mocha:**

  ```bash
  mocha --reporter json <files> > test/<test_name>.json
  ```

* **Pytest:**

  ```bash
  pytest <files> --json-report --json-report-file=test/<test_name>.json
  ```

* **Java (JUnit):**

  ```bash
  mvn test -DjsonReportOutput=test/<test_name>.json
  ```

* **Next.js (with Jest under the hood):** same as Jest above.

### Schema

Each JSON file must strictly contain:

* `test_name`: `[a-zA-Z0-9_-]{1,255}`
* `status`: `"passed" | "failed" | "skipped"`
* `run_time_seconds`: float, 3 decimals
* `error_message`: null if pass/skip, string if failed

### Workflow

#### Quick Checklist

1. **Plan**: Identify changed files and relevant tests.

2. **Run**: Execute framework-specific command to output JSON results.

3. **Validate**: Open and read JSON file(s), check schema and outcomes.

4. **Delete**: If all tests pass, delete JSON file(s); if not, retain until fixed.

5. Run only the relevant/changed tests, output to `/test/` JSON.

6. LLM **must read the JSON file**, validate schema, and report outcome.

7. If all pass → delete file(s). If failures → retain file(s) until fixed.

### Output Example

```json
{
  "test_name": "integration_case12",
  "status": "failed",
  "run_time_seconds": 2.304,
  "error_message": "Expected value not found in response"
}
```

### Success Conditions

* All result files schema-validated.
* No CLI interaction (watch/quit prompts forbidden).
* Files deleted automatically after successful runs.
* Only JSON file contents, never terminal logs, are used for validation.

---

# 🔹 Usage Flow

1. Prime with **Meta Protocol (0)**.
2. Select applicable protocol (Task List, TDD, or Test Suite).
3. Follow hierarchical steps: **Plan → Act → Validate → Pause**.
4. Confirm correctness and alignment before moving forward.
