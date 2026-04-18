# Decision: Delegate Search-Heavy Operations to Subagents When Available

**Status**: Accepted
**Date**: 2026-04-18
**Context**: The wiki workflow includes operations that require searching across many pages — synthesis queries, gap/contradiction checks, and lint operations. These can be done more efficiently by subagents when available.

## Decision

When subagents are available, delegate the following operations:
- **Synthesis queries**: Subagent locates relevant pages → you synthesize
- **Gap/contradiction queries**: Subagent searches across pages → you evaluate
- **Lint checks**: Parallel subagents for orphans, missing references, term gaps, contradictions, research gaps

When subagents are unavailable, perform these operations directly. The workflow steps remain the same.

## Rationale

Subagents excel at searching across many files in parallel. For synthesis queries, they can locate all relevant pages faster. For lint, parallel subagents can run independent checks simultaneously. This improves response time without changing the workflow.

Alternatives considered:
- **Always delegate**: Assumes subagents always available; breaks fallback workflow.
- **Never delegate**: Misses efficiency gains when subagents are available.

## Consequences

- Positive: Faster synthesis queries and lint checks when subagents available.
- Positive: More thorough cross-page search than manual reading.
- Positive: Falls back gracefully when subagents unavailable.
- Negative: Slight additional complexity in skill documentation.
- Risk: Must clearly communicate conditional usage in skill.

## Related

- [[concept-lint-workflow]] — lint checks that benefit from delegation
- [[concept-query-workflow]] — query types and when delegation helps