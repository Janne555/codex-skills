---
name: plan-change
description: Turn researched problems into concrete, testable implementation plans without writing code.
---

## When to use
After research is complete and you need a concrete plan for a code change.

## Role
ROLE: Plan. Act as a senior engineer designing the change. Do not write final code; focus on solution design and testing approach.

Allowed:
- Produce an executable plan aligned to `.ace/ACE.md`.
- Define acceptance criteria and risks.

Forbidden:
- Writing implementation code.
- Expanding scope beyond `.ace/ACE.md` and `.ace/TASK.md`.

Stop when:
- The plan is executable and reviewed.

## Inputs
- Problem/feature description
- Research document from `.ace/research.md` (from research-codebase). Always re-read the research document from file as the developer might have made changes to it.
- Non-functional requirements (performance, security, compatibility, etc.)
- `.ace/ACE.md` for canonical constraints and current phase
- `.ace/TASK.md` for original intent (user-authored; never edit)

Precedence rules (when conflicts exist): `ACE.md` > `TASK.md` > `plan.md` > `research.md`.
Artifact location: write all outputs to `.ace/` and only update relevant sections in `.ace/ACE.md`.

## Objectives
1. Define the desired behavior precisely.
2. Specify the minimal, coherent code changes.
3. Design tests and validation steps.
4. Produce a plan another agent can implement directly.
5. Update `.ace/ACE.md` with decisions, acceptance criteria, and plan summary (phase = Implementation ready).

## Steps
1. Clarify desired behavior (inputs, outputs, edge cases, error handling).
2. Propose solution approach: modules/functions to modify, new types/interfaces/configuration.
3. Break work into incremental, testable steps.
4. Specify tests: unit and integration/end-to-end as relevant.
5. Call out migration/rollout considerations (flags, config, data migrations).
6. Write the plan to `.ace/plan.md` and update `.ace/ACE.md`.

## Output format
Provide `.ace/plan.md` with:
1. **Planned Behavior**: plain-language description plus edge cases and expected handling.
2. **Change Set Overview**: files to change and what will change.
3. **Implementation Steps**: ordered, numbered steps that are small and testable.
4. **Tests**: unit test cases (given/when/then) and integration scenarios with expected outcomes.
5. **Rollout / Risk Notes**: potential failure modes, monitoring/metrics, flags/config strategy.
