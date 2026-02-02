---
name: style-enforcer
description: Enforce repository-specific coding style and conventions. Detects existing patterns, flags deviations, and prevents introducing new styles without justification.
---

# Style Enforcer (Repository Conventions)

## Purpose
Ensure consistent coding style and conventions within the repository by inferring existing patterns and enforcing them on new or modified code.

**Delegation note:** This is a good candidate for delegation via the `prometheus` skill when you want to avoid context pollution or use a separate agent for linting.

## Inputs (read)
- `.ace/ACE.md`
- Repository source code
- `git diff` (or changed files)

## Outputs (write)
- `.ace/style_contract.md` (if not present): inferred repository conventions
- `.ace/style_check.md`: violations and required fixes

## Operating rules
- Do not reformat or refactor code automatically.
- Prefer **existing patterns** over external best practices.
- If multiple styles exist, document the dominant one and flag inconsistencies.

## Style dimensions to infer
- Naming (files, types, functions, variables)
- Formatting (indentation, line length, braces)
- Error handling patterns
- Logging patterns
- File and folder organization
- Test structure and naming

## Output: `.ace/style_contract.md`
Capture:
- Formatting rules actually used
- Naming conventions actually used
- Error/logging patterns actually used
- Explicit “do not introduce” patterns

Keep this concise and repo-specific.

## Output: `.ace/style_check.md`

### Style Check Report

## Verdict
- PASS | FAIL

## Blocking violations (must fix)
1. <violation>
   - Evidence: <file:line or diff excerpt>
   - Required fix: <specific change>

## Warnings (should fix)
1. ...

## Notes
- Any ambiguity or mixed conventions detected
