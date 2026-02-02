---
name: prometheus
description: Delegate skill use to a separate agent/context to avoid context pollution or when a workflow forbids using a skill directly. Use to draft a handoff request for another agent to run a specific skill and return results. Do not use recursively or to invoke prometheus itself.
---

# Prometheus

## CLI
Use the `prometheus` CLI to delegate to another agent.

Command shape:
```
prometheus <skill-name> "<prompt>"
```

Prompt augmentation:
- The prompt is prefixed with: `please use the $${skill} skill to `
- The prompt is suffixed with: ` You are in non-interactive mode. Please do not write any files.`

Optional output flag:
```
prometheus -o <filename> <skill-name> "<prompt>"
```

## Role
Act as a delegation broker. Prepare a clean, bounded request for another agent to run a specific skill and return only the needed results.

## Rules
- Do not invoke or reference this skill within its own delegation request.
- Do not run the target skill yourself.
- Use the `prometheus` CLI for delegation; do not call the target skill directly.
- Keep the handoff scoped: ask only for the minimum needed outputs.
- Avoid copying unnecessary context; include only what the other agent needs.
- If a target skill is missing or unavailable, say so and propose the next-best alternative.

## Inputs
- Target skill to delegate
- Reason for delegation
- Minimal context needed to execute the target skill
- Expected outputs and any formatting requirements

## Outputs
Produce a delegation request that includes:
1) Target skill name and reason for delegation
2) Minimal context package
3) Specific questions or tasks for the other agent
4) Required output format and any constraints

When execution is requested, run `prometheus` with the target skill and prompt. Prefer `-o <filename>` if the user wants the output captured to a file.

## Delegation template
```
Delegation request:
- Target skill: <skill-name>
- Reason: <why this must run in a separate agent/context>
- Context: <only the minimal facts, file paths, or snippets needed>
- Tasks/questions:
  - <task or question>
  - <task or question>
- Output format: <expected structure or file locations>
- Constraints: <time bounds, scope limits, or “no extra research”>
```
