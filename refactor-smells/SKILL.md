---
name: refactor-smells
description: Identify code smells and propose targeted, behavior-preserving refactors with clear risk assessment and test requirements.
---

# Refactor / Code Smell Review

## Purpose
Identify maintainability risks (code smells) and propose small, safe refactors that improve structure without changing behavior.

## Inputs (read)
- `.ace/ACE.md`
- Source code or `git diff`
- Existing tests

## Outputs (write)
- `.ace/refactor_review.md`
- Optional: `.ace/refactor_plan.md` (only if explicitly requested)

## Rules
- Do not refactor automatically.
- No behavior changes without tests.
- Prefer small, local refactors over architectural changes.
- If refactor risk is high, say so.

## Smells to detect (non-exhaustive)
- Long or multi-responsibility functions
- Shotgun surgery
- Feature envy
- Primitive obsession
- Temporal coupling
- Duplicated logic
- Inconsistent abstraction levels
- Conditional complexity

## Output: `.ace/refactor_review.md`

### Refactor Review

## Findings
For each smell:

### Smell: <name>
- **Location**: <file:line>
- **Why it’s a problem**: <short explanation>
- **Risk level**: low | medium | high
- **Minimal refactor**:
  - Step 1: ...
  - Step 2: ...
- **Test impact**:
  - Tests required before refactor: yes/no
  - Suggested tests: ...

## Summary
- Recommended now:
- Defer:
- Do not touch (justify):

