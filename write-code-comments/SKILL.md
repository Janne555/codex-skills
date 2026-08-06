---
name: write-code-comments
description: Decide whether source code needs a comment, choose the right comment type, and write concise, durable content. Use when creating, editing, or reviewing code and considering inline comments, block comments, doc comments, TODOs, workaround notes, invariant or safety explanations, or lint and type-check suppressions. Do not use for pull request review comments or general prose documentation.
---

# Write Code Comments

Treat every comment as a maintenance liability that must earn its place. Add one only when it preserves useful information that the code, types, or names cannot express clearly enough.

## Inspect the Local Contract

Before deciding, inspect the repository instructions, language conventions, documentation tooling, and nearby code. Follow explicit requirements such as public-API documentation, safety comments, generated-file rules, or structured TODO syntax. Prefer the established local style when it conflicts with generic advice.

When editing code, also inspect adjacent comments. Update or remove comments made false, redundant, or misleading by the change.

## Follow the Decision Tree

Evaluate each candidate location independently:

1. **Is a comment required by a repository rule, language/tool contract, or user request?**
   - Yes: add the required comment in the prescribed form, then continue to the quality checks.
   - No: continue.
2. **Does a public or externally consumed interface need a documented contract?**
   - Yes: add an API or doc comment if nearby project practice does so.
   - No: continue.
3. **Would a competent future maintainer reasonably ask why this code exists, why the obvious approach is wrong, or what must remain true?**
   - Yes: continue.
   - No: do not add a comment.
4. **Can clearer naming, types, constants, control flow, or extraction convey the same information?**
   - Yes: improve the code first, then reevaluate from step 3.
   - No: continue.
5. **Is the information verified, specific, and likely to remain useful?**
   - Yes: choose a comment type and write it.
   - No: verify it, narrow it, or omit it. Never turn a guess into source-code folklore.

Do not add a comment merely because the code is complex. Complexity that can be removed should be removed; irreducible complexity should be explained at the smallest useful scope.

## Choose the Comment Type

### API or doc comment

Describe the caller-facing contract rather than narrating the implementation. Include only non-obvious parts of:

- purpose and intended use;
- preconditions and valid inputs;
- return value, errors, and exceptional behavior;
- side effects, ownership, lifecycle, or thread-safety;
- important limitations or a short example when usage is otherwise unclear.

Do not repeat names, parameter types, or facts already evident from the signature. Prefer tests or executable documentation for behavior that can drift.

### Rationale or design-constraint comment

Explain why the implementation takes a surprising path, which alternative was rejected, or which external constraint drives the choice. State the consequence of removing or changing it when that is not obvious.

Place the comment immediately above the decision it explains. Preserve the rationale, not the chronology of who changed it or when.

### Invariant, safety, or concurrency comment

State the exact condition that must remain true and the failure it prevents. Name the protected state, ordering rule, units, ownership boundary, security assumption, or unsafe-operation precondition as applicable.

Do not use vague warnings such as “important” or “be careful.” If the invariant can be asserted, typed, or tested, do that as well; the comment explains the reason and boundary.

### Workaround or compatibility comment

Identify:

- the affected dependency, platform, protocol, or version range;
- the observed constraint or failure;
- why this workaround is safe;
- the concrete removal condition;
- a durable issue or upstream link when useful.

Summarize the reason in the code. A bare ticket URL is not an explanation, and a ticket title may change or disappear.

### Suppression or tool-directive comment

Use the narrowest possible suppression. Explain why the warning is a false positive or why the normally preferred rule does not apply here. Do not merely restate “ignore this warning.”

### TODO or FIXME

Add one only for concrete unfinished work that belongs in the source and follows repository policy. State the missing outcome or triggering condition and include the required issue or owner reference. Avoid vague promises, speculative cleanup, and TODOs that duplicate tracked work without adding local context.

### Structural comment

Use a section or phase comment only when it materially helps navigation through a long algorithm or data declaration. Name the concept or phase, not the syntax below it. Prefer extracting a named function when that produces a clearer structure.

## Write the Smallest Sufficient Comment

Make the comment:

- local to the code it governs;
- about current truth rather than edit history;
- focused on one rationale, contract, or constraint;
- understandable without reconstructing the entire investigation;
- precise about conditions and consequences;
- consistent with repository language, syntax, tone, and formatting;
- free of secrets, personal data, credentials, and transient debugging details.

Use complete, direct prose unless the repository uses another established form. Prefer one strong sentence over a paragraph. Add a second sentence only when it supplies a necessary consequence, boundary, or removal condition.

## Reject Low-Value Comments

Do not add comments that:

- translate a statement into English without adding meaning;
- compensate for a misleading name or avoidable control-flow complexity;
- duplicate the same explanation in declarations and implementations;
- restate a nearby type, assertion, or API signature without explaining its significance;
- speculate about intent or blame a person or team;
- preserve dead code or old implementations;
- state that code is “temporary” without a removal condition;
- use labels such as “hack,” “magic,” or “obvious” instead of explaining the constraint;
- contradict the implementation or rely on an unstable detail unnecessarily.

## Compare Examples

Obvious narration:

```ts
// Increment retries.
retries += 1;
```

Useful rationale:

```ts
// Count the initial request as an attempt so the limit matches the API contract.
retries += 1;
```

Vague warning:

```go
// Important: do not reorder.
writeHeader()
writeBody()
```

Explicit invariant:

```go
// Write the header first because readers allocate the body buffer from its length.
writeHeader()
writeBody()
```

Weak workaround:

```python
# Work around library bug. See #4182.
normalize_twice(value)
```

Durable workaround:

```python
# UnicodeLib versions before 3.4 leave combining marks unnormalized after case folding.
# Remove the second pass when the minimum supported version is 3.4.
normalize_twice(value)
```

## Run the Final Check

Before keeping a new or modified comment, verify:

1. It adds information the code cannot express as clearly.
2. It explains a contract, rationale, constraint, or consequence rather than mechanics.
3. Every factual claim is supported by code, tests, specifications, issue context, or observed behavior.
4. Its scope and placement make the governed code unambiguous.
5. It will remain true when nearby implementation details change.
6. The code change updates or removes any now-stale comments.

If any check fails, revise the code or comment, or omit the comment. When reporting the completed coding task, do not narrate every comment decision unless the user asks; mention only choices material to understanding the change.
