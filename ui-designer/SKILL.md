---
name: ui-designer
description: Evaluate existing user interfaces and design new UI concepts using evidence-based usability, accessibility, and responsive-design principles. Use when Codex must audit a UI, suggest prioritized UX/UI improvements, or produce a new screen/layout direction with rationale and implementation-ready guidance.
---

# UI Designer

## Purpose
Assess and improve an existing UI, or design a new UI direction that is clear, usable, accessible, and responsive.

## Inputs (read)
- Product goal and primary user tasks
- Target platforms (web, iOS, Android, desktop)
- Existing UI artifacts: screenshots, live pages, component code, flows
- Constraints: brand, engineering limits, deadlines, regulatory/accessibility requirements

## Outputs (write)
- `.ace/ui_design_review.md` for existing-UI audits
- `.ace/ui_design_spec.md` for new UI directions

## Workflow
1. Clarify scope and success criteria.
2. Pick mode:
- `Audit mode` for improving an existing interface.
- `Design mode` for creating a new UI direction.
3. Read `references/ui-best-practices.md` and apply only relevant sections.
4. Produce prioritized recommendations tied to user impact and effort.
5. Include test suggestions that validate the recommendations.

## Audit mode
1. Identify top user journeys and key screens.
2. Evaluate against:
- Task clarity and information hierarchy
- Navigation/findability
- Feedback and system status visibility
- Error prevention and recovery
- Accessibility basics (contrast, focus, labels, target size)
- Responsive behavior across viewport sizes
3. List findings as:
- `Critical`: blocks task completion or accessibility
- `Major`: causes friction or confusion
- `Minor`: polish/consistency issue
4. For each finding, provide:
- Evidence (screen/component + observed issue)
- Recommendation (specific change)
- Rationale (usability principle)
- Validation method (what to test)

## Design mode
1. Define primary user, top tasks, and context of use.
2. Propose structure:
- Page/screen regions
- Content hierarchy
- Primary and secondary actions
3. Specify interaction states:
- Default, hover/focus/pressed, loading, empty, error, success
4. Bake in accessibility and responsiveness from the start.
5. Deliver a concise spec with:
- Layout description
- Component behavior notes
- Copy and microcopy guidance
- Acceptance checks

## Output template: `.ace/ui_design_review.md`

### UI Review

## Scope
- Screens/flows reviewed
- Assumptions

## Findings
1. [Critical|Major|Minor] <title>
- Evidence: <where/what>
- Recommendation: <specific change>
- Why: <principle>
- Validate: <test>

## Quick wins
- <high-impact, low-effort changes>

## Risks and gaps
- <unknowns or missing artifacts>

## Output template: `.ace/ui_design_spec.md`

### UI Design Spec

## Goal
- <product outcome>

## User and tasks
- Primary user: <persona>
- Top tasks: <task list>

## Screen structure
- <layout and hierarchy>

## Interaction model
- <primary actions, secondary actions, state changes>

## Accessibility and responsive rules
- <non-negotiable requirements>

## Acceptance checks
- <observable pass/fail checks>
