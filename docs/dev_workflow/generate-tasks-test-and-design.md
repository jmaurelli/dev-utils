# Workflow: Tasks + Testing (MVP-First)

## Objective
Transform a Lean PRD into actionable tasks **with built-in testing guidance**.  
This unifies task generation and lightweight TDD into a single streamlined process for solo MVP development.

---

## Workflow Steps

### 1. Input
- Start from a Lean PRD (`create-prd.md`).  
- Confirm PRD has: overview, goals, user stories, requirements.  

### 2. Generate Parent Tasks
- Extract 3–5 parent tasks from PRD.  
- Keep them clear and high-level.  
- Example: “Implement login API.”  

### 3. Expand into Sub-Tasks
- Break down each parent task into small, <1-day actions.  
- Always include at least one test-related sub-task.  

**Example:**  
- Parent: Implement login API  
  - [ ] Define request/response schema  
  - [ ] Write failing smoke test (valid + invalid login)  
  - [ ] Implement minimal code to pass test  
  - [ ] Add error handling for bad input  

### 4. Relevant Files
For each task, list files to create/touch:  
```markdown
- src/api/login.ts – Implementation
- src/api/login.test.ts – Test stub/smoke test
```

### 5. Changelog
Maintain changelog at the top of task file:  
```markdown
## Changelog
- [2025-08-24] Initial tasks created.
```

---

## Testing Guidelines (MVP-First)

### MVP Mode
- Write **smoke tests only** for core flows:  
  - App starts  
  - User can log in  
  - Key feature works  
- Place test stubs alongside code, even if mostly empty.  

### Enhancement Mode (Later)
- Expand smoke tests → unit tests → integration tests.  
- Refactor tasks to include design-driven TDD steps.  
- Ensure all test results follow schema in `test-suite.md`.  

---

## Task File Example
```markdown
# Tasks for User Login

## Changelog
- [2025-08-24] Initial tasks created.

## Relevant Files
- src/api/login.ts – Backend login handler
- src/api/login.test.ts – Smoke test

## Notes
- MVP: Only smoke test for valid/invalid login.
- Later: Expand with TDD and edge cases.

## Tasks
- [ ] 1.0 Implement Login API
  - [ ] 1.1 Define API schema
  - [ ] 1.2 Write smoke test (login success/failure)
  - [ ] 1.3 Implement minimal endpoint
  - [ ] 1.4 Add error handling
```

---

## AI Agent Instructions
- Always generate **task list + test stubs together**.  
- For MVP: limit to smoke tests.  
- Save task files to `/tasks/tasks-[prd-name].md`.  
- Keep output ≤1 page for MVP.  
- Expand only when explicitly requested (Enhancement Mode).  
