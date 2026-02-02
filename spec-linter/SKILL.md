---
name: spec-linter
description: Lint a feature spec in docs/specs for completeness, consistency with the spec template, and alignment with the specs index. Produces a pass/fail report with concrete fixes.
---

# Spec Linter

## Purpose
Evaluate whether a feature spec describes the desired system state clearly and completely. Identify missing sections, ambiguity, scope drift into implementation tasks, and index mismatches.

**Delegation note:** This is a good candidate for delegation via the `prometheus` skill when you want to avoid context pollution or use a separate agent for linting.

---

## Inputs (read)
- `docs/specs/<feature-name>.md`
- `docs/specs/_index.md`
- `/Users/janne/.codex/skills/feature-specs/references/spec-template.md` (template)
- `/Users/janne/.codex/skills/feature-specs/references/index-template.md` (index format)

---

## Outputs (write)
- `docs/specs/_spec_lint.md` (required): pass/fail report with fixes
- Optional: a "Suggested spec edits" section (not applied automatically)

---

## Rules
- Do not implement code or change the spec automatically.
- Do not rewrite the entire spec unless explicitly asked.
- Prefer concrete, minimal fixes.
- Treat the feature spec template as canonical if conflicts exist.

---

## Lint checks (rubric)

### Blocking checks (FAIL if any)

#### 1. Template coverage
- All required sections from the template must be present (Headings may be reordered, but content must exist).
- Optional sections can be empty or omitted.

#### 2. Desired-system focus
- Spec must describe target behavior and outcomes, not implementation tasks, rollout plans, or verification checklists.
- If task-like items are present, mark as out-of-scope for the spec and suggest moving to a task definition.

#### 2b. Spec language (style)
- The spec must read like a description of the desired system state, not a task list.
- Flag imperative or stepwise language ("do X", "then Y", "implement", "roll out", "verify") as task-style drift unless used inside examples.

#### 3. Functional vs non-functional requirements
- Must include both sections, with at least one concrete item each (unless explicitly marked "N/A" with justification).
- Non-functional requirements must be expressed as quality attributes or constraints, not implementation choices.

#### 4. Alternatives with rationale
- Alternatives considered section must include at least one rejected alternative and a reason for rejection.

#### 5. Change log
- Change log section must exist and include a new entry dated today or the most recent edit date present in the file.

#### 6. Index alignment
- `docs/specs/_index.md` must include a row for the spec.
- Feature name must match the filename.
- Last updated date must match the spec’s latest change log date.
- Summary must be a single sentence.

---

### Warning checks (PASS allowed, but report)
- Goals are not measurable or are framed as implementation tasks.
- User stories table is present but empty.
- Ambiguous language (e.g., "handle edge cases", "as needed") without specifics.
- Risks lack mitigations.
- Dependencies listed without owners or impact notes.

---

## Output format: `docs/specs/_spec_lint.md`

# Spec Lint Report

## Verdict
- PASS | FAIL

## Spec
- File: `docs/specs/<feature-name>.md`
- Date linted: YYYY-MM-DD

## Blocking issues (must fix)
1. <issue>
   - Evidence: <quote or reference to spec section>
   - Fix: <specific change>

## Warnings (should fix)
1. ...

## Index Check
- Row present: Yes | No
- Feature name matches filename: Yes | No
- Last updated matches change log: Yes | No
- Summary is one sentence: Yes | No

## Suggested spec edits (optional)
- <bullet list of exact edits to apply>
