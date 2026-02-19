---
name: feature-specs
description: Create or update durable feature specifications that describe the desired system state (not implementation tasks), stored in a repo’s docs/specs folder with a maintained docs/specs/_index.md. Use when asked to define or revise what a system should be like.
---

# Feature Specs

## Overview

Create or update durable feature specs stored in `docs/specs/`, with a consistent structure and a maintained `docs/specs/_index.md`. The spec describes the desired system state and behavior, not the work needed to align the system to it. When editing, replace the spec body with the new version and append a change-log entry explaining what changed and why.

## Feature definition (soft)

Treat a “feature” as any product change that benefits from a durable description of the desired system state (UI/UX changes, backend capabilities, policy or workflow changes). This is guidance, not a gate.

## Workflow

### 0) Clarify the desired system before committing

Be politely skeptical. Ask clarifying questions that pressure-test the idea, align on the target system state, and reduce scope risk. Do this before drafting or updating the spec. Aim for 3–6 targeted questions, focusing on:

- The real problem and why it matters now
- Who it affects and what the system should enable for them
- Key behaviors, constraints, and what “good” looks like
- What can be excluded or deferred
- Assumptions and unknowns that should be tracked

If the user’s request is urgent, still ask at least 2 questions and proceed with reasonable assumptions, clearly marking them in the spec.

### 1) Confirm scope and location

- Default location: `docs/specs/`
- Default index: `docs/specs/_index.md`
- File name: `<feature-name>.md` (slugified if needed)
- If the repo uses a different path or naming convention, ask before writing.

### 2) Decide create vs update

- **Create new spec** when no file exists for the feature.
- **Update existing spec** when a file exists or the user explicitly asks to edit.

### 3) Draft the spec using the template

Load `references/spec-template.md` and fill every section that applies. Keep it concise but complete. Prioritize:

- Problem/opportunity clarity
- Goals vs non-goals (desired outcomes, not test criteria)
- Target system behavior and user experience
- NFRs (security, privacy, accessibility, performance)
- Risks, dependencies, alternatives, and open questions

Do not include implementation tasks, rollout plans, or acceptance criteria. If the user requests alignment or verification, direct that to a task definition.

Functional requirements describe what the system must do (capabilities/behaviors). Non-functional requirements (quality attributes) describe how well it must do it or constraints on those behaviors (performance, reliability, security, privacy, accessibility, etc.).
Include user stories/scenarios when they help capture expected behavior from the user’s point of view; omit them for purely internal capabilities.
Frontmatter `implemented_version` should reflect the latest spec revision date that is actually implemented in the system. If not yet implemented, leave it as `YYYY-MM-DD` or set to `N/A`.

### 4) Update the index (discoverability-first)

Load `references/index-template.md`. Treat `docs/specs/_index.md` as a routing layer that helps agents decide whether to read a long spec.

Add or update the row for the feature with:

- Feature name (matches file name)
- Status (Draft, In Review, Approved, Deprecated)
- Owner
- Last updated (YYYY-MM-DD)
- Problem (1 sentence): what pain/opportunity this spec addresses
- In scope (1 sentence): highest-value behaviors included
- Out of scope (1 sentence): explicit exclusions to prevent context overreach
- Keywords: 4-8 stable search terms (nouns/phrases, comma-separated)
- Read if...: 1 sentence describing when an agent should include this spec in context
- Summary (1 sentence): concise overall description

Index writing constraints:

- Keep each cell short and scannable; avoid multi-sentence cells except `Read if...`.
- Prefer stable terminology over project slang so search/retrieval is reliable.
- Update index metadata whenever the spec meaning changes, not only when the date changes.
- If uncertain between two labels/tags, choose the one future readers are more likely to search.

### 5) Update the change log (required)

At the bottom of the spec, ensure a **Change log** section exists. Append a new entry:

`YYYY-MM-DD — Author — Summary of changes — Rationale`

If the file is new, create the change log and add an initial entry like:
`YYYY-MM-DD — Author — Initial draft — Created`

## Editing Rules

- Overwrite the main spec content with the new version.
- Preserve the **Change log** section and append a new entry.
- If content conflicts with prior versions, resolve in the main body and document the decision in the change log.

## Output Expectations

- Produce the spec file in `docs/specs/<feature-name>.md`.
- Update `docs/specs/_index.md`.
- Ensure `_index.md` is useful for pre-read triage of long specs.
- Keep writing direct, structured, and scannable.

## References

- `references/spec-template.md` — canonical spec structure
- `references/index-template.md` — index table format
