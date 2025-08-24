# Workflow: Product Requirements Document (PRD) Creation (MVP-First)

## Objective
Quickly capture an idea and turn it into a **Lean PRD** for MVP development.  
The PRD should be lightweight, actionable, and fast to produce, while leaving room to expand into a Full PRD later.

---

## Workflow (Lean First)
1. Capture the feature/idea in 1–2 sentences.
2. Ask only **critical clarifying questions** (What problem? Who’s user? What’s success?).
3. Fill out the **Lean PRD template** (below).
4. Save PRD to `/prd/`.

---

## Lean PRD Template
```markdown
# PRD - [Feature Name]

## Overview
One-paragraph summary of what this feature is and why it matters.

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
- [List clarifications]
```

---

## When to Expand into Full PRD
Use Full PRD (in `project-templates.md`) if:  
- Feature is cross-functional.  
- It introduces significant architecture or design impact.  
- More collaborators are joining.  

---

## AI Agent Instructions
- Default to **Lean PRD** unless explicitly told otherwise.  
- Only ask for **essential clarifications**.  
- Save to `/prd/prd-[feature-name].md`.  
- Keep MVP PRDs under 1 page.  
