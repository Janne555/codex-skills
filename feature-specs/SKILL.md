---
name: feature-specs
description: Create or update durable feature specifications/PRDs and lightweight design docs that live in a repo’s docs/specs folder, maintaining a docs/specs/_index.md index. Use when asked to design a new feature, write a PRD/spec, edit an existing spec, or produce consistent feature documentation that should be kept as a long‑lived artifact.
---

# Feature Specs

## Overview

Create or update permanent feature specs/PRDs and lightweight design docs stored in `docs/specs/`, with a consistent structure and a maintained `docs/specs/_index.md`. When editing, replace the spec body with the new version and append a change-log entry explaining what changed and why.

## Feature definition (soft)

Treat a “feature” as any product change that benefits from a durable spec and measurable outcomes (UI/UX changes, backend capabilities, policy or workflow changes). This is guidance, not a gate.

## Workflow

### 0) Interrogate the problem before committing

Be politely skeptical. Ask clarifying questions that pressure-test the idea, align on outcomes, and reduce scope risk. Do this before drafting or updating the spec. Aim for 3–6 targeted questions, focusing on:

- The real problem and why it matters now
- Who it affects and how success is measured
- Constraints, risks, and what could go wrong
- What can be excluded or deferred
- Evidence or assumptions that must be tested

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
- Goals vs non-goals
- Proposed solution and UX notes
- NFRs (security, privacy, accessibility, performance)
- Risks, dependencies, alternatives, and open questions
- Success metrics + rollout plan
- Acceptance criteria that are testable

### 4) Update the index

Load `references/index-template.md`. Add or update the row for the feature with:

- Feature name (matches file name)
- Status (Draft, In Review, Approved, Deprecated)
- Owner
- Last updated (YYYY-MM-DD)
- One‑sentence summary

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
- Keep writing direct, structured, and scannable.

## References

- `references/spec-template.md` — canonical spec structure
- `references/index-template.md` — index table format
