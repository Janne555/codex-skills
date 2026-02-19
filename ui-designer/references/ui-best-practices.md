# UI Best Practices (Source-Backed)

Last reviewed: 2026-02-12

## 1) Start from user needs and task outcomes
- Prioritize real user goals over internal organization.
- Make the next step obvious at each point in a flow.
- Reduce steps and cognitive load for common tasks.

Sources:
- GOV.UK Design Principles: https://www.gov.uk/guidance/government-design-principles
- NN/g Usability Heuristics (match between system and real world, user control): https://www.nngroup.com/articles/ten-usability-heuristics/

## 2) Preserve clarity through strong hierarchy and consistency
- Use clear visual hierarchy so users can scan and decide quickly.
- Keep navigation, labels, and interaction patterns consistent.
- Show system status promptly after user actions.

Sources:
- NN/g Usability Heuristics (consistency and standards, visibility of system status): https://www.nngroup.com/articles/ten-usability-heuristics/
- web.dev Design and UX guidance: https://web.dev/learn/design/

## 3) Design for accessibility as a baseline requirement
- Meet WCAG principles (Perceivable, Operable, Understandable, Robust).
- Enforce contrast minimums for text (4.5:1 normal, 3:1 large).
- Ensure keyboard access and visible focus.
- Keep touch targets large enough; WCAG 2.2 target-size criterion sets a 24x24 CSS px minimum with exceptions.

Sources:
- WCAG Overview / principles: https://www.w3.org/WAI/standards-guidelines/wcag/
- WCAG 2.2 Quick Reference (contrast, focus, target size): https://www.w3.org/WAI/WCAG22/quickref/
- Android accessibility principles (labels, touch target sizing, color contrast): https://developer.android.com/guide/topics/ui/accessibility/principles

## 4) Treat responsive behavior as core functionality
- Design from smallest viewport constraints upward.
- Prevent horizontal overflow and broken layouts at common breakpoints.
- Verify readable line length, spacing, and control sizes on mobile.

Sources:
- Responsive design basics (fluid layout, media queries, viewport): https://web.dev/articles/responsive-web-design-basics

## 5) Build trust with error prevention and recovery
- Prevent common input errors with constraints and clear affordances.
- Use plain-language errors that explain cause and next action.
- Preserve user input when errors happen.

Sources:
- NN/g Usability Heuristics (error prevention, error recovery): https://www.nngroup.com/articles/ten-usability-heuristics/

## Practical review checklist
Use this when auditing a UI quickly:
- Can a new user identify the primary action within 5 seconds?
- Is system status visible after every important action?
- Are labels and navigation consistent across screens?
- Can every key path be completed by keyboard?
- Do text/background combinations appear to meet WCAG contrast?
- Are targets comfortably tappable on mobile?
- Does layout remain usable at narrow widths?
- Are errors clear, specific, and recoverable?
