# Wiki Conventions

This reference contains shared rules that apply across ingest, query, and lint workflows.

## Raw Sources

Raw sources are immutable. The LLM reads from `wiki/raw/` but never edits files there.

Naming convention: `{type}-{short-title}.md`

Examples:
- `spec-rest-api.md`
- `paper-consensus-raft.md`
- `article-react-hooks.md`

## Link Prefix System

All wiki links use a mandatory type prefix to prevent name collisions.

- Format: `{type}-{name}`
- Allowed prefixes: `concept`, `entity`, `decision`, `comparison`, `synthesis`, `source`
- Casing: all lowercase with hyphens
- Prefix position: always the first segment before the first hyphen
- Source links: `[[source-filename]]`
- Comparison links: include `vs` in the name, for example `[[comparison-postgres-vs-mysql]]`

Why this matters: concepts and entities often share names, and multiple sources often discuss overlapping terms. The prefix keeps each namespace unambiguous.

## When To Create Links

Use `[[page-name]]` links whenever mentioning a concept or entity that already has its own page.

- Always link when the referenced concept or entity has a page.
- Link to sources using `[[source-filename]]`.
- Add missing cross-references during ingest and lint when two pages should clearly be connected.

## When To Create New Pages

Create a new page when:

- A concept or entity appears in 3 or more sources and needs its own synthesis
- A design decision should be recorded
- A comparison is requested and is valuable enough to persist
- An answer synthesizes multiple sources and is reusable

## Stub Pages

When a concept needs a page but the wiki does not yet have enough material for a full synthesis, create a stub:

```markdown
# [Concept Name]

> [Brief definition from first mention]

## Status

Stub - needs expansion from sources: [[source-spec-auth-flow]], [[source-paper-consensus-raft]]

## Initial Notes

[Brief notes from current understanding]
```

## Index Structure

`index.md` is the content catalog and should be updated on every ingest, lint pass that changes pages, and whenever a substantial new filed page is created.

```markdown
# Wiki - Content Catalog

> Auto-updated by the LLM on every ingest, query filing, and lint pass.

## Concepts

Domain concepts that appear across multiple sources.

- [[concept-example-name]] - one-line description
- [[concept-another-example]] - one-line description

## Entities

Concrete things in the system.

- [[entity-example-name]] - one-line description

## Decisions

Design decisions with rationale.

- [[decision-example-name]] - one-line description

## Comparisons

Trade-off analyses.

- [[comparison-example-name]] - one-line description

## Sources

Per-source summaries.

- [[source-filename]] - one-line description

## Statistics

| Metric | Count |
|--------|-------|
| Raw sources | N |
| Wiki pages | N |
| Concepts | N |
| Entities | N |
```

## Log Entries

`log.md` is append-only. Record every ingest, every lint pass, and every substantial filed synthesis.

Use concise entries that say what changed and which pages were created or updated.
