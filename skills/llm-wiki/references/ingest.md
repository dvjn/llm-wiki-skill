# Ingest Workflow

New source in `wiki/raw/` or existing source needs folding into wiki.

## Workflow

1. Read source thoroughly
2. Discuss key takeaways with user (especially early sources in new wiki)
3. Create source summary: Load template `references/templates/source.md` and create `wiki/pages/sources/source-<name>.md`
4. Update affected pages
5. Create new pages: Load template `references/templates/<type>.md` and create `wiki/pages/<type>s/<type>-<name>.md`
6. Update index: Manually add entry to `wiki/index.md` with type, name, and description
7. Log: Append entry to `wiki/log.md`

## Outputs (minimum)

- Source summary page: Load template `references/templates/source.md` and create `wiki/pages/sources/source-<name>.md`
- Updates to affected pages
- Index entries added: Manually add to `wiki/index.md`
- Log entry appended: Append to `wiki/log.md`

## Log Format

```markdown
## [YYYY-MM-DD] ingest | [Source Title]

Added `raw/...`. Created source summary. Updated N concept pages. Created N new pages. Updated index.
```

## Creation Heuristics

Create pages when:
- Concept/entity appears across multiple sources and merits synthesis
- Source introduces reusable comparison
- Source motivates design decision
- Source fills out a stub enough to convert

For important concepts not yet fully developed, create a stub page.
