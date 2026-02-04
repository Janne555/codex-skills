---
name: task-planner
description: Help design or refine a task definition, typically for `.ace/TASK.md`, by clarifying goals, scope, constraints, acceptance criteria, and risks. Use when a user needs help formulating a task request, turning a rough idea into a concrete task, or aligning a task with an existing spec. If the request is for a durable feature/system description rather than a task, route to feature-specs.
---

# Task Planner

## Goals
- Produce a clear task definition or a draft `.ace/TASK.md`.
- Ask only the missing questions needed to remove ambiguity.

## Workflow
1. Classify the request as a task vs. a feature spec. If it should be a spec, suggest `feature-specs` and pause. If the user still wants a task, proceed.
2. Gather context: goal, constraints, acceptance criteria, non-goals, dependencies, stakeholders, risks, priority, and timeline.
3. Ask up to 5 focused questions (prefer yes/no or short answers).
4. Draft `.ace/TASK.md` using the template below and list any assumptions to confirm.
5. If there is no `.ace/` context, provide the template and ask where it should live.

## `.ace/TASK.md` template
```
# Task
<short description>

## Constraints
- <constraint>

## Acceptance criteria
- [ ] <criterion>
```

## Prompting tips
- For small tasks, ask 1-3 questions.
- When scope is unclear, ask what success looks like and what is explicitly out of scope.
- When a spec exists, align the task to it and do not add new requirements.
