---
name: bug-recorder
description: Record bug reports through a repeatable intake workflow. Use when the user wants the agent to enter a bug-reporting mode, wait for one report at a time, decide whether the report contains enough detail to fix or investigate, ask only the missing questions, and then record the bug using the storage method or artifact format the user wants.
---

# Bug Recorder

## Goals
- Switch into bug-intake mode immediately.
- Decide whether each report is actionable for debugging or fixing.
- Ask only the missing questions needed to make the report usable.
- Record the bug in the format and location the user wants.
- After recording, prompt for the next bug unless the user changes mode.

## Default stance
- Treat the workflow as serial: one bug at a time.
- Do not turn the interaction into a broad planning exercise.
- Do not assume one storage method. Follow the user's chosen recording method.
- Preserve uncertainty. Keep hypotheses labeled as hypotheses until verified.

## Intake workflow
1. Enter intake mode and wait for a bug report.
2. Read the report as an implementer: is there enough detail to begin reproducing, tracing, or fixing it?
3. Check for the minimum actionable context:
   - observed problem
   - expected behavior
   - affected area or surface
   - reproduction steps, trigger conditions, or concrete example
   - relevant environment, role, or scope if it changes the behavior
4. Ask only the missing questions that block meaningful follow-up. Prefer short, concrete questions. Keep the count low.
5. Once the report is actionable, record it using the user's requested method.
6. Confirm the recorded result briefly and prompt for the next bug.

## Sufficiency rule
A report is sufficient when a competent engineer could start the next real step without guessing at the core problem.

Usually sufficient:
- concrete symptom plus affected surface
- at least one reproduction path, example, or trigger condition
- expected behavior or why the current behavior is wrong

Usually not sufficient:
- only a vague complaint with no surface or symptom
- only a hypothesis about the cause
- no clue which user, role, page, endpoint, job, or flow is affected when that changes behavior

## Clarifying-question rules
- Ask for missing facts, not speculative architecture discussions.
- Prefer questions that unlock debugging immediately.
- If the user already gave enough detail, do not ask filler questions.
- If several details are missing, ask the smallest useful batch first.
- If the user wants rapid intake, capture the bug with explicit gaps rather than blocking on non-critical details.

## Recording rules
- Use the storage location, structure, and wording style the user requested.
- If the method is not yet specified, ask where or how the user wants bugs recorded before creating artifacts.
- Record facts, reproduction details, impact, and open questions separately when useful.
- Keep unverified causes under a clear label such as `Hypotheses` or `Suspected cause`.
- Do not silently normalize away important wording from the user's report if it changes meaning.

## Suggested entry shape
Use the target format the user requested, but preserve these fields when possible:

```md
Title: <short bug name>
Status: reported
Observed: <what is happening>
Expected: <what should happen>
Surface: <page, flow, endpoint, job, role, env, or system area>
Reproduction: <steps, trigger, example, or evidence>
Impact: <why it matters>
Open questions: <only unresolved blockers or useful follow-ups>
Hypotheses: <optional; clearly marked as unverified>
```

## Mode boundaries
- Stay in intake/recording mode until the user asks to fix, triage, prioritize, or investigate.
- When the user switches from recording to implementation, use the recorded bug as source material rather than re-interviewing them from scratch.
