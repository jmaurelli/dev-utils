# MVP-First Workflow Cheat Sheet (Optimized to 5 Docs)

## 🚀 Goal
Move fast as a solo dev to deliver an MVP, while setting the foundation for future scaling & quality.

---

## Workflow Overview
1. **Idea → PRD**  
   - Use `create-prd.md`  
   - Default: **Lean PRD** (1 page max).  
   - Only expand to Full PRD if project grows.  

2. **PRD → Tasks + Testing**  
   - Use `tasks-and-testing.md`  
   - Extract 3–5 parent tasks, break into small sub-tasks.  
   - Add smoke tests + stubs inline with tasks.  
   - Save to `/tasks/tasks-[prd-name].md`.  

3. **Tasks → Code**  
   - Implement quickly.  
   - Write smoke tests for core flows.  
   - Place test stubs alongside code.  

4. **Deploy MVP**  
   - Use notes from `project-templates.md` (Lean Deployment).  
   - Ship as soon as smoke tests pass.  

5. **Enhancement Mode (later)**  
   - Expand Lean PRDs → Full PRDs.  
   - Expand tasks → full TDD.  
   - Expand smoke tests → full test suite.  
   - Add monitoring & performance.  

---

## Document Roles
- `create-prd.md` → Capture idea, make Lean PRD.  
- `tasks-and-testing.md` → Turn PRD into tasks **with built-in testing guidance**.  
- `project-templates.md` → Library of Lean/Full docs.  
- `software-project-workflow-guide.md` → Defines MVP vs Enhancement modes.  
- `test-suite.md` → Store results in JSON, expand schema later.  

---

## AI Agent Rules (MVP Mode)
- Default to Lean templates.  
- Do not generate excessive clarifications.  
- Always create test stubs, but only smoke tests are required now.  
- Keep all docs ≤1 page during MVP.  
- Save files in the correct folders (`/prd/`, `/tasks/`, `/tests/`).  

---

## Example Flow
1. Capture feature → Lean PRD (`prd-user-login.md`).  
2. Generate tasks + smoke tests → (`tasks-prd-user-login.md`).  
3. Implement:  
   - Code login endpoint.  
   - Smoke test: “User can log in successfully.”  
4. Deploy MVP.  
5. Expand later if project grows.  
