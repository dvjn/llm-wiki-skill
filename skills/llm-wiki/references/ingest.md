# Ingest Workflow

Use this workflow when a new source is added to `wiki/raw/` or when an existing source needs to be folded into the wiki.

Also read [page-templates.md](page-templates.md) for page structures and [conventions.md](conventions.md) for naming, links, stub rules, and index conventions.

## Workflow

1. Read the source document thoroughly.
2. Discuss key takeaways with the user when that would improve the synthesis, especially for early sources in a new wiki.
3. Create a source summary page in `wiki/pages/sources/`.
4. Update relevant concept, entity, decision, comparison, or synthesis pages across the wiki.
5. Create new pages when the source introduces durable concepts, entities, or decisions that warrant them.
6. Update `wiki/index.md` to catalog created or materially changed pages.
7. Append an ingest entry to `wiki/log.md`.

A single source may touch many wiki pages. That is expected.

## Ingest Outputs

Every ingest should produce, at minimum:

- A source summary page
- Updates to affected synthesis pages or concept/entity pages
- An updated index entry set
- A log entry

## Log Entry Format

```markdown
## [YYYY-MM-DD] ingest | [Source Title]

Added `raw/papers/paper-consensus-raft.md`. Created source summary. Updated 8 concept pages (consensus, leader-election, log-replication). Created 2 new entity pages (node, log-entry). Updated index.
```

## Creation Heuristics

Create new pages during ingest when:

- A concept or entity appears across multiple sources and now clearly merits synthesis
- The source introduces a reusable comparison
- The source changes or motivates a design decision
- The source fills out a stub enough to convert it into a real page

If a concept is clearly important but not fully developed yet, create a stub page rather than leaving the term untracked.
