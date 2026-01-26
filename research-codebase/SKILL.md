---
name: research-codebase
description: Research the codebase around a change, map current behavior end-to-end, and capture risks before planning.
---

## When to use
Use when you need to investigate a problem or feature request before proposing a solution.

## Role
Act as a senior engineer gathering and structuring information. Do not write code yet.

## Inputs
- Problem or feature description
- Relevant issue/ticket text
- Recent stack traces or logs (if applicable)
- Initial file or symbol hints (if any)

## Objectives
1. Map the relevant parts of the codebase.
2. Explain current behavior end-to-end.
3. Identify plausible change points and risks.
4. Prepare material for the planning phase.

## Steps
1. Skim the provided files and references.
2. Identify key modules, entrypoints, data flows, types, interfaces, invariants, and external dependencies.
3. Infer constraints (performance, scaling, backwards compatibility, security/privacy).
4. List open questions and missing information to ask humans.

## Output format
Produce a markdown doc with:
1. **Summary**: 2–4 sentences on the problem and relevant code areas.
2. **Relevant Files and Responsibilities**: bullet list of paths with one-line descriptions.
3. **Current Behavior**: step-by-step description of current behavior for this case.
4. **Candidate Change Points**: bullets of files/functions to modify and why.
5. **Constraints and Risks**: bullets of compat/perf/coupling considerations.
6. **Open Questions**: questions for the team before implementing.
