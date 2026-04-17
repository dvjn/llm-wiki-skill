# Entity: SKILL.md

> The root instruction document for the llm-wiki skill — describes the architecture, global rules, and workflow routing.

## Purpose

`SKILL.md` is the entry point for the llm-wiki skill. It describes the three-layer architecture, the global rules (link prefixes, naming, log/index maintenance), and routes the LLM to the appropriate workflow reference for ingest, query, or lint tasks.

## Structure

- **Lazy Loading Requirement** — task-to-reference mapping table with explicit violations to prevent overloading the context
- **Directory Structure** — canonical `wiki/` tree diagram
- **Global Rules** — link prefix requirements, naming conventions, index/log update obligations, stub creation

- **Workflow Routing** — routes to `references/ingest.md`, `references/query.md`, `references/lint.md`, `references/wiki-setup.md`, and `references/templates/<type>.md`

## Frontmatter (per Agent Skills spec)

| Field | Required | Constraint |
|-------|----------|------------|
| `name` | Yes | Max 64 chars; lowercase + hyphens only; must match directory name |
| `description` | Yes | Max 1024 chars; describe what the skill does and when to use it |
| `license` | No | License name or bundled file reference |
| `compatibility` | No | Max 500 chars; environment requirements |
| `metadata` | No | Arbitrary string key-value map |
| `allowed-tools` | No | Space-separated pre-approved tools (experimental) |

The `description` is the tier-1 routing signal: it is loaded at agent startup and must be precise enough to trigger on relevant tasks. See [[concept-progressive-disclosure]].

## Size Budget

Per the Agent Skills specification:
- `SKILL.md` body: **< 500 lines / < 5000 tokens** — defer details to `references/`
- Workflow references are tier-3 resources, loaded only when the specific workflow is invoked

## File Path

`skills/llm-wiki/SKILL.md`

## Lifecycle

Created once during skill development. Updated when the architecture or global conventions change materially. Each section corresponds to a reference file in `skills/llm-wiki/references/`.

## Related Entities

- [[entity-schema-document]] — the wiki's configuration file; distinct from this skill entrypoint
- [[entity-index-md]] — described in SKILL.md as the content catalog
- [[entity-log-md]] — described in SKILL.md as the append-only log

## Related Concepts

- [[concept-three-layer-architecture]] — the architecture SKILL.md describes
- [[concept-progressive-disclosure]] — the loading model SKILL.md participates in (tier 2); the "Lazy Loading Requirement" section enforces it

- [[concept-stub-pages]] — SKILL.md names stub creation as a global rule
- [[concept-ingest-workflow]] — routed from SKILL.md to `references/ingest.md`
- [[concept-query-workflow]] — routed from SKILL.md to `references/query.md`
- [[concept-lint-workflow]] — routed from SKILL.md to `references/lint.md`

## Sources

- [[source-agentskills-what-are-skills]] — defines what SKILL.md must contain
- [[source-agentskills-specification]] — normative spec for frontmatter fields and size budgets
