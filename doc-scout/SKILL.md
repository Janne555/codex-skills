---
name: doc-scout
description: Search official documentation and other external sources to answer a set of technical questions. Use when the main agent suspects outdated knowledge and needs fresh, source-backed answers. Produces a compact answer pack with links, section headings, and version/date signals.
compatibility: Requires access to the internet (via the host agent/CLI) to read external docs.
---

# Doc-Scout (External Documentation Research)

## Purpose
Given a list of questions, find **current, source-backed** answers by reading external documentation and other authoritative resources, then return a **compact answer pack** suitable for ingestion by another Codex session without blowing up context.

## Inputs
- `.ace/doc_scout_questions.md` (required): a Markdown file containing questions to answer.
  - If the file does not exist, ask the user to provide it or paste its contents.

## Outputs
- `.ace/doc_scout_answers.md` (required): a compact answer pack (strict format below).

## Operating rules
1. **Prefer authoritative sources**
   - Official docs, vendor docs, reference manuals, release notes, changelogs.
   - Avoid blog posts unless official docs are missing or ambiguous.
2. **Optimize for freshness**
   - If the ecosystem is versioned, find the latest stable docs/version.
   - Capture a “freshness signal” (version number, release date, “last updated” date, or doc URL path that indicates version).
3. **No large dumps**
   - Do not paste long doc excerpts.
   - Summarize; keep each answer tight.
4. **Bounded output**
   - Max 5 bullets per question in “Answer”.
   - Max 2 sources per question unless essential.
   - If a question cannot be answered confidently, say so and propose the next best source to check.

## Required format: `doc_scout_answers.md`
For each question, produce:

### Q: <question text>
**Answer**
- <bullet 1>
- <bullet 2>
- ...

**Sources**
- <Doc title> — <URL> — <section heading / anchor / page location>

**Freshness**
- <version/date/last-updated indicator; if unknown, state "unknown">

**Notes**
- <assumptions, ambiguity, or decision points (optional, keep short)>

## Workflow
1. Read `.ace/doc_scout_questions.md`.
2. For each question:
   - Identify the most likely official docs.
   - Read enough to answer accurately.
   - Record the source link + section heading.
   - Extract a freshness signal if available.
3. Write `.ace/doc_scout_answers.md` in the required format.
4. Stop.

## Edge cases
- If sources disagree:
  - Prefer official docs and newer sources.
  - Note the disagreement in **Notes** and include both sources if necessary.
- If the question is underspecified:
  - Provide the minimal safe answer and list what missing parameter(s) would change the answer.

