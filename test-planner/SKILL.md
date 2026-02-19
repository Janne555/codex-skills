---
name: test-planner
description: Plan a behavior-focused, risk-based full-stack test suite and choose between unit, integration, and end-to-end tests using specs and user stories as the test basis. Use when defining or refining test strategy, deriving tests from requirements, mapping acceptance criteria to test levels, setting quality gates, or building test traceability documentation.
---

# Test Planner

## Goals
- Produce an effective test suite plan that balances unit, integration, and e2e tests.
- Derive tests directly from specifications and user stories.
- Preserve bidirectional traceability between requirements and planned tests.

## Inputs
- Product specs, user stories, and acceptance criteria.
- Architecture context (services, boundaries, external dependencies).
- Risk context (business impact, likelihood, change frequency).

If inputs are missing, ask only for the minimum needed details before planning.

## Outputs
- `.ace/test-plan.md` (required): suite strategy, selected tests, and rationale.
- `.ace/test-traceability.csv` (optional): requirement-to-test mapping for auditability.

## Workflow
1. Build the test basis.
- Parse specs and stories into atomic behaviors.
- Assign stable IDs (`STORY-<n>`, `AC-<n>`, or existing IDs).

2. Score risk per behavior.
- Use: impact, likelihood, user reach, and change volatility.
- Classify each behavior as `high`, `medium`, or `low` risk.

3. Choose the lowest effective test level per behavior.
- Start at `unit`.
- Escalate to `integration` when behavior depends on module/service boundaries, persistence, contracts, or framework wiring.
- Escalate to `e2e` only when confidence requires real user flows across the deployed stack.
- Avoid duplicating deep assertions at e2e level.

4. Define the suite shape.
- Keep most cases in unit/integration.
- Keep e2e to critical-path journeys, cross-cutting regressions, and release blockers.
- Mark each planned test as `happy-path`, `edge-case`, or `failure-mode`.

5. Add execution and CI strategy.
- Tag tests by level and criticality.
- Define required gates (for example: unit+integration on every PR; critical e2e on merge/deploy).
- Define anti-flake measures for e2e (isolation, resilient locators, retries on CI only, diagnostics on failure).

6. Build traceability artifacts.
- Map each requirement/acceptance criterion to at least one planned test.
- Record fields: requirement ID, behavior, risk, level, rationale, owner, and status.

7. Run quality checks on the plan.
- Flag over-reliance on e2e.
- Flag untested high-risk behaviors.
- Flag tests without a source requirement.

## Decision Rules
- Prefer `unit` for deterministic domain logic and branch-heavy behavior.
- Prefer `integration` for API contracts, data access, queues/events, and framework composition.
- Prefer `e2e` for authentication, checkout/payment, permissions, and other business-critical user journeys.
- If uncertain, choose the lower level first and justify escalation explicitly.

## Required `test-plan.md` structure
```markdown
# Test Plan

## Scope
- In scope:
- Out of scope:

## Test Basis
- Specs:
- User stories:
- Acceptance criteria:

## Risk Model
- Scoring method:
- High-risk behaviors:

## Planned Test Suite
| Behavior ID | Requirement ID | Risk | Level | Test intent | Rationale |
|---|---|---|---|---|---|

## CI Gates
- PR:
- Merge:
- Release:

## Traceability Notes
- Coverage gaps:
- Deferred tests:
```

## Optional `test-traceability.csv` columns
`requirement_id,behavior_id,risk,test_level,test_name,owner,status,notes`

## Reference usage
- Read `references/testing-best-practices.md` when selecting levels, setting e2e limits, or defining documentation rules.
