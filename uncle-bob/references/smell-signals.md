# Smell Signals

Use this file as the evidence rubric for smell detection and refactor suggestions.

## Evidence-first principle
- Prefer objective signals (complexity, duplication, dependency direction, change-coupling hints) over taste.
- Treat static analyzer findings as hints; confirm in code before recommending refactor.
- Do not escalate to architecture-level refactors unless local changes cannot reduce risk.

## Core smell categories

### 1) Bloaters
Signals:
- Long methods/functions with multiple abstraction levels.
- Large classes/modules that aggregate unrelated responsibilities.
- Long parameter lists and data clumps.
Typical risks:
- High defect probability during edits.
- Slow onboarding and difficult testing.
Refactor patterns:
- Extract function/method.
- Extract class/module.
- Introduce parameter object.

### 2) Object-orientation and data design smells
Signals:
- Primitive obsession (raw strings/ints used where domain types should exist).
- Feature envy (a method mostly manipulates another object's data).
- Data classes/anemic models with behavior spread elsewhere.
Typical risks:
- Weak invariants and duplicated validation logic.
- Leaky boundaries across modules.
Refactor patterns:
- Replace primitive with domain object/value object.
- Move method/behavior to owning type.
- Encapsulate record and enforce invariants.

### 3) Change-preventers
Signals:
- Shotgun surgery: one change requires edits across many files.
- Divergent change: one module changes for unrelated reasons.
- Parallel inheritance hierarchies.
Typical risks:
- Change amplification and frequent regressions.
- Hard-to-plan releases.
Refactor patterns:
- Extract cohesive seams.
- Consolidate variation points behind interfaces.
- Collapse unnecessary hierarchies.

### 4) Couplers and dependency smells
Signals:
- Tight runtime coupling between layers.
- Message chains and train-wreck calls.
- Temporal coupling (operations must occur in hidden order).
Typical risks:
- Fragile integration behavior and order-dependent bugs.
- Poor test isolation.
Refactor patterns:
- Introduce explicit orchestration boundary.
- Hide navigation behind intention-revealing methods.
- Introduce lifecycle/state guards.

### 5) Conditional complexity
Signals:
- Deeply nested conditionals and switch trees.
- Repeated condition blocks across call sites.
- Boolean parameter flags controlling behavior modes.
Typical risks:
- Missing edge-case coverage.
- Inconsistent behavior across paths.
Refactor patterns:
- Replace conditional with polymorphism/strategy.
- Introduce guard clauses.
- Split mode-specific paths into explicit collaborators.

## Tool-aligned heuristics

### Sonar maintainability/code smell signals
- Use code smell issues to prioritize maintainability hotspots.
- Combine issue density with module criticality before recommending refactor.
Reference:
- https://docs.sonarsource.com/sonarqube-server/user-guide/rules/overview/

### PMD design rules
- Use PMD design categories as language-level detectors for complexity and design risk.
- Focus on repeated rule hits in the same module rather than single isolated alerts.
Reference:
- https://pmd.github.io/latest/pmd_rules_java_design.html

### ESLint complexity rule (JS/TS)
- Treat elevated cyclomatic complexity as a smell candidate, not an automatic defect.
- Escalate when high complexity coexists with duplication or poor naming.
Reference:
- https://eslint.org/docs/latest/rules/complexity

## Reporting standard
- Always include location and concrete evidence.
- Keep refactors minimal and behavior-preserving by default.
- Pair each medium/high-risk suggestion with pre-refactor tests.

## Source grounding
- Martin Fowler, "Code Smell" and refactoring catalog:
  - https://martinfowler.com/bliki/CodeSmell.html
  - https://refactoring.com/catalog/
- Refactoring Guru smell taxonomy:
  - https://refactoring.guru/refactoring/smells
