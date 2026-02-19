# Full-Stack Testing Best Practices (Current)

## Source-backed principles
- Keep most tests at lower levels (unit/component/integration), and reserve e2e for critical journeys and true system confidence gaps.
- Choose test level by confidence need: smallest scope that can prove the behavior.
- Treat requirements and user stories as the test basis; derive test conditions and prioritize with risk.
- Maintain bidirectional traceability between requirements and tests.
- Use e2e reliability practices: isolation, resilient locators, retries in CI, and diagnostics artifacts.

## Practical level-selection heuristic
1. Start with unit.
2. Move to integration if behavior crosses a boundary (DB, service, contract, framework wiring).
3. Move to e2e only if user-journey/system confidence is still unresolved.

## Documentation expectations
- Keep a requirement-to-test mapping (table or CSV).
- Include risk and rationale per planned test.
- Track deferred coverage and ownership.
- Keep naming behavior-oriented (`when_<context>_then_<outcome>` style).

## Quality gates beyond raw line coverage
- Critical-path pass rate.
- Flake rate and retry debt.
- Defect escapes by area.
- Requirements/risk coverage completeness.
- Coverage dimensions that matter for the code shape (branch/function/condition where relevant).

## Primary references
- Cypress Testing Strategy: https://docs.cypress.io/app/core-concepts/testing-strategy (last updated Jan 16, 2025)
- Cypress FAQ: https://docs.cypress.io/app/faq (last updated Jan 14, 2025)
- Cypress Code Coverage: https://docs.cypress.io/app/tooling/code-coverage (last updated Jan 14, 2025)
- Playwright Best Practices: https://playwright.dev/docs/best-practices (current docs, v1.56 nav)
- Playwright CI: https://playwright.dev/docs/ci (current docs, v1.56 nav)
- Testing Library Guiding Principles: https://testing-library.com/docs/guiding-principles
- ISTQB CTFL v4.0: https://www.istqb.org/certifications/certified-tester-foundation-level
- ISTQB ISO standards overview (29119 references): https://www.istqb.org/iso-standards/
- Cucumber Gherkin Reference: https://cucumber.io/docs/gherkin/reference
