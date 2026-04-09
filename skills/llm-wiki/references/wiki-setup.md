# Wiki Setup Guide

Use this reference when the project does not yet have a wiki, when the default structure needs to be adapted to a domain, or when the repo should carry a local `SCHEMA.md` or `AGENTS.md` to guide future wiki maintenance.

This is setup guidance, not a runtime workflow. For day-to-day ingest, query, and lint tasks, use the semantic workflow references instead.

## Default Bootstrap

For a new project, start with this structure:

```text
wiki/
├── raw/
│   ├── specs/          # Formal standards and requirements
│   ├── papers/         # Academic papers
│   ├── articles/       # Blog posts, tutorials, notes
│   └── assets/         # Downloaded images and supporting files
│
├── pages/
│   ├── concepts/       # Domain concepts
│   ├── entities/       # Concrete system objects
│   ├── decisions/      # ADR-style records
│   ├── comparisons/    # Trade-off analyses
│   ├── synthesis/      # Evolving takeaways and open questions
│   └── sources/        # Per-source summaries
│
├── index.md            # Content catalog
└── log.md              # Append-only change log
```

Create the full tree up front even if some directories start empty. That gives ingest, query, and lint a stable target shape.

## Minimal Starter Files

Bootstrap `index.md` with the standard top-level sections from [conventions.md](conventions.md).

Bootstrap `log.md` with a short header such as:

```markdown
# Wiki Log

Append-only record of ingest, lint, and major synthesis updates.
```

If the project benefits from an explicit local schema, create `wiki/SCHEMA.md` or a repo-level `AGENTS.md` that records:

- the purpose of the wiki
- the folder structure
- any domain-specific page conventions
- any codebase-specific expectations, such as linking entity pages to implementation files

## What To Customize

Start from the default structure and only change it when the domain clearly needs it.

Examples:

- Add `raw/rfcs/` for standards-heavy technical work
- Add `raw/chapters/` for book notes
- Emphasize `pages/decisions/` for architecture-heavy engineering wikis
- Emphasize `pages/synthesis/` for research and literature-review work

Prefer additive changes over renaming the default directories. Keeping the standard shape makes the workflow references easier to apply consistently.

## What The Local Schema Should Say

If you create a local schema file, it should define:

- the wiki's purpose and boundaries
- the exact directory structure
- the page types in use
- any domain-specific template adjustments
- the ingest, query, and lint expectations
- any integration with the codebase or external systems

The local schema should customize this skill, not replace it. Reuse the default conventions unless the project has a concrete reason to diverge.
