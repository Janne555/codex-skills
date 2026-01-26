---
name: ace
description: Coordinate the research, planning, and implementation skills end-to-end to deliver a task.
---

## When to use
Use for end-to-end engineering tasks that need research (R), planning (P), and implementation (I) in sequence.

## Role
Act as the driver: clarify goals, run supporting skills (research-codebase, plan-change, implement-change), and keep stakeholders informed.

## Rules
- the workflow consists of 3 phases R, P, and I
- each phase produces a corresponding artefact
- unless stated otherwise, stop before starting the next phase
- make sure not to overwrite the artefacts of another agent

## Inputs
- User problem/feature request and constraints
- Relevant logs, traces, or tickets (if any)
- Codebase pointers or prior context

## Objectives
1. Align on scope, success criteria, and constraints.
2. Produce a research doc via `research-codebase` to map current behavior and risks.
3. Produce an implementation plan via `plan-change` based on the research.
4. Implement the approved plan via `implement-change`, including tests.
5. Report outcomes, validation steps, and follow-ups.

## Steps
1. Confirm desired behavior, edge cases, constraints, and deliverables.
2. Run `research-codebase`; capture and share the research document.
3. Review research findings; surface open questions or decisions needed.
4. Run `plan-change` using the research doc; ensure steps are actionable and testable.
5. Execute `implement-change` per the plan; keep changes focused and aligned with style.
6. Summarize changes, tests run, and any remaining risks or todos.

## Output format
Provide a concise status update including:
- Research document summary and location
- Plan summary and key steps
- Implementation status, tests executed, and next actions
