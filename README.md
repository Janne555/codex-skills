# Skills README

This repository contains Codex skills. Each skill is a focused playbook stored in `/<skill-name>/SKILL.md`.
Skills define when to use them, required inputs/outputs, and the expected workflow.

## How humans should use these skills
- Choose the skill that best matches the task intent (research, plan, implement, review, etc.).
- Open the skill’s `SKILL.md` before acting; follow its workflow and rules.
- Use only the inputs/outputs specified by the skill unless the user requests otherwise.
- Treat skills as task-scoped guidance: do not apply them across unrelated tasks.
- If multiple skills apply, use the minimal set and state the order.

## Skills list

- a11y-review — Accessibility review of UI changes using WCAG-oriented heuristics.
- ace — End-to-end coordinator across research, planning, and implementation.
- doc-scout — Research official documentation and produce a source-backed answer pack.
- feature-specs — Create/update durable feature specs that describe desired system state.
- implement-change — Implement a pre-approved plan with focused edits and tests.
- infosec-audit — Adversarial security analysis without automatic fixes.
- invariant-mining — Identify program invariants from static/runtime evidence.
- plan-change — Turn researched problems into a concrete implementation plan.
- plan-linter — Lint `.ace/plan.md` for readiness and alignment with `.ace/ACE.md`.
- refactor-smells — Identify code smells and propose safe refactors.
- research-codebase — Map current behavior and risks before planning.
- spec-linter — Lint feature specs for completeness, focus, and index alignment.
- style-enforcer — Enforce repository coding style and conventions.

## Notes
- Skills are designed to be durable guidance. If a skill’s intent changes, update its `SKILL.md` and any referenced templates.
- Some skills read/write files in `.ace/` or `docs/specs/`. Follow each skill’s Input/Output rules.
