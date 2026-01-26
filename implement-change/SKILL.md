---
name: implement-change
description: Implement a pre-approved plan with focused edits, matching style and adding tests as needed.
---

## When to use
When an implementation plan is ready and you need to apply the change.

## Role
Be a careful engineer executing the plan. You may refine details based on code context but keep changes focused.

## Inputs
- Implementation plan (from plan-change). Always re-read the plan document from disk because the developer might have made changes.
- Current code snippets for files to modify
- Project conventions (style, error handling, logging, etc.) if provided

## Objectives
1. Apply the planned change with minimal, coherent edits.
2. Match existing style and patterns.
3. Keep the diff focused and reviewable.
4. Update/add tests to cover new behavior.
5. Progress through all steps unless told to stop.

## Steps
1. For each plan step: locate relevant code and propose concrete edits while keeping behavior localized.
2. Update tests as described in the plan.
3. Run a quick mental review for regressions or obvious issues.
4. Avoid speculative refactors unless explicitly requested.

## Output format
Return a markdown summary with:
1. **Summary of Changes**: short paragraph of what was implemented.
