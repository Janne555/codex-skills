---
name: uncle-bob
description: Find maintainability and design code smells, explain why they matter, and propose small behavior-preserving refactors with risk and test guidance. Use when a user asks for code quality review, design issue identification, refactor opportunities, or "what bad code looks like" analysis.
---

# Uncle Bob: Code Smell and Refactor Review

## Purpose
Identify code smells and design issues, then recommend targeted refactors that improve structure without changing behavior.

## Inputs (read)
- User request and constraints
- Relevant source files or `git diff`
- Existing tests and linters (if available)

## Outputs (write)
- Primary: concise findings in the response
- Optional file output when requested: `.ace/uncle_bob_review.md`

## Rules
- Do not apply refactors automatically unless explicitly asked.
- Prefer evidence-backed findings over stylistic opinions.
- Prioritize behavior-preserving, local changes.
- State uncertainty when evidence is weak.
- Require test guidance for every medium/high-risk recommendation.

## Workflow
1. Define review scope
- Determine whether to review a diff, module, or full subsystem.
- Identify business-critical code paths to avoid unsafe advice.

2. Gather objective signals
- Check for duplicated logic, large functions/classes, deep nesting, and dense conditionals.
- Use available static analysis output (for example PMD, Sonar, ESLint) when present.
- Capture concrete evidence (file + line) for each candidate smell.

3. Classify smells
- Map each finding to a smell category from `references/smell-signals.md`.
- Distinguish design problems (coupling, abstraction leaks, temporal coupling) from local readability issues.

4. Assess risk and impact
- Estimate severity: low, medium, high.
- Describe likely maintenance failure mode (defect risk, change amplification, test fragility).
- Note if change should be deferred due to high blast radius.

5. Propose minimal refactors
- Recommend the smallest coherent change sequence.
- Keep each step independently testable and reversible.
- Call out pre-refactor tests needed to lock behavior.

6. Report clearly
- Order findings by severity.
- Include location, evidence, smell type, refactor suggestion, and test impact.

## Output template
For each finding:

### Smell: <name>
- **Location**: <file:line>
- **Evidence**: <objective signal(s)>
- **Why it matters**: <maintenance/design risk>
- **Risk level**: low | medium | high
- **Minimal refactor**:
  - Step 1: ...
  - Step 2: ...
- **Test impact**:
  - Tests required before refactor: yes/no
  - Suggested tests: ...

## Smell catalog and evidence rules
Load and follow:
- `references/smell-signals.md`
