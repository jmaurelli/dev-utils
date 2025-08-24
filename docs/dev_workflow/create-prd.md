Developer: # Workflow: Product Requirements Document (PRD) Creation (MVP-First)

## Objective
Efficiently capture an idea and transform it into a **Lean PRD** focused on MVP development. The PRD should be lightweight, actionable, and quick to produce, with the flexibility to be expanded into a Full PRD if needed.

---

## Workflow (Lean-First)
Begin with a concise checklist (3-7 bullets) of what you will do; keep items conceptual, not implementation-level.
1. Capture the feature or idea succinctly in 1–2 sentences.
2. Ask only the most **critical clarifying questions** (e.g., What problem does this solve? Who is the user? What defines success?).
3. Complete the **Lean PRD template** provided below.
4. Save the PRD in the `/prd/` directory.
After each step, verify that all required information has been captured; if not, request only the minimal essential clarification or complete the missing parts before proceeding.

---

## Lean PRD Template
```markdown
# PRD - [Feature Name]

## Overview
A one-paragraph summary describing the feature and its importance.

## Goals
- [ ] Goal 1
- [ ] Goal 2

## User Stories
- As a [user], I want [action] so that [benefit].

## Functional Requirements
1. Requirement 1
2. Requirement 2

## Success Criteria
- [ ] Metric or check for completion

## Open Questions
- [List any clarifications needed]
```

---

## Criteria for Expanding to a Full PRD
Move to a Full PRD (see `project-templates.md`) if:
- The feature is cross-functional,
- It has a significant impact on architecture or design,
- Or additional collaborators will be involved.

---

## AI Agent Directives
- Default to creating a **Lean PRD** unless otherwise instructed.
- Only request **essential clarifications**.
- Save files as `/prd/prd-[feature-name].md`.
- Limit Lean PRDs to one page or less.
After completing the Lean PRD, validate that the file exists, is accessible in the `/prd/` directory, and matches the template. If validation fails, self-correct before considering the task complete.
Set reasoning_effort = minimal, as the Lean PRD workflow is straightforward; keep outputs concise and focused.