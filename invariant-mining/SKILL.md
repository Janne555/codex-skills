---
name: invariant-mining
description: Mine likely program invariants from tests, traces, logs, or runtime observations to capture behavioral constraints. Use when establishing baseline behavior (research) or validating changes (verify).
---

# Invariant Mining

## Purpose
Infer likely invariants (preconditions, postconditions, state relationships, range constraints) from runtime evidence to document behavioral constraints and detect unexpected shifts.

## Inputs (read)
- Tests and test outputs
- Runtime traces, logs, or telemetry samples
- Repro steps and scenarios
- `.ace/TASK.md` when present (user-authored; never edit)
- `.ace/ACE.md` for canonical constraints and current phase

## Outputs (write)
- `.ace/invariants.md`: inferred invariants, sources, and confidence

## Operating rules
- Do not change code or tests.
- Prefer existing tests and traces; do not invent data.
- State confidence and evidence sources for each invariant.
- Flag invariants that appear unstable or environment-dependent.

## Workflow
1. Identify available runtime evidence (tests, traces, logs) and document sources.
2. Select scenarios that represent the target behavior.
3. Infer candidate invariants (inputs/outputs, state transitions, ranges, relations).
4. Group invariants by subsystem or data flow.
5. Note gaps, weak evidence, and questions for the team.
6. Write `.ace/invariants.md` and update `.ace/ACE.md` with key findings and risks.

## Output format: `.ace/invariants.md`

# Invariants

## Evidence sources
- <tests/traces/logs used>

## Inferred invariants
1. <invariant>
   - Scope: <module/flow>
   - Evidence: <tests/traces/logs>
   - Confidence: low | medium | high

## Anomalies / unstable candidates
- <potentially unstable invariant + why>

## Gaps / questions
- <what additional evidence is needed>
