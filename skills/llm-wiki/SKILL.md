---
name: llm-wiki
description: Build and maintain a knowledge wiki using LLMs. This skill manages a three-layer architecture (raw sources, LLM-generated wiki pages, and schema documentation) with workflows for ingesting sources, querying knowledge, and linting for consistency. Use this skill whenever the user wants to create a knowledge base, manage research notes, build a wiki, ingest documents for synthesis, or maintain structured documentation that compounds over time. Essential for research projects, book notes, competitive analysis, course notes, or any domain where knowledge accumulates and cross-references matter.
---

# LLM Wiki Skill

Build and maintain a knowledge wiki using LLMs. The wiki is a persistent, compounding artifact that sits between you and your raw sources.

## Core Philosophy

Traditional RAG retrieves from raw documents on every query. A wiki is different: the LLM incrementally builds and maintains a structured knowledge base that accumulates understanding. Cross-references are already there. Contradictions are already flagged. The synthesis reflects everything you've read.

Key principle: The LLM writes the wiki. You curate sources and ask questions. The tedious bookkeeping is handled automatically.

## Three-Layer Architecture

```text
wiki/
├── raw/                    # Immutable source documents (never modified)
│   ├── specs/             # Formal standards, W3C specs, IETF drafts
│   ├── papers/            # Academic papers
│   ├── articles/          # Blog posts, tutorials, informal sources
│   └── assets/            # Images downloaded from web sources
│
├── pages/                  # LLM-generated wiki pages
│   ├── concepts/          # Domain concepts appearing across sources
│   ├── entities/          # Concrete things in your domain
│   ├── decisions/         # Design decisions (ADR-style)
│   ├── comparisons/       # Trade-off analyses
│   ├── synthesis/         # Evolving thesis, open questions
│   └── sources/           # Per-source summaries
│
├── index.md               # Content catalog (auto-updated)
└── log.md                 # Chronological activity log (append-only)
```

Raw sources are immutable. The LLM reads them but never modifies them.

## Global Rules

- Use type-prefixed wiki links everywhere: `[[concept-name]]`, `[[entity-name]]`, `[[decision-name]]`, `[[comparison-name]]`, `[[synthesis-name]]`, `[[source-name]]`.
- Keep all page names lowercase with hyphens.
- Update `index.md` whenever pages are created, renamed, or materially repurposed.
- Append to `log.md` for every ingest, lint pass, and substantial filed synthesis.
- Create stub pages when a concept clearly needs its own page but cannot yet be fully synthesized.

Read [references/conventions.md](references/conventions.md) for naming, link, stub, cross-reference, and index rules.

## Workflow Routing

Start here, then load the workflow reference that matches the task.

### Ingest

Use when a new source is being added to `wiki/raw/` or when an existing source needs to be folded into the wiki. The ingest workflow creates a source summary, updates affected concept/entity/decision/comparison pages, updates the catalog, and logs the change.

Read [references/ingest.md](references/ingest.md).

### Query

Use when answering a question from the existing wiki. The query workflow starts from `index.md`, reads only the pages needed, answers with wiki-style citations, and offers to file substantial synthesis back into the wiki (filing directly when clearly durable).

Read [references/query.md](references/query.md).

### Lint

Use when health-checking the wiki for contradictions, stale claims, orphan pages, missing pages, missing links, and research gaps. Linting proposes or applies maintenance work and records the pass in `log.md`.

Read [references/lint.md](references/lint.md).

## Shared References

- Read [references/page-templates.md](references/page-templates.md) when creating or expanding wiki pages.
- Read [references/wiki-setup.md](references/wiki-setup.md) when setting up a new wiki, adapting the default folder structure, or creating a project-specific schema file.

## Why This Works

The tedious part of maintaining a knowledge base is not the reading or the thinking. It is the bookkeeping: updating cross-references, keeping summaries current, noting when new data contradicts old claims, and maintaining consistency across dozens of pages. Humans abandon wikis because the maintenance burden grows faster than the value. LLMs can touch many files in one pass and keep the wiki maintained at near-zero marginal cost.
