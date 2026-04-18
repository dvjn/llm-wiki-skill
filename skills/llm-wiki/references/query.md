# Query Workflow

Answer from existing wiki.

## Query Types

- **Lookup** — specific fact. Read index + 1-2 pages. Answer directly.
- **Synthesis** — connect concepts. If subagents available, delegate to find relevant pages → then synthesize. Otherwise, read index + pages directly.
- **Gap/contradiction** — health check. If subagents available, delegate search → then evaluate. Otherwise, read index + affected pages directly.

## Workflow

1. Read `wiki/index.md` to locate pages
2. For synthesis/gap queries: if subagents available, delegate to find all relevant pages. Otherwise, read relevant pages in parallel.
3. Read source summaries if provenance/conflict resolution needed
4. Synthesize with section-level citations: `[[concept-x]] §Section`
5. Surface gaps noticed while reading
6. For synthesis queries, suggest 2-3 follow-up questions
7. Offer to file durable synthesis back into wiki

## Principles

- Start narrow from index
- Prefer synthesized answers over raw excerpts
- Cite at section level (`§`)
- File good answers — they compound
- Note missing concepts while reading (potential lint pass)

## Filing Answers

When filing durable synthesis back into wiki:

- Create page: Load template `references/templates/<type>.md` and create page directly
- Update index: Add entry to index.md manually
- Log: Append to log.md
