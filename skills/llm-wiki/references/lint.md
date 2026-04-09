# Lint Workflow

Use this workflow when the user asks for a wiki health check or when routine maintenance is needed.

Also read [conventions.md](conventions.md). Read [page-templates.md](page-templates.md) if linting will create stub pages or rewrite existing pages.

## Workflow

1. Scan for contradictions across related pages.
2. Identify stale claims that newer sources supersede.
3. Find orphan pages with no inbound links from the index or other pages.
4. Identify frequently mentioned terms that still lack their own pages.
5. Find missing cross-references between clearly related pages.
6. Identify research gaps that could be resolved by adding sources or running a web search.

The LLM should propose fixes and ask for confirmation before applying them when the changes are non-trivial.

## Typical Fixes

- Repair broken or missing internal links
- Create stub pages for missing but recurring concepts
- Update stale summaries or synthesis pages
- Flag contradictions explicitly for user review
- Suggest missing external research

## Log Entry Format

```markdown
## [YYYY-MM-DD] lint | Wiki lint pass

Fixed 3 broken links. Created 2 stub concept pages for frequently mentioned terms. Noted 1 potential contradiction between [[concept-consistency]] and [[concept-availability]] pages regarding CAP theorem tradeoffs. Suggested web search for "distributed consensus patterns".
```
