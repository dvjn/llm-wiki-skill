---
name: llm-wiki
description: Build and maintain a knowledge wiki using LLMs. Use when a `wiki/` folder exists in the project OR the user explicitly asks to build a wiki. When wiki is present, query it first for project information and use it to document significant changes.
---

# LLM Wiki

Build and maintain a knowledge wiki using LLMs. The wiki accumulates understanding over time. You curate sources; the LLM writes and maintains pages.

## ⚠️ LAZY LOADING REQUIREMENT

**Only load references when explicitly needed. Never read all references.**

| Task    | Load Only This                                           |
|---------|----------------------------------------------------------|
| Ingest  | `references/ingest.md`                                    |
| Query   | `references/query.md`                                     |
| Lint    | `references/lint.md`                                     |
| Setup   | `references/wiki-setup.md` (never otherwise)             |
| Create  | `references/templates/<type>.md` (one of: concept, entity, decision, comparison, source, stub) |

**Violations:** Loading conventions.md for query, loading wiki-setup.md when wiki exists, loading multiple template files when creating one page.

## Directory Structure

```
wiki/
├── raw/           # Immutable sources (read only)
├── pages/         # LLM-generated pages (concepts/, entities/, decisions/, comparisons/, synthesis/, sources/)
├── index.md       # Content catalog
└── log.md         # Append-only changelog
```

## Global Rules

- Links: `[[type-name]]` with prefix (concept, entity, decision, comparison, synthesis, source)
- Names: lowercase with hyphens
- Update `index.md` on page create/rename/material change
- Append to `log.md` on ingest, lint, and substantial synthesis
- Create stubs for important but underdeveloped concepts

## Workflow Routing

### Ingest
New source → fold into wiki. Read `references/ingest.md`. Use templates from `references/templates/` to create pages. Update `index.md` and `log.md` manually.

### Query
Answer from wiki. Read `references/query.md`. Suggest filing answers back into wiki with direct file operations.

### Lint
Health check. Read `references/lint.md`. Append results to `log.md`.

### Setup
Initialize new wiki. Read `references/wiki-setup.md`.

### Create Pages
Need a template. Read `references/templates/<type>.md` where type matches the page you're creating (concept, entity, decision, comparison, source, or stub).

### Subagent Delegation

If subagents are available, delegate these operations:

- **Synthesis queries**: Subagent locates relevant pages → you synthesize
- **Gap/contradiction queries**: Subagent searches across pages → you evaluate
- **Lint checks**: Parallel subagents for orphans, missing references, term gaps, contradictions, research gaps

If subagents unavailable, perform these operations directly. The workflow remains the same.
