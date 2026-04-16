# Query Workflow

Use this workflow when the user asks a question that should be answered from the existing wiki.

Also read [conventions.md](conventions.md). Read [page-templates.md](page-templates.md) only if the answer should be promoted into a durable page.

## Query Types

Recognize the type before starting — it shapes how deep to read.

- **Lookup** — retrieving a specific fact or definition. Read index + 1-2 pages. Answer directly.
- **Synthesis** — connecting concepts across multiple pages or sources. Read index + all relevant pages. Answer with cross-page citations.
- **Gap/contradiction** — health-checking coverage or consistency. Read index + affected pages. Surface what's missing or conflicting.

Synthesis and gap queries are where the wiki's value compounds. Prefer framing questions as synthesis queries when possible.

## Workflow

1. Read `wiki/index.md` first to locate relevant pages.
2. Read the most relevant concept, entity, comparison, decision, or synthesis pages in parallel.
3. Read source summary pages if deeper provenance or conflict resolution is needed.
4. Synthesize the answer using section-level wiki citations: `[[concept-x]] §Key Properties`.
5. After answering, surface any gaps noticed while reading (see lint-pass principle below).
6. For synthesis and gap queries, suggest 2-3 follow-up drill questions that would deepen the current thread.
7. Offer to file durable answers back into the wiki (see below).

## Query Principles

- Start narrow from the index instead of reading the whole wiki.
- Prefer synthesized answers over raw excerpts.
- Use source summaries for provenance and nuance, not as a substitute for page-level synthesis.
- Always cite at section level (`§`), not just page level.
- Preserve good answers by filing them — answers that disappear into chat history are wasted synthesis.
- Treat every query as a potential lint pass: note what's missing while reading.

## Filing The Answer

Offer to file when the answer synthesizes multiple pages. File directly (without prompting) only for clearly durable synthesis.

File as:
- **concept page** — answer defines or refines a domain concept
- **comparison page** — answer produces a trade-off analysis
- **decision page** — answer clarifies a design choice or rationale
- **synthesis page** — answer advances the evolving thesis or surfaces open questions

After filing, add `[[type-page-name]]` links from the new page to all referenced pages. Update `wiki/index.md` and append an entry to `log.md`.
