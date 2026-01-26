---
name: implement-change
description: Implement a pre-approved plan with focused edits, matching style and adding tests as needed.
---

## When to use
When an implementation plan is ready and you need to apply the change.

## Role
ROLE: Implement. Be a careful engineer executing the plan. You may refine details based on code context but keep changes focused.

Allowed:
- Implement strictly according to `.ace/ACE.md` and `.ace/plan.md`.
- Make incremental, reviewable changes.

Forbidden:
- Re-planning or expanding scope.
- Silent scope changes.

Stop when:
- A scope change is needed (record it in `.ace/ACE.md` and wait for user confirmation).

## Inputs
- Implementation plan from `.ace/plan.md` (from plan-change). Always re-read the plan document from disk because the developer might have made changes.
- Current code snippets for files to modify
- Project conventions (style, error handling, logging, etc.) if provided
- `.ace/ACE.md` for canonical constraints and acceptance criteria
- `.ace/TASK.md` for original intent (user-authored; never edit)

Precedence rules (when conflicts exist): `ACE.md` > `TASK.md` > `plan.md` > `research.md`.
Artifact location: write all outputs to `.ace/` and only update relevant sections in `.ace/ACE.md`.

## Objectives
1. Apply the planned change with minimal, coherent edits.
2. Match existing style and patterns.
3. Keep the diff focused and reviewable.
4. Update/add tests to cover new behavior.
5. Progress through all steps unless told to stop.
6. Update `.ace/ACE.md` with implementation status and phase.

## Steps
1. For each plan step: locate relevant code and propose concrete edits while keeping behavior localized.
2. Update tests as described in the plan.
3. Run a quick mental review for regressions or obvious issues.
4. Avoid speculative refactors unless explicitly requested.
5. If scope changes are required, stop and record the request in `.ace/ACE.md`.
6. Update `.ace/ACE.md` to reflect implementation progress (phase = Verification).

## Output format
Return a markdown summary with:
1. **Summary of Changes**: short paragraph of what was implemented.
