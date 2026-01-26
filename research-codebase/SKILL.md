---
name: research-codebase
description: Research the codebase around a change, map current behavior end-to-end, and capture risks before planning.
---

## When to use
Use when you need to investigate a problem or feature request before proposing a solution.

## Role
ROLE: Research. Act as a senior engineer gathering and structuring information. Do not write code or make irreversible decisions.

Allowed:
- Explore unknowns and identify constraints.
- Surface questions and risks.

Forbidden:
- Writing implementation code.
- Committing to scope changes or final decisions.

Stop when:
- Unknowns are enumerated and sources identified.

## Inputs
- Problem or feature description
- Relevant issue/ticket text
- Recent stack traces or logs (if applicable)
- Initial file or symbol hints (if any)
- `.ace/TASK.md` when present (user-authored; never edit)
- `.ace/ACE.md` for canonical constraints and current phase

Precedence rules (when conflicts exist): `ACE.md` > `TASK.md` > `plan.md` > `research.md`.
Artifact location: write all outputs to `.ace/` and only update relevant sections in `.ace/ACE.md`.

## Objectives
1. Map the relevant parts of the codebase.
2. Explain current behavior end-to-end.
3. Identify plausible change points and risks.
4. Prepare material for the planning phase.
5. Update `.ace/ACE.md` with findings summary, open questions, and candidate constraints.

## Steps
1. Skim the provided files and references.
2. Identify key modules, entrypoints, data flows, types, interfaces, invariants, and external dependencies.
3. Infer constraints (performance, scaling, backwards compatibility, security/privacy).
4. List open questions and missing information to ask humans.
5. Write any research question depends on external documentation, refer to the [External-docs rule](<SKILL#External-docs rule>)
6. Write findings to `.ace/research.md` and update `.ace/ACE.md` (phase = Research).

## Output format
Produce `.ace/research.md` with:
1. **Summary**: 2–4 sentences on the problem and relevant code areas.
2. **Relevant Files and Responsibilities**: bullet list of paths with one-line descriptions.
3. **Current Behavior**: step-by-step description of current behavior for this case.
4. **Candidate Change Points**: bullets of files/functions to modify and why.
5. **Constraints and Risks**: bullets of compat/perf/coupling considerations.
6. **Open Questions**: questions for the team before implementing.

## External-docs rule
1) Create or update `.ace/doc_scout_questions.md` with a numbered list of questions.
2) Each question must include brief context: relevant library/tool name, version (if known), target environment, and what decision the answer will affect.
3) Update `ACE.md` under "Open questions / risks" noting that doc-scout is required.
4) STOP. Do not guess; do not proceed to planning until doc-scout answers are available.

