---
name: plan-linter
description: Lint `.ace/plan.md` for executability, completeness, ambiguity, scope control, and alignment with `.ace/ACE.md` acceptance criteria. Outputs a pass/fail report and concrete fixes. Applies additional rules if the plan is intended for Codex Web execution.
---

# Plan Linter

## Purpose
Evaluate whether `.ace/plan.md` is ready for implementation. Identify missing pieces, ambiguity, scope creep, and misalignment with `.ace/ACE.md`.

If the plan is intended for **Codex Web execution**, apply additional readiness constraints to ensure safe, deterministic delegation.

**Delegation note:** This is a good candidate for delegation via the `prometheus` skill when you want to keep the main context clean or need a separate agent to run the linter.

---

## Inputs (read)
- `.ace/TASK.md`
- `.ace/ACE.md`
- `.ace/plan.md`

---

## Outputs (write)
- `.ace/plan_lint.md` (required): pass/fail report with fixes
- Optional: a "Suggested plan edits" section (not applied automatically)

---

## Rules
- Do not implement code.
- Do not rewrite the entire plan unless explicitly asked.
- Prefer concrete, minimal fixes.
- Treat `.ace/ACE.md` as canonical if conflicts exist.

---

## Conditional mode: Codex Web

### Detection
Enable **Codex Web rules** if **any** of the following are true:
- `.ace/plan.md` explicitly states it is intended for Codex Web
- The plan references Codex Web, delegation, or autonomous execution
- A handoff or execution prompt is present
- The invoking instruction specifies “lint for Codex Web” or equivalent

If none apply, run in **CLI / local execution mode only**.

---

## Lint checks (rubric)

### Blocking checks (FAIL if any)

#### 1. Executability
- Steps must be specific and sequential.
- Plan must name the files/components to touch (or mark unknowns explicitly).
- If multiple candidate plans are listed, a single plan must be explicitly selected in a Decision section.

#### 2. Acceptance criteria mapping
- Every acceptance criterion checkbox in `.ace/ACE.md` must map to:
  - plan step(s) that implement it
  - verification step(s) that validate it
- Mapping must reference the selected plan, not discarded candidates.

#### 3. Verification
- Must include explicit commands/tests or measurable checks.

#### 4. Ambiguity
- Flag vague language ("handle edge cases", "as needed", "make sure") and require concrete definitions.
- If an evaluation matrix is present, scores must include brief notes justifying each candidate's score.

#### 5. Scope control
- Flag steps that add new requirements not present in `.ace/TASK.md` or `.ace/ACE.md`.
- Ensure non-goals are respected.
- Candidate plans must not introduce new scope unless explicitly called out as out-of-scope.

---

### Additional blocking checks (Codex Web mode only)

#### 6. Delegation completeness
- All decisions must be written down; no steps may rely on “human judgment during implementation”.
- No step may require interactive clarification.
- Any known alternatives must be explicitly rejected in writing.

#### 7. Scope boundaries (hard limits)
- Plan must explicitly state:
  - allowed directories/files
  - forbidden directories/files (or “none”)
- Absence of explicit scope bounds is a FAIL.

#### 8. Environment assumptions
- Plan must state assumptions about:
  - dependencies
  - setup scripts
  - submodules or generated files
- If setup or maintenance steps are required, they must be referenced explicitly.

#### 9. Skill resolution
- Any skills referenced must:
  - include an explicit path
  - exist under `.codex/skills/**` (or declared equivalent)
- Implicit or “assumed” skills are a FAIL.

#### 10. Atomicity
- The plan must be executable as a **single autonomous run**, or explicitly broken into numbered autonomous phases.
- Mid-run human checkpoints are not allowed.

---

### Warning checks (PASS allowed, but report)
- Risk handling and mitigations
- Rollback/migration strategy when relevant
- Step size / ordering / incrementalism
- Candidate plans exceed 3

#### Additional warnings (Codex Web mode)
- Large refactors without explicit justification
- Verification steps that rely on visual/manual inspection
- Missing or weak success/failure reporting instructions

---

## Output format: `.ace/plan_lint.md`

# Plan Lint Report

## Verdict
- PASS | FAIL

## Mode
- CLI / Local
- Codex Web (additional rules applied)

## Candidate Plans Check (if present)
- Count: <number>
- Decision present: Yes | No
- Selected plan: <name or identifier>
- Notes: <any issues with candidate scope, missing evaluation notes, or decision clarity>

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

## Codex Web Readiness Summary (only if applicable)
- Delegation-safe: Yes | No
- Missing written decisions: <list>
- Scope boundaries explicit: Yes | No
- Environment assumptions documented: Yes | No
- Skills resolvable: Yes | No

## Suggested plan edits (optional)
- <bullet list of exact edits to apply>
