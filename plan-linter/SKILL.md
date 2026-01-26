---
name: plan-linter
description: Lint `.ace/plan.md` for executability, completeness, ambiguity, scope control, and alignment with `.ace/ACE.md` acceptance criteria. Outputs a pass/fail report and concrete fixes.
---

# Plan Linter

## Purpose
Evaluate whether `.ace/plan.md` is ready for implementation. Identify missing pieces, ambiguity, scope creep, and misalignment with `.ace/ACE.md`.

## Inputs (read)
- `.ace/TASK.md`
- `.ace/ACE.md`
- `.ace/plan.md`

## Outputs (write)
- `.ace/plan_lint.md` (required): pass/fail report with fixes
- Optional: a "Suggested plan edits" section (not applied automatically)

## Rules
- Do not implement code.
- Do not rewrite the entire plan unless explicitly asked.
- Prefer concrete, minimal fixes.
- Treat `.ace/ACE.md` as canonical if conflicts exist.

## Lint checks (rubric)

### Blocking checks (FAIL if any)
1. **Executability**
   - Steps must be specific and sequential.
   - Plan must name the files/components to touch (or mark unknowns explicitly).

2. **Acceptance criteria mapping**
   - Every acceptance criterion checkbox in `.ace/ACE.md` must map to:
     - plan step(s) that implement it
     - verification step(s) that validate it

3. **Verification**
   - Must include explicit commands/tests or measurable checks.

4. **Ambiguity**
   - Flag vague language ("handle edge cases", "as needed", "make sure") and require concrete definitions.

5. **Scope control**
   - Flag steps that add new requirements not present in `.ace/TASK.md` or `.ace/ACE.md`.
   - Ensure non-goals are respected.

### Warning checks (PASS allowed, but report)
- Risk handling and mitigations
- Rollback/migration strategy when relevant
- Step size / ordering / incrementalism

## Output format: `.ace/plan_lint.md`

# Plan Lint Report

## Verdict
- PASS | FAIL

## Blocking issues (must fix)
1. <issue>
   - Evidence: <quote or reference to plan section>
   - Fix: <specific change>

## Warnings (should fix)
1. ...

## Acceptance Criteria Coverage Table
For each acceptance criterion in `.ace/ACE.md`:
- Criterion: ...
- Plan step(s): ...
- Verification: ...
- Status: Covered | Missing | Unclear

## Suggested plan edits (optional)
- <bullet list of exact edits to apply>

