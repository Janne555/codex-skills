---
name: a11y-review
description: Review UI changes for accessibility issues using WCAG-oriented heuristics. Produces actionable findings and test suggestions.
---

# Accessibility (a11y) Review

## Purpose
Evaluate UI changes for accessibility risks and violations, focusing on real user impact and practical fixes.

## When to use
- Any UI/UX change
- Forms, navigation, dialogs, dynamic content

## Inputs (read)
- `.ace/ACE.md`
- UI code / templates / components
- `git diff`
- Optional: screenshots or flow descriptions

## Outputs (write)
- `.ace/a11y_review.md`

## Evaluation dimensions
- Semantic structure (headings, landmarks)
- Keyboard navigation and focus order
- Focus visibility and management
- Form labels, errors, and help text
- ARIA usage (only when necessary)
- Color contrast assumptions
- Dynamic content announcements

## Rules
- Prefer semantic HTML over ARIA.
- Do not invent new UI requirements.
- Flag missing test coverage for a11y-critical behavior.

## Output: `.ace/a11y_review.md`

### Accessibility Review

## Verdict
- PASS | FAIL

## Blocking issues (must fix)
1. <issue>
   - Location: <component/file>
   - Impacted users: <screen reader / keyboard / low vision>
   - Fix: <specific change>

## Non-blocking issues (should fix)
1. ...

## Test recommendations
- <e.g. keyboard-only navigation test>
- <e.g. screen reader smoke test>

## Notes
- Assumptions made
- Areas not covered

