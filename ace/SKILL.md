---
name: ace
description: Coordinate the research, planning, and implementation skills end-to-end to deliver a task.
---

## When to use
Use for end-to-end engineering tasks that need explicit Research, Plan, Implement, and Verify phases in sequence.

## Role
Act as the driver: enforce role boundaries, manage `.ace/` task artifacts, run supporting skills, and keep stakeholders informed.

## Rules
- The workflow consists of 4 phases: Research, Plan, Implement, Verify.
- Each phase produces a corresponding `.ace/` artifact and updates `.ace/ACE.md`.
- Unless stated otherwise, stop before starting the next phase.
- Do not overwrite existing `.ace/` artifacts created by the user or another agent.
- Enforce precedence when documents conflict: `ACE.md` > `TASK.md` > `plan.md` > `research.md`.
- Compaction or session restarts should happen only at phase boundaries.
- Artifact location: write all outputs to `.ace/` and only update relevant sections in `.ace/ACE.md`.

## Inputs
- User problem/feature request and constraints
- Relevant logs, traces, or tickets (if any)
- Codebase pointers or prior context
- `.ace/TASK.md` when present (user-authored; never edit)

## Objectives
1. Align on scope, success criteria, and constraints.
2. Ensure `.ace/` artifacts exist and `ACE.md` is canonical.
3. Produce a research doc via `research-codebase` to map current behavior and risks.
4. Produce an implementation plan via `plan-change` based on the research.
5. Implement the approved plan via `implement-change`, including tests.
6. Verify outcomes (tests, diff review) without expanding scope.
7. Report outcomes, validation steps, and follow-ups.

## Steps
1. Confirm desired behavior, edge cases, constraints, and deliverables.
2. Ensure `.ace/` exists. If `.ace/TASK.md` is missing, prompt the user to create it and stop. If `.ace/ACE.md` is missing, create it using the template below.
3. Run `research-codebase`; capture and share `.ace/research.md`.
4. Review research findings; surface open questions or decisions needed and stop before planning.
5. Run `plan-change` using `.ace/research.md`; ensure steps are actionable and testable.
6. Execute `implement-change` per `.ace/plan.md`; keep changes focused and aligned with style.
7. Enter Verify role: run tests or validate diffs, identify concrete issues, and stop if fixes are required.
8. Summarize changes, tests run, and any remaining risks or todos. If changes have security impacts, refer to the [security integraion section](#When security review is required).
9. Run the `style-enforcer` skill to evaluate the changes.
10. Run the `refactor-smells` skill to evaluate the quality of the changes.
11. If the task produce changes to UI run the `a11y-review` skill to verify accessibility.

## Templates
Use these templates when creating missing artifacts.

### `.ace/ACE.md` template
```
# ACE: Task State

## Task goal
<1-2 sentences>

## Non-goals / out of scope
- <item>

## Decisions made
- <decision + short rationale>

## Hard constraints
- <constraint>

## Acceptance criteria
- [ ] <criterion>

## Current phase
Research

## Next steps
- <next step>

## Known risks / open questions
- <risk or question>
```

### `.ace/TASK.md` template (user-authored)
```
# Task
<short description>

## Constraints
- <constraint>

## Acceptance criteria
- [ ] <criterion>
```

## Output format
Provide a concise status update including:
- Research document summary and location
- Plan summary and key steps
- Implementation status, tests executed, and next actions
- Current phase and any updates to `.ace/ACE.md`

## Security integration

### When security review is required
Run a security review if the task involves any of:
- auth/authz/session handling
- untrusted input (HTTP/API/CLI/file/env)
- file upload/download
- secrets/keys/tokens
- PII or sensitive data
- external integrations or webhooks
- new or changed public endpoints

### How to run it
After implementation (and before final verification/Done):
1) Switch to `ROLE: Security Audit`.
2) Invoke the `infosec-audit` skill.
3) Produce `.ace/security_review.md`.
4) Update `.ace/ACE.md`:
   - add/complete an acceptance checkbox: "Security audit complete"
   - copy the top 3 risks (or "no significant issues found") into "Open questions / risks".

