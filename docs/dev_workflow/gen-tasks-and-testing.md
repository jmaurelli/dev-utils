Developer: # Workflow: Tasks + Testing (MVP-First)

## Objective
Transform a Lean PRD into actionable tasks with integrated testing guidance. This process combines task generation and lightweight TDD into a streamlined approach suitable for solo MVP development.

---

## Workflow Steps

Begin with a concise checklist (3-7 bullets) of intended sub-tasks before proceeding; keep checklist items conceptual.

### 1. Input
- Begin with a Lean PRD (`create-prd.md`).
- Ensure the PRD contains: overview, goals, user stories, and requirements.
- If any elements are missing, clearly state what is absent at the top of the output, and skip steps that cannot be performed as a result.

### 2. Generate Parent Tasks
- Identify 3–5 parent tasks derived from the PRD.
- If fewer than 3 or more than 5 parent tasks are available, proceed with what is supported, and clearly document this under **Notes** in the output.
- Parent tasks should be clear and high-level, for example: “Implement login API.”

### 3. Expand into Sub-Tasks
- For each parent task, break it down into smaller sub-tasks (ideally actions that take less than one day) using Markdown checklists (`- [ ]`).
- Ensure that each parent task includes at least one sub-task related to testing.

**Example:**
- Parent: Implement login API
  - [ ] Define request/response schema
  - [ ] Write failing smoke test (valid + invalid login)
  - [ ] Implement minimal code to pass the test
  - [ ] Add error handling for bad input

### 4. Relevant Files
- List the files associated with each parent task in a dedicated **Relevant Files** section as a Markdown list.
- Always specify both implementation and related test files.

### 5. Changelog
- Maintain a **Changelog** at the very top of the task file in Markdown format.
- Record each change as a new bullet point, starting with `[YYYY-MM-DD]`.

---

## Testing Guidelines (MVP-First)

### MVP Mode
- Write only smoke tests for key flows:
  - App startup
  - User login
  - Main feature operation
- Place test stubs alongside code, even if mostly empty.

### Enhancement Mode (Later)
- Gradually add more tests:
  - Expand smoke tests to unit tests, then integration tests.
  - Update tasks to include design-driven TDD approaches.
  - Ensure all test results conform to the schema in `test-suite.md`.

---

## AI Agent Instructions
- Always generate both the task list and test stubs together.
- For MVP, restrict tests to smoke tests only.
- Save task files in `/tasks/tasks-[prd-name].md`, using the lowercase PRD name with hyphens.
- Output should fit on a single page for MVP; expand only if Enhancement Mode is explicitly requested.
- If instructions cannot be followed due to missing PRD data, provide a clear note in the output and indicate incomplete or omitted sections as appropriate.

Set reasoning_effort = medium due to moderate task complexity; produce tool and code outputs succinctly, but offer fuller detail in the final Markdown document.

After generating the Markdown task file, validate that all required sections (Changelog, Relevant Files, Notes if needed, Tasks) are present and in the correct order, and that every parent task contains at least one test-related sub-task. If any step is incomplete due to missing PRD data, clearly indicate this in both the Notes and Tasks sections.

---

## Output Format

Output should be a single Markdown document saved as `/tasks/tasks-[prd-name].md` and conform to the following structure:

```markdown
# Tasks for [PRD Name]

## Changelog
- [YYYY-MM-DD] Initial tasks created.
- [YYYY-MM-DD] [Description of subsequent changes]

## Relevant Files
- path/to/file1.ext – description
- path/to/file2.ext – description

## Notes
- [Freeform notes, including process deviations: e.g., “Only 2 parent tasks inferred due to limited PRD input.” “User stories section missing from PRD; requirements inferred from goals.”]

## Tasks
- [ ] 1.0 [Parent Task 1]
  - [ ] 1.1 [Subtask 1]
  - [ ] 1.2 [Subtask 2]
  ...
- [ ] 2.0 [Parent Task 2]
  ...
```

- All sections must appear in this order: Changelog, Relevant Files, Notes (optional if not needed), Tasks.
- Every parent task must include at least one test-related sub-task.
- Tasks and sub-tasks must use `- [ ]` Markdown checklists.
- The **Relevant Files** section must always list both implementation and test/validation files for each task.
- If any PRD elements are missing, identify them explicitly in **Notes** and indicate in **Tasks** which steps were omitted as a result.
